# ML4SCI GSOC GENIE Task
## Common Task 1. Auto-encoder of the quark/gluon events

At the LHC, a bunch of protons are accelerated and made to collide with each other which produces constituent particles. The set of scattered particles are called jets and snapshots of jets are called jet images. Now, we cannot save every such image as the collision frequency is extremely high and we have limited storage capacity. Another issue that we deal with is finding anomalies in such jet images. If the anomalies is something out of the standard known theory we may not be able to identify them.

Thus, We use Autoencoders which are a class of neural networks that learn the inherent pattern of the data and represent it in lower dimensions. This can be used to compress the original image and once it learns the structure of the image if it is shown something different it will fail at representing it in a lower dimension. This failure to compress can be quantified using a reconstruction loss and when this loss crosses a certain threshold we can identify the image as an anomalous image.

## Task 
1. Train an auto-encoder to learn the representation based on three image channels (ECAL, HCAL and Tracks) for the dataset.
2. Show a side-by-side comparison of original and reconstructed events.

## Training and result
The data set was trained on a VAE and Beta-VAE architecture with the following parameters:
```
Learning Rate: 3e-4
Optimizer: Adam
Loss: Binary Cross Entropy + KL Divergence
Epochs: 30
```
### Result:
## VAE 
![Original Image V/S Reconstructed for VAE](images/vae.png =250x250) 
## Beta VAE
![Original Image V/S Reconstructed for Beta-VAE](images/beta_vae.png =250x250)
### Loss
## VAE
![Loss for VAE](images/loss_vae.png) 
## Beta VAE
![Loss for VAE](images/loss_beta.png) 

# Conclusion:

As it can be seen from above the generated images are not very good. So reasons for that can be:
1.   Since this is not typical RGB data the model does not behave in a way that it would for an RGB data.
2.   Although traditional transformations can be applied but there is not much difference. For Example, Rotating a image won't do us any good as the data is kind of rotation invariate. Similar for other transformations.
3. Since all of the dataset wasn't used so the training wasn't perfect. There may be a scope of Overfitting.
4. The hyperparameters may not be right and further fine tuning will be neccessary.
5. Using the Beta-VAE to understand the disentagled latent factore didn't helped. The reason may be data from all the channels may seem similar to the model.

Ways to improve the model:



1.   Other Architectures need to be explore.
2.   The hyperparamters should be tuned more.
3.   Other Generative models can be used to learn the representation such as Diffusion model etc.
4. Since the images are not the typical RGB images and based on research converting them to graph and applying Graph VAE may yield better results.
