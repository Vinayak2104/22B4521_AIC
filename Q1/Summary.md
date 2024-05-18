<h1>Training a CNN on PASCAL VOC Dataset</h1>
<h3>About the Dataset</h3>
<ul>
  <li>The training data contains 17125 images along with there labels</li>
  <li>Each label can belong to more than 1 out of 20 classes present in the dataset, which makes it a multi-label classification problem.</li>
  <li>The test data contains 16135 images but almost all the images in the test data belongs on "person" class,therefore we will be using a part of training set as validation set which will be used to evaluate performance of our model</li>
</ul>
<h3>Data preprocessing</h3>
<ul>
  <li>Normalize the pixel value between 0 and 1.</li>
  <li>Resize all the images to same size. I have used a size of (100x100) to train the models.</li>
</ul>
<h3>Few problems that are needed to be addressed before we move on to train the model</h3>
<img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q1/train_dis_wo_aug.png">
<ul>
  <li>In the image above, it is clear that there is a class imbalance both within each class(mostly negative samples) and between classes(more images where "person" is one of the class )</li>
  <li>To solve the imbalance within each class we will define a custom <b>WeightedCrossEntropy</b> loss function which we account for weights of positive and negative samples within in each class.</li>
  <li>To solve the imbalance between the class we will take help of data augmentation.This will also help to increase the size of dataset and bring more variability to it, which will hopefully make our models more robust </li>
</ul>
<h3>Data Augmentation</h3>
<h4>Transformations used:</h4>
<ul>
  <li>Random rotation between 0 to 25 degrees</li>
  <li>Random horizontal flipping</li>
  <li>Random vertical and horizontal shift by 0.05</li>
</ul>
<p>We will take all the images that does not belong to "person" class and generate <b>two</b> augmented image for each image.</p>
<h3>Approach to multi-label classification</h3>



