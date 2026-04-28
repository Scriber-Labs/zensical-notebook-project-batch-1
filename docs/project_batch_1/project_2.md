# Project 2: Inverse Schrödinger Problem

!!! admonition Overview

    === "Figure 1"

        ``` markdown
        * Sed sagittis eleifend rutrum
        * Donec vitae suscipit est
        * Nulla tempor lobortis orci
        ```

    === "Architecture"

        ```mermaid
%%====================================================================
%%  🏗️ PIML Architecture
%%====================================================================
%%{ init: {
        "theme": "base",
        "themeVariables": {
            "background": "#0d1117",
            "lineColor": "#14b5ff",
            "textColor": "#ffffff",
            "fontFamily": "'Aclonica', sans-serif",
            "borderRadius": "16",
        },
        "handDrawn": true
    } }%%
%%====================================================================
flowchart TB
    %%--------------------------------------------------------------
    classDef grad1 fill:#301934,stroke:#5D3FD3,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef grad2 fill:#45275a,stroke:#5D3FD3,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef grad3 fill:#5c3b80,stroke:#5D3FD3,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef grad4 fill:#7495b5,stroke:#5D3FD3,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef grad5 fill:#8ac9d9,stroke:#5D3FD3,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef grad6 fill:#a0f0ff,stroke:#5D3FD3,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;

    style spatial fill:#340b2d,stroke:#b045e0,color:#ffffff,rx:12,ry:12;
    style observed fill:#181c3f,stroke:#5f88ff,stroke-width:2px,color:#ffffff,rx:12 ry:12;

    classDef Total_loss stroke:#767cea,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef stage0 fill:#301934,stroke:#5D3FD3,stroke-dasharray: 6 6,color:#ffffff,rx:12,ry:12;
    classDef PIML_framework fill:#161b22,stroke:#14b5ff,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef stage1 fill:#0f2a3d,stroke:#14b5ff,stroke-dasharray: 6 6,color:#ffffff,rx:12,ry:12;
    classDef stage2 fill:#103b4f,stroke:#00e8ff,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef stage3 fill:#124f55,stroke:#00f5db,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef stage4 fill:#1a6b63,stroke:#00f5db,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef dashed_green fill:#555555,stroke:#3EB489,stroke-width:3px,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef stage5 fill:#1f4e5f,stroke:#00FF7F,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef POD_diagnostics stroke:#f78166,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef stage6 fill:#3a2f2a,stroke:#f78166,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef stage7 fill:#3a2f2a,stroke:#f68080,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef dashed_orange_1 fill:#161b22,stroke:#f68080,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;
    classDef pink_dotted fill:#420C29,stroke:#f72585,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;

    classDef blue_dotted_2 fill:#0f2a3d,stroke:#14b5ff,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;

    classDef stage5 fill:#0f2a3d,stroke:#00FF7G,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef blue_purple fill:#3bb2f5,stroke:#767cea,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef periwinkle_purple fill:#767cea,stroke:#b045e0,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef MLP fill:#3a0ca3,stroke:#767cea,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef light_dark_purple fill:#4361ee,stroke:#b045e0,stroke-width:2px,color:#ffffff,rx:12,ry:12;
    classDef blue_pink fill:#4cc9f0,stroke:#eb0fd5,stroke-width:2 2,color:#ffffff,rx:12,ry:12;

    classDef purple_blue fill:#7209b7,stroke:#3bb2f5,stroke-width:2px,color:#ffffff,rx:12,ry:12;

    style step0 fill:#0f0a25,stroke:#7c5cff,stroke-width:4px,color:#ffffff,rx:12px, ry:12px;
    style synthetic fill:#14153a,stroke:#6b4cff,stroke-width:3px,color:#ffffff,stroke-dasharray:6 6,rx:12px, ry:12px;
    style PIML fill:#161b22,stroke:#14b5ff,strok-width:5px,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12px;
    style learned_parameters fill:#0d1a30,stroke:#3b82ff,stroke-width:3px,color:#ffffff,stroke-dasharray:6 6,rx:12px, ry:12px;

    classDef MLP fill:#2a185c,stroke:#9a66ff,stroke-width:4px,color:#ffffff,rx:12px, ry:12px;
    style potential fill:#11163a,stroke:#5f88ff,stroke-width:4px,color:#ffffff,rx:12px, ry:12px;
    style potential_network fill:#0d1630,stroke:#3072f5,stroke-width:4px,color:#ffffff,stroke-dasharray:6 6,rx:12px, ry:12px;

    classDef eigenfunctions fill:#153a55,stroke:#4ec9ff,stroke-width:2px,color:#ffffff,rx:12px, ry:12px;
    style eigenfunction_networks fill:#11253f,stroke:#38c6ff,stroke-width:2px,color:#ffffff,stroke-dasharray:6 6,rx:12px, ry:12px;

    classDef energy fill:#0d2238,stroke:#3b9eff,stroke-width:4px,color:#ffffff,rx:12px, ry:12px;
    style energy_eigenvalues fill:#071320,stroke:#3b9eff,stroke-width:4px,color:#ffffff,stroke-dasharray: 6 6, rx:12px, ry:12px;

    style post-training fill:#161b22,stroke:#f68080,stroke-dasharray:6 6,color:#ffffff,rx:12,ry:12;

    %%-----------------------------------------------------------
    %% LOSS (cyan end of gradient)
    %%-----------------------------------------------------------

    classDef loss fill:#0a0f1a,stroke:#22d3ee,stroke-width:3px,color:#ffffff,stroke-dasharray:6 6,rx:12px,ry:12px;
    style loss_terms fill:#03011b,stroke:#4f15ee,stroke-width:2px,color:#ffffff,stroke-dasharray:6 6,rx:12px,ry:12px;

    style residual fill:#0a1329,stroke:#5f88ff,stroke-width:2px,color:#ffffff,rx:12px, ry:12px;
    style R fill:#0e1c3f,stroke:#4ec9ff,stroke-width:2px,color:#ffffff,rx:12px, ry:12px;

    style loss_physics fill:#06083b,stroke:#1135ff,stroke-width:2px,color:#ffffff,rx:12px, ry:12px;
    style loss_norm fill:#0e2a3b,stroke:#4ec9ff,stroke-width:2px,color:#ffffff,rx:12px, ry:12px;
    style loss_smooth fill:#0b2f2a,stroke:#34d399,stroke-width:2px,color:#ffffff,rx:12px,ry:12px;
    style loss_data fill:#3a0a28,stroke:#fc72f9,stroke-width:2px,color:#ffffff,rx:12px,ry:12px;

    style opt fill:#2a1c16,stroke:#f59e0b,stroke-width:2px,color:#ffffff,rx:12px,ry:12px;

    style finite_difference fill:#0a1329,stroke:#31ff48,stroke-width:2px,color:#ffffff,stroke-dasharray:6 6,rx:12px,ry:12px;
    style potential_stencil fill:#11163a,stroke:#5f88ff,stroke-width:4px,color:#ffffff,rx:12px,ry:12px;
    style eigenfunction_stencil fill:#132a3a,stroke:#4ec9ff,stroke-width:2px,color:#ffffff,rx:12px,ry:12px;

    classDef stage6 fill:#2a1a1a,stroke:#f87171,stroke-width:2px,color:#ffffff,rx:12px,ry:12px;
    classDef stage7 fill:#2a1a1a,stroke:#fb7185,stroke-width:2px,color:#ffffff,rx:12px,ry:12px;

    %%--------------------------------------------------------------
    %%  LIGHT‑GRAY ARROW STYLE (so arrows stay subtle)
    %%--------------------------------------------------------------
    linkStyle default stroke:#888,stroke-width:2px

    %%--------------------------------------------------------------
    %% CORE PINN PIPELINE
    %%--------------------------------------------------------------

    subgraph PIML
    direction LR

        subgraph synthetic
        direction LR
            spatial
            observed
        end

        %% Neural parameterizations
        subgraph learned_parameters
        direction TB
            subgraph potential_network
              direction LR
              MLP1 --> potential

            end

            subgraph eigenfunction_networks
            direction LR
                MLP2 --> psi_0
                MLP3 --> psi_1
                MLP4 --> psi_2
            end

            subgraph energy_eigenvalues
            direction TB
                energy_0
                energy_1
                energy_2
            end
        end


        %% Derivatives
        subgraph finite_difference
        direction LR
            eigenfunction_stencil
            potential_stencil
        end

        %% Physics residual
        subgraph residual
           R
        end

        %% Loss terms
        subgraph loss_terms
        direction LR
            loss_physics
            loss_norm
            loss_smooth
            loss_data
        end

        opt

    end

    %%--------------------------------------------------------------
    %% Connections
    %%--------------------------------------------------------------
    step0 --> PIML

    spatial --> MLP1
    spatial --> MLP2
    spatial --> MLP3
    spatial --> MLP4

    psi_0 --> eigenfunction_stencil
    psi_1 --> eigenfunction_stencil
    psi_2 --> eigenfunction_stencil

    potential --> potential_stencil
    potential --> loss_smooth
    potential_stencil --> loss_smooth

    energy_eigenvalues --> R
    energy_eigenvalues --> loss_data

    eigenfunction_stencil --> R
    potential --> R

    R --> loss_physics

    psi_0 --> loss_norm
    psi_1 --> loss_norm
    psi_2 --> loss_norm

    psi_0 --> R
    psi_1 --> R
    psi_2 --> R

    psi_0 --> loss_data
    psi_1 --> loss_data
    psi_2 --> loss_data

    observed --> loss_data

    loss_terms --> opt

    opt --> MLP2
    opt --> MLP3
    opt --> MLP4

    opt --> MLP1
    opt --> energy_eigenvalues

    %%--------------------------------------------------------------
    %%  POST‑TRAINING DIAGNOSTICS
    %%--------------------------------------------------------------
    subgraph post-training
    direction TB
        subgraph POD
        direction TB
            SVD
            sigma
            U
            %% noteW["Wᵀ holds temporal coefficients – not needed for static eigenmode analysis"]:::stage7
            %% noteSpec["‘Spectrum’ = the set of singular values; gaps signal low‑rank structure"]:::stage7

            SVD --> sigma
            SVD --> U
        end
        POD:::stage6

        H["Sanity Checks"]:::stage6
    end
    post-training:::dashed_orange_1

    PIML --> post-training
```