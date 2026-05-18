## Variants of Diffusion Models
 While the standard diffusion model learns to generate random data from scratch, applying it in the real-world complex ITS requires significant 
 control and efficiency. However, researchers use two major variants to achieve this efficiency.

 1. Conditional Diffusion Model
 2. Latent Diffusion Model (LDM)

## Conditional Diffusion Model:
Standard Diffusion models are unconditional; they only use the noisy data and the current step of the denoising process. Whereas the conditional diffusion model allows us to inject extra information,
for example, historical traffic data, road maps, or text prompts to control what exactly to generate. Conditioning Mechanisms:

<img src="images/conditiona_variants.png" width="500" height="200">
   
    *Figure 1: Different condition mechanisms for diffusion models*

### 1. Concatenation-based CDM
The conditioning information is directly added to the data $x$ or to the diffusion step $t$. It is simple and highly effective for tasks like predicting future traffic flow or vehicle trajectories

### 2. Cross-attention-based CDM
Cross-attention is used when the condition and the output are from different modalities. For example, when we would like to use both the prompt and the BEV feature to generate a scene.

### 3. Classifier-Based CDM
This approach uses an external classifier (like a cost function and a reinforcement learning algorithm) to guide the generation process. It makes sure that the generated trajectory is actualy obey traffic rules and physical constraints.

### 4. Classifier-free-based CDM
This method accumulates both conditional and unconditional diffusion models without training a separate classifier.
It works by blending the output of conditional and unconditional diffusion models, which is highly useful for generating realistic scenarios. 
