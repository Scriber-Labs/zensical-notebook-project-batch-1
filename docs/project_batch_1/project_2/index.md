# Project 2: Low-Fidelity Inverse Schrödinger Problem

!!! abstract "**Overview**"

    === "🥅 Goal"

        The purpose of project 2 is to study operator features that are identifiable in a low fidelity physics-informed machine learning prototype for the inverse Schrödinger problem.    
        
    === "5️⃣ 5 Brunton Steps"

        | **Step** | **Description** | **Completed?** |
        |----------|-----------------|----------------|
        | 1. **Problem formualtion** | Can a physics-informed neural network recover the unknown potential $V(x)$ along with the corresponding eigenfunctions from only noisy spectral data and probability-density snapshots? | ✔️ |
        | 2. **Data collection & curation** | - Uniform collocation grid of spatial points $x\in [-5,5]. <br/> - Noisy energy and probability density observations. | ✔️ |
        | 3. **Neural architecture**        | Two lightwieght neural networks with tanh activations (see [Project 2 architecture diagram](architecture_2.md)) | ⚠️ Both neural networks are scalar-in, scalar-out, fully differentiable, and deliberately kept shallow to preserve interpretibility. |
        | 4. **Loss function**              | All terms are soft penalties with static $\lambda$ weights. | ✔️ |
        | 5. **Optimization**               | - Adam optimizer with a fixed learning rate. <br/> - Forward pass training loop that computes loss terms and uses back propagation to update $V_\theta$ and $\psi_n^\theta$. | ❌⚠️ As in project 1, the optimizer is intentionally vanilla; the aim is to expose how the physics prior interacts with noisy data, not to chase maximal performance |

    === "🌍 Global Design Choices"


