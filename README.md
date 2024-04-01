# ML4SCI GSOC GENIE Task
## Common Task 1. Auto-encoder of the quark/gluon events

At the LHC, a bunch of protons are accelerated and made to collide with each other which produces constituent particles. The set of scattered particles are called jets and snapshots of jets are called jet images. Now, we cannot save every such image as the collision frequency is extremely high and we have limited storage capacity. Another issue that we deal with is finding anomalies in such jet images. If the anomalies are something out of the standard known theory we may not be able to identify them.

Thus, We use Autoencoders which are a class of neural networks that learn the inherent pattern of the data and represent it in lower dimensions. This can be used to compress the original image into the latent dimension and once it is learned if it is fed with an image containing anomaly it will fail to reconstruct it as the data it is trained on is predominantly of non-anomalous images. This failure to reconstruct the image can be quantified using the reconstruction loss.

## Task 
1. Train an auto-encoder to learn the representation based on three image channels (ECAL, HCAL, and Tracks) for the dataset.
2. Show a side-by-side comparison of original and reconstructed events.

## Training and result
The data set was trained on a VAE and Beta-VAE architecture with the following parameters:
```
Learning Rate: 3e-4
Optimizer: Adam
Loss: Binary Cross Entropy + KL Divergence
Epochs: 30
```
## Result:
### VAE 
<img src="images/vae.png" width="350" height="500">

### Beta VAE
<img src="images/beta_vae.png" width="350" height="500">

## Loss
### VAE
<img src="images/loss_vae.png" width="500" height="500">

### Beta VAE
<img src="images/loss_beta.png" width="500" height="500">

# Conclusion:

As it can be seen from above the generated images are not very good. The reasons for that can be:
1.   Since this is not typical RGB data the model does not behave in a way that it would for RGB data.
2.   Although traditional transformations can be applied there is not much difference. For Example, Rotating an image won't do us any good as the data is kind of rotation invariant. Similar to other transformations.
3. Since all of the dataset wasn't used so the training wasn't perfect. There may be a scope of Overfitting.
4. The hyperparameters may not be right and further fine-tuning will be necessary.
5. Using the Beta-VAE to understand the disentangled latent factor didn't help. The reason may be data from all the channels may seem similar to the model.

Ways to improve the model:



1.   Other Architectures need to be explored.
2.   The hyperparameters should be tuned more.
3.   Other Generative models can be used to learn the representation such as the Diffusion model etc.
4. Since the images are not the typical RGB images and based on research converting them to graphs and applying Graph VAE may yield better results.
