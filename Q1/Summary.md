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
