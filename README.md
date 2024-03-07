# ML4SCI GSOC GENIE Task
## Common Task 1. Auto-encoder of the quark/gluon events

At the LHC, a bunch of protons are accelerated and made to collide with each other which produces constituent particles. The set of scattered particles are called jets and snapshots of jets are called jet images. Now, we cannot save every such image as the collision frequency is extremely high and we have limited storage capacity. Another issue that we deal with is finding anomalies in such jet images. If the anomalies is something out of the standard known theory we may not be able to identify them.

Thus, We use Autoencoders which are a class of neural networks that learn the inherent pattern of the data and represent it in lower dimensions. This can be used to compress the original image and once it learns the structure of the image if it is shown something different it will fail at representing it in a lower dimension. This failure to compress can be quantified using a reconstruction loss and when this loss crosses a certain threshold we can identify the image as an anomalous image.

## Task 
1. Train an auto-encoder to learn the representation based on three image channels (ECAL, HCAL and Tracks) for the dataset.
2. Show a side-by-side comparison of original and reconstructed events.

## Dataset
The dataset consists of Jet Images with three channels which are Tracks, ECAL and HCAL.


