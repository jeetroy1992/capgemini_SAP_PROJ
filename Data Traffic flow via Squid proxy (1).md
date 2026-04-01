```mermaid
flowchart LR

%% ===========================
%%     GLOBAL STYLE OVERRIDES
%% ===========================
%% Increase default font & node size
%% Mermaid supports custom CSS-like styling
%% ----------------------------------------

classDef bigNode stroke-width:4px, font-size:22px, padding:25px, color:#000;

%% ===========================
%%     CUSTOM COLOR STYLES
%% ===========================

classDef customer fill:#4DA3FF,stroke:#005B99,stroke-width:4px,color:#fff,font-size:22px,padding:25px;
classDef internet fill:#A6A6A6,stroke:#595959,stroke-width:4px,color:#fff,font-size:22px,padding:25px;
classDef nie fill:#FFB84D,stroke:#CC7A00,stroke-width:4px,color:#000,font-size:22px,padding:25px;
classDef router fill:#66C2A5,stroke:#2A7F62,stroke-width:4px,color:#000,font-size:22px,padding:25px;
classDef border fill:#B3A2C7,stroke:#6A5A8C,stroke-width:4px,color:#000,font-size:22px,padding:25px;
classDef networkpair fill:#F28585,stroke:#993333,stroke-width:4px,color:#000,font-size:22px,padding:25px;
classDef compute fill:#FFD966,stroke:#B79D00,stroke-width:4px,color:#000,font-size:22px,padding:25px;
classDef vm fill:#8FD9A8,stroke:#3F8F5E,stroke-width:4px,color:#000,font-size:22px,padding:25px;

%% ===========================
%%     NODES
%% ===========================

A[Customer Network]
B[Internet]

C[NIE]
C2[DIBS]

INET["SAP Internet Router Pair<br/>(INET Pair)"]

BL[MLAG Border Leaf Pair]

VPN["VPN Pair<br/>(IPSec Policy‑Based / Route‑Based)"]
WAN["WAN Pair<br/>(MPLS / Cloud Peering)"]

F[Load Balancer]
G[CGS]
H[Customer VM]
class A customer;
class B internet;

class C,C2 nie;
class INET router;

class BL border;

class VPN,WAN networkpair;

class F,G compute;
class H vm;

%% ===========================
%%     FLOWS (Thicker Arrows)
%% ===========================

linkStyle default stroke-width:4px;

A --> B
B --> C & C2

C --> INET
C2 --> INET

INET --> BL

BL --> VPN
BL --> WAN

VPN --> F
WAN --> F

F --> G --> H
