```mermaid
sequenceDiagram

    autonumber

    participant U as 👤 User1000<br/>Corporate VPN

    participant VPN as 🔐 VPN Tunnel<br/>Cust Network

    participant CORE as 🌐 Core Network<br/>10.10.10.100

    participant VIP as 🟠 F5 Internal VIP<br/>192.168.1.100:443

    participant CSSL as 🔒 Client SSL Profile<br/>www.wd.abc.co.in<br/>SAP Internal CA

    participant SNAT as 🔄 SNAT Pool<br/>.249 / .250 / .251

    participant PERS as 🍪 Persistence Profile<br/>Cookie Based

    participant SSSL as 🔒 Server SSL Profile<br/>Internal CA

    participant SAP1 as 🟢 SAP Server 1<br/>10.10.10.11:8000

    participant SAP2 as ⚪ SAP Server 2<br/>10.10.10.12:8000

    rect rgb(230, 240, 255)

        Note over U,CORE: 🔐 STEP 1 — VPN Connection

        U->>VPN: Connect to Corporate VPN<br/>User1000 → Cust Network

        VPN->>CORE: VPN Tunnel Established<br/>Cust → SAP HEC Core<br/>10.10.10.100

        CORE-->>U: VPN Connected ✅<br/>Inside HEC Network now

    end

    rect rgb(255, 245, 220)

        Note over U,VIP: 🤝 STEP 2 — TCP 3-Way Handshake

        U->>VIP: SYN → dst: 192.168.1.100:443

        VIP-->>U: SYN-ACK

        U->>VIP: ACK — TCP Connection Established ✅

    end

    rect rgb(220, 255, 220)

        Note over U,CSSL: 🔒 STEP 3 — TLS Handshake LEG 1 (VPN User ↔ F5)

        U->>CSSL: CLIENT HELLO<br/>─────────────────<br/>TLS Version: TLS 1.2 / 1.3<br/>Supported Ciphers: AES-256, AES-128...<br/>Random Number (Client Random)<br/>Session ID

        CSSL-->>U: SERVER HELLO<br/>─────────────────<br/>Selected TLS Version: TLS 1.3<br/>Selected Cipher: AES-256-GCM-SHA384<br/>Random Number (Server Random)<br/>Session ID Confirmed

        CSSL-->>U: CERTIFICATE<br/>─────────────────<br/>www.wd.abc.co.in<br/>Issued by: SAP Internal CA<br/>Valid Until: 2027-04-10

        CSSL-->>U: CERTIFICATE CHAIN<br/>─────────────────<br/>SAP Internal Intermediate CA<br/>SAP Internal Root CA

        Note over U: VPN Client verifies chain:<br/>SAP Internal Root CA trusted ✅<br/>(Pre-installed via VPN/Corporate)<br/>Intermediate signed by Root ✅<br/>Cert signed by Intermediate ✅<br/>Domain matches ✅

        U->>CSSL: KEY EXCHANGE<br/>─────────────────<br/>Pre-Master Secret<br/>(encrypted with F5 Public Key)

        Note over U,CSSL: Both sides derive Session Keys<br/>using Client Random + Server Random<br/>+ Pre-Master Secret

        U->>CSSL: CHANGE CIPHER SPEC<br/>Switching to encrypted communication

        CSSL-->>U: CHANGE CIPHER SPEC<br/>Switching to encrypted communication

        U->>CSSL: FINISHED (encrypted) ✅

        CSSL-->>U: FINISHED (encrypted) ✅

        Note over U,CSSL: 🔒 LEG 1 Encrypted Tunnel Established<br/>VPN User ↔ F5

    end

    rect rgb(255, 230, 230)

        Note over VIP,SNAT: 🔓 STEP 4 — F5 Decrypts & Applies SNAT

        U->>CSSL: HTTPS GET /sap/bc/gui/<br/>Host: www.wd.abc.co.in

        CSSL->>CSSL: Decrypt using Session Key 🔓<br/>Now readable plain HTTP

        CSSL->>SNAT: Apply SNAT Pool<br/>src → 10.10.10.249 (.250/.251 floating)<br/>Backend can reply to F5 ✅

    end

    rect rgb(255, 240, 200)

        Note over PERS,SAP2: 🍪 STEP 5 — Persistence Check

        SNAT->>PERS: SNAT Applied ✅<br/>Check Persistence Cookie

        alt First Visit — No Cookie Found

            PERS->>SAP1: No cookie ❌<br/>Load Balance → SAP Server 1<br/>dst: 10.10.10.11:8000

        else Return Visit — Cookie Found

            PERS->>SAP1: Cookie Found ✅<br/>BIGipServer=10.10.10.11<br/>Skip LB → Always Server 1

        end

    end

    rect rgb(220, 240, 255)

        Note over SSSL,SAP1: 🔒 STEP 6 — TLS Handshake LEG 2 (F5 ↔ SAP Server)

        PERS->>SSSL: Forward to SAP Server 1

        SSSL->>SAP1: CLIENT HELLO<br/>─────────────────<br/>TLS Version: TLS 1.2 / 1.3<br/>Supported Ciphers<br/>Client Random

        SAP1-->>SSSL: SERVER HELLO<br/>─────────────────<br/>Selected TLS Version<br/>Selected Cipher<br/>Server Random

        SAP1-->>SSSL: CERTIFICATE<br/>─────────────────<br/>appserver01.hec-internal.local<br/>Issued by: SAP Internal CA

        Note over SSSL: F5 verifies backend cert:<br/>SAP Internal CA trusted ✅<br/>Cert valid ✅<br/>Not expired ✅

        SSSL->>SAP1: KEY EXCHANGE<br/>Pre-Master Secret<br/>(encrypted with SAP Server Public Key)

        Note over SSSL,SAP1: Both sides derive Session Keys

        SSSL->>SAP1: CHANGE CIPHER SPEC

        SAP1-->>SSSL: CHANGE CIPHER SPEC

        SSSL->>SAP1: FINISHED (encrypted) ✅

        SAP1-->>SSSL: FINISHED (encrypted) ✅

        Note over SSSL,SAP1: 🔒 LEG 2 Encrypted Tunnel Established<br/>F5 ↔ SAP Server 1

    end

    rect rgb(220, 255, 220)

        Note over SAP1: ⚙️ STEP 7 — SAP Processes Request

        SSSL->>SAP1: Plain HTTP Request forwarded<br/>GET /sap/bc/gui/...

        SAP1-->>SSSL: HTTP 200 OK Response<br/>SAP Fiori / GUI content

        SAP2-->>SAP2: Standby ⚪

    end

    rect rgb(255, 245, 220)

        Note over U,PERS: 📤 STEP 8 — F5 Sends Response to VPN User

        SSSL-->>PERS: Decrypt SAP Response 🔓

        PERS-->>CSSL: Insert Persistence Cookie<br/>Set-Cookie: BIGipServer_Pool=<br/>10.10.10.11.8000; path=/; HttpOnly

        CSSL-->>U: Re-encrypt with Session Key 🔒<br/>HTTPS 200 OK<br/>+ SAP Content<br/>+ Persistence Cookie

    end

    rect rgb(240, 240, 240)

        Note over U,SAP1: ✅ STEP 9 — Session Fully Established<br/>Browser stores cookie 🍪<br/>All future requests → Cookie → Server 1 always<br/>SAP session intact 🔒<br/>Internal Cert: www.wd.abc.co.in (SAP Internal CA) ✅

    end
 
```
