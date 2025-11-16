# Model-Merging Examples
This repository provides a Jupyter-based implementation of the model-merging techniques introduced in MergeME: Model Merging Techniques for Homogeneous and Heterogeneous Mixture-of-Experts (MoE) Models (Zhou et al., 2024). The notebook demonstrates how to merge dense expert LLMs into a unified Mixture-of-Experts model.

## Key Model Merging Techniques

This project explores and implements several advanced model merging techniques:

### 1. Homogeneous Model Merging

This section focuses on merging homogeneous models, specifically addressing the challenge of parameter interference in non-FFN layers. Traditional merging methods often struggle with these layers, leading to performance degradation. We utilize advanced merging methods like **Dare (Disentangled and Re-Entangled)** and **Ties (Task-Independent Expert Selection)** to mitigate this interference.

*   **Dare:** This method aims to disentangle the contributions of different experts and then re-entangle them in a way that minimizes destructive interference, particularly in shared layers beyond the FFNs.
*   **Ties:** Ties focuses on identifying and preserving the most critical parameters from each expert, effectively "tying" them together to form a robust merged model. This is crucial for maintaining the specialized knowledge of each expert while integrating them into a cohesive MoE.

*(Image: Diagram illustrating homogeneous model merging with Dare/Ties, showing how non-FFN layers are handled.)*

### 2. Perplexity-Based Routing

A significant challenge in Mixture-of-Experts (MoE) models is the routing mechanism, which typically requires extensive fine-tuning to effectively direct inputs to the most suitable experts. This project implements a novel **perplexity-based routing heuristic** that allows for efficient routing without the need for extensive fine-tuning.

This heuristic leverages the perplexity of an input with respect to each expert to determine the most appropriate expert(s) for processing. By calculating how "surprised" each expert is by a given input, we can infer its expertise and route the input accordingly. This approach significantly reduces the computational cost and time associated with training MoE routers.

*(Image: Flowchart demonstrating perplexity-based routing, showing input, perplexity calculation for each expert, and routing decision.)*

### 3. Heterogeneous Model Merging (Conceptual Approach)

While the primary focus is on homogeneous merging, this repository also conceptually explores **heterogeneous model merging**. This involves merging models that possess different architectures, a more complex scenario than merging models of the same type.

The conceptual approach involves the use of **projector layers**. These layers act as bridges, transforming the representations from one model's architecture into a compatible format for another. This allows for the integration of diverse models, each potentially specialized in different tasks or data modalities, into a unified framework. This section outlines the theoretical underpinnings and potential implementation strategies for such a system.

*(Image: Diagram illustrating heterogeneous model merging with projector layers, showing different model architectures connected via projectors.)*
