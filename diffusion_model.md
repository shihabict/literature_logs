## What is the Diffusion Model?
It is a branch of AI that actually learns to predict noise. There are two steps in the diffusion process:
 - **Forward Process (Destroying Phase)**:
   - In this process, the model injects noise into the data. At each timestep $t$, it increases the noise, and at the final T, the data become indistinguishable.
   - There is no learning in this phase, this phase only turns the original data into a noisy version.
  
 - **Reverse Process (Reverse Diffusion)**:
   - ML learning happens in this phase.
   - We train a neural network (U-Net) that actually learns to predict the noise that was added in the first Phase.
   - At every time step, if the model can predict the noise accurately, we subtract that from the noisy data and move one step ahead to the clean data.
   - To generate a new image, the model starts with pure random noise and asks to denoise it repeatedly utill a high fidelity data is generated.
    
