[image0]: ./Samples/loss.png
[image1]: ./Samples/1.png
[image2]: ./Samples/2.png
[image3]: ./Samples/3.png
[image4]: ./Samples/4.png
[image5]: ./Samples/5.png
[image6]: ./Samples/6.png
[image7]: ./Samples/7.png
[image8]: ./Samples/8.png
[image9]: ./Samples/9.png
[image10]: ./Samples/10.png
[video1]: ./videos/1.mp4
[video1]: ./videos/2.mp4
[video1]: ./videos/3.mp4

# Semantic Segmentation
### Introduction
This project aims to create a Fully Convolutional Network (FCN) to label the pixels of a road in images using `kitti Road dataset` and `VGG16` pre-trained model.

### Model Training

The model is trained based on the following hyperparameter:

| Parameter        | Value   | 
|:-------------:|:-------------:| 
| Learning rate      | 0.00001        | 
| Batch Size      | 5      |
| Epochs      | 50      |
| Regularization factor     | 0.001        |
| Keep Probability     | 0.5        |


During the training, this is the loss among the `50` epochs:

<img src="./Samples/loss.png" height="350" width="600"/>

### Model Results

<p>
  <img src="./Samples/1.png" height="120" width="280"/>
  <img src="./Samples/2.png" height="120" width="280"/>
  <img src="./Samples/3.png" height="120" width="280"/>
  <img src="./Samples/4.png" height="120" width="280"/>
  <img src="./Samples/5.png" height="120" width="280"/>
  <img src="./Samples/6.png" height="120" width="280"/>
  <img src="./Samples/7.png" height="120" width="280"/>
  <img src="./Samples/8.png" height="120" width="280"/>
  <img src="./Samples/9.png" height="120" width="280"/>
</p>

Check also these 3 videos of different roads after applying the FCN model [Here](./videos/1.mp4), [Here](./videos/2.mp4), [Here](./videos/3.mp4) 

### Setup
##### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)
##### Dataset
Download the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip).  Extract the dataset in the `data` folder.  This will create the folder `data_road` with all the training a test images.

### Start
##### Implement
Implement the code in the `main.py` module indicated by the "TODO" comments.
The comments indicated with "OPTIONAL" tag are not required to complete.
##### Run
Run the following command to run the project:
```
python main.py
```
**Note** If running this in Jupyter Notebook system messages, such as those regarding test status, may appear in the terminal rather than the notebook.

### Submission
1. Ensure you've passed all the unit tests.
2. Ensure you pass all points on [the rubric](https://review.udacity.com/#!/rubrics/989/view).
3. Submit the following in a zip file.
 - `helper.py`
 - `main.py`
 - `project_tests.py`
 - Newest inference images from `runs` folder  (**all images from the most recent run**)
 
 ### Tips
- The link for the frozen `VGG16` model is hardcoded into `helper.py`.  The model can be found [here](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/vgg.zip)
- The model is not vanilla `VGG16`, but a fully convolutional version, which already contains the 1x1 convolutions to replace the fully connected layers. Please see this [forum post](https://discussions.udacity.com/t/here-is-some-advice-and-clarifications-about-the-semantic-segmentation-project/403100/8?u=subodh.malgonde) for more information.  A summary of additional points, follow. 
- The original FCN-8s was trained in stages. The authors later uploaded a version that was trained all at once to their GitHub repo.  The version in the GitHub repo has one important difference: The outputs of pooling layers 3 and 4 are scaled before they are fed into the 1x1 convolutions.  As a result, some students have found that the model learns much better with the scaling layers included. The model may not converge substantially faster, but may reach a higher IoU and accuracy. 
- When adding l2-regularization, setting a regularizer in the arguments of the `tf.layers` is not enough. Regularization loss terms must be manually added to your loss function. otherwise regularization is not implemented.
 
### Using GitHub and Creating Effective READMEs
If you are unfamiliar with GitHub , Udacity has a brief [GitHub tutorial](http://blog.udacity.com/2015/06/a-beginners-git-github-tutorial.html) to get you started. Udacity also provides a more detailed free [course on git and GitHub](https://www.udacity.com/course/how-to-use-git-and-github--ud775).

To learn about REAMDE files and Markdown, Udacity provides a free [course on READMEs](https://www.udacity.com/courses/ud777), as well. 

GitHub also provides a [tutorial](https://guides.github.com/features/mastering-markdown/) about creating Markdown files.
