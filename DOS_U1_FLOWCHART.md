
# Flowchart U1

'''
flowchart TD
    A[Distributed Operating System]
    A --> B[Introduction to Distributed Systems]
    A --> C[Goals]
    A --> D[Design Issues]
    A --> E[Computer Networks]
    A --> F[Network Topologies]
    A --> G[Medium-Access Control Protocols]
    A --> H[Switching Techniques]
    A --> I[Routing Techniques]
    A --> J[Communication Protocols]
    A --> K[Internetworking]
    A --> L[Message Passing]
    A --> M[Synchronization]
    A --> N[Group Communication]

    %% Introduction to Distributed Systems
    B --> B1[Historical Context: 1940s–1960s]
    B1 --> B11["Early computers: Large, expensive"]
    B1 --> B12["Advances: Microprocessors & high-speed networks"]
    B --> B2[Definition]
    B2 --> B21["Collection of independent computers appearing as a single system"]
    B2 --> B22["Hardware: Autonomous machines"]
    B2 --> B23["Software: Single-system illusion"]

    %% Goals
    C --> C1[Advantages]
    C1 --> C11["Economics: Cost-effective microprocessors"]
    C1 --> C12["Inherent Distribution: Spatially separated apps"]
    C1 --> C13["Reliability: Survives node failures"]
    C1 --> C14["Incremental Growth: Scalable resources"]
    C1 --> C15["Data/Device Sharing: Databases, printers"]
    C1 --> C16["Communication: Email, collaboration"]
    C1 --> C17["Flexibility: Workload distribution"]
    C --> C2[Disadvantages]
    C2 --> C21["Software Scarcity: Limited tools"]
    C2 --> C22["Network Issues: Saturation, latency"]
    C2 --> C23["Security Risks: Data exposure"]

    %% Design Issues
    D --> D1[Transparency]
    D1 --> D11["User/System Level: Hide complexity"]
    D1 --> D12["Types: Location, Failure, Access, Migration, Replication, Concurrency"]
    D --> D2[Flexibility]
    D2 --> D21["Kernels: Monolithic vs. Microkernel"]
    D --> D3[Reliability]
    D3 --> D31["Fault Tolerance: Availability, security"]
    D3 --> D32["Job Takeover: Failed node replacement"]
    D --> D4[Performance]
    D4 --> D41["Metrics: Response time, throughput, utilization"]
    D4 --> D42["Parallelism: Fine-grained vs. Coarse-grained"]
    D --> D5[Scalability]
    D5 --> D51["Decentralized Algorithms: No global state, local decisions"]

    %% Computer Networks
    E --> E1[LANs]
    E1 --> E11["Small area (office/building), 10 Mbps–10 Gbps"]
    E --> E2[WANs]
    E2 --> E21["Large geographic span (countries), interconnects LANs"]

    %% Network Topologies
    F --> F1[Buses]
    F1 --> F11["Shared medium (e.g., Sun Enterprise)"]
    F1 --> F12["Bandwidth bottleneck"]
    F --> F2[Crossbars]
    F2 --> F21["Non-blocking, O(p²) complexity"]
    F --> F3[Omega Networks]
    F3 --> F31["log p stages, 2×2 switches (pass-through/crossover)"]
    F3 --> F32["Routing: Bitwise destination matching"]
    F3 --> F33["Blocking example: Link contention"]
    F --> F4[Completely Connected]
    F4 --> F41["O(p²) links, impractical for large p"]
    F --> F5[Star Networks]
    F5 --> F51["Central node bottleneck"]
    F --> F6[Linear Arrays/Meshes]
    F6 --> F61["1D (ring), 2D/3D grids, hypercubes (log p distance)"]
    F --> F7[Fat Trees]
    F7 --> F71["Bandwidth scalability via thickened links"]

    %% MAC Protocols
    G --> G1[CSMA/CD]
    G1 --> G11["Carrier sensing, collision detection, exponential backoff"]
    G1 --> G12["Use Case: Ethernet (LANs)"]
    G1 --> G13["Drawbacks: Unbounded delay, no prioritization"]
    G --> G2[Token Ring]
    G2 --> G21["Controlled access via circulating token"]
    G2 --> G22["Advantages: Bounded delay, variable message size"]
    G --> G3[Slotted Ring]
    G3 --> G31["Fixed-size slots with control/data fields"]
    G3 --> G32["Advantages: Fair bandwidth sharing"]

    %% Switching Techniques
    H --> H1[Circuit Switching]
    H1 --> H11["Dedicated path (e.g., PSTN)"]
    H --> H2[Message Switching]
    H2 --> H21["Store-and-forward (high latency)"]
    H --> H3[Packet Switching]
    H3 --> H31["Efficient resource use, fault tolerance"]
    H3 --> H32["Process: Split, route, reassemble"]

    %% Routing Techniques
    I --> I1[Source Routing]
    I1 --> I11["Path predefined by sender"]
    I --> I2[Hop-by-Hop Routing]
    I2 --> I21["Dynamic decisions per node"]
    I --> I3[Static vs. Dynamic]
    I3 --> I31["Static: Fixed tables"]
    I3 --> I32["Dynamic: Adaptive tables"]

    %% Communication Protocols
    J --> J1[OSI Model]
    J1 --> J11["Layers: Physical, Data Link, Network, Transport, Session, Presentation, Application"]
    J --> J2[IEEE 802]
    J2 --> J21["MAC Layer: CSMA/CD (802.3), Token Bus (802.4), Token Ring (802.5)"]
    J2 --> J22["LLC Layer: Common protocol for all MACs"]

    %% Internetworking
    K --> K1[Bridges]
    K1 --> K11["Connect similar networks (Data Link)"]
    K --> K2[Routers]
    K2 --> K21["Route traffic (Network layer)"]
    K --> K3[Gateways]
    K3 --> K31["Protocol translation (Session–Application)"]

    %% Message Passing
    L --> L1[Structure]
    L1 --> L11["Header (address, sequence) + data"]
    L --> L2[Semantics]
    L2 --> L21["Blocking/Nonblocking Send/Receive"]
    L --> L3[Buffering]
    L3 --> L31["Null, Single-Message, Unbounded/Finite-Capacity"]

    %% Synchronization
    M --> M1[Blocking vs. Nonblocking]
    M1 --> M11["Trade-offs: Simplicity vs. Concurrency"]
    M --> M2[Timeouts]
    M2 --> M21["Prevent indefinite blocking during failures"]

    %% Group Communication
    N --> N1[Design Issues]
    N1 --> N11["Closed vs. Open Groups"]
    N1 --> N12["Peer vs. Hierarchical Groups"]
    N --> N2[Membership]
    N2 --> N21["Centralized vs. Distributed Management"]
    N --> N3[Atomicity]
    N3 --> N31["All-or-Nothing Delivery"]
    N --> N4[Message Ordering]
    N4 --> N41["Global vs. Consistent Time Ordering"]
    N --> N5[Scalability]
    N5 --> N51["Challenges in large groups"]
    
'''
