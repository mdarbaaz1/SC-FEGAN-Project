# SC-FEGAN-Project

# SC-FEGAN

It is a face editing softaware by Youngjoo Jo and Jongyoul Park check the paper in [arXive](https://arxiv.org/abs/1902.06838). It allows editting faces using masks, sketches and colors. The [implementation](https://github.com/JoYoungjoo/SC-FEGAN) is in TensorFlow and I just ported it to work in the browser using javascript and python. The system uses end-to-end convolutional neural network to generate the images taking a batch of four inputs 

*   **Masked Image** we use a mask to input incomplete image to the generator 
*   **Sketch** a binary image that represent sketches to guid the generator 
*   **Color** rgb image that can be used to add more control to the generated images. 
*   **Noise** a random input as a seed to the generator 

To train our the model, they used the CelebA-HQ dataset after several preprocessed as the following . First ran-domly select 2 sets of $29,000$ images for training and $1,000$
images for testing. Then the images are resized the images to $512 \times 512$ pixels
before attaining the sketch and color dataset.  The input training images are appended with 

*   **Masking** free-form masking with eye-positions. 
*   **Sketches** HED is used to create the sketches of the faces. 

The network architecture includes the generator and descriminator. 



*   **Generator** a simple U-Net model with all the conv layers replaced with gated convolutions. The [gated convolutoions](https://arxiv.org/abs/1806.03589) solve the issue of vanilla convolution that treats all input pixels as valid ones and generalize partial convolution by providing a learnable dynamic feature selection mechanism for each channel at each spatial location across all layer. 

*  **Descrinimator** has [SN-PatchGAN](https://arxiv.org/abs/1806.03589) structure with no ReLu applied to the GAN loss. 



![alt text](https://raw.githubusercontent.com/JoYoungjoo/SC-FEGAN/master/imgs/teaser.jpg)
