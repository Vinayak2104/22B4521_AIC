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
<img  width=1000 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q1/rough_model_arch.png">
<p>The above image shows the rough architecture that we will be using.</p>
<ul>
  <li>We will treat the multi-label classification problem as 20 binary classification problem, hence sigmoid is used instead of softmax in the output layer.</li>
  <li>Since the number of images in our dataset is less,it is good practice to use to a pretrained model and fine tune the dense layers and convolutional layers towards the end of the architecture on our data.</li>
</ul>
<h3>VGG16</h3>
<p>The first model that we will be trying is VGG16. We will freeze all the layers except the last 4 and add our own dense layers for the downstream task.</p>
<p><b>Note:</b> Accuracy is not a good metric here due to the imbalance present, therefore we will be using area under <b>precision-recall curve</b> as our metric during training.</p>
<h4>VGG 16 performance on validation set</h4>
<h5>Classification Report</h5>
<img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q1/vgg_cr.png">
<p>The performance seems good, but we can try one more thing to improve the performance which is optimize the cutoff threshold for each class. The classification report shown above is generated using 0.5 as the cutoff probablity.</p>
<p>Now we will use precision-recall curve to find the best cutoff probablity for each class.</p>
<p><b>Note:</b> We could also use ROC( receiver operating characteristics) curve for the same, but it is advised to use precision-recall in case of imbalanced datasets since there is no involvement of <b>True negatives</b> in calculations of precision and recall, where as true negative plays a role in calculation of False positive rate used in ROC.</p>
<h5>Steps to calculate best cutoff probablity</h5>
<ol>
  <li>Pick a class, and calculate F1 score for each threshold value.</li>
  <li>Pick threshold with maximum F1 score as cutoff threshold.</li>
  <li>Repeat above steps for rest of the classes.</li>
</ol>
<h5>Classification Report using new cutoff probablities</h5>
<img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q1/vgg_cr_thresh.png">
<p>We can clearly observe an improvement in the F1 score.</p>
<h3>ResNet50</h3>
<p>The second model that we will be trying is ResNet50. We will freeze all the layers except the last 50 and add our own dense layers for the downstream task.</p>
<h4>Resnet50 performance on validation set</h4>
<h5>Classification Report</h5>
<img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q1/resnet_cr.png">
<h5>Classification Report using new cutoff probablities</h5>
<img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q1/resnet_cr_thresh.png">
<p>Find cutoff probabilities using PR curve shows improvement in ResNet50 also but overall we can see that VGG16 performs better on our dataset</p>
<h4><b>VGG16 is the winner here :)</b></h4>
<h3>Making predictions</h3>
<p>As descibed above the test dataset contains images mostly with only "person" class, therefore according to me it is better to make the visualize some predictions from the validation set,although classification report on the test set is available in the notebook</p>
<h4>VGG16</h4>
<img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q1/vgg_val_preds.png">
<h4>ResNet50</h4>
<img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q1/resnet_val_pred.png">
<p>Both the models still struggle to identify all the labels correctly when images belong to more than one label</p>
<h3>Discussing some problems and probable improvements that can be done</h3>
<h4>Problems</h4>
<ul>
  <li>Due to limited computational resources, i had to use an image size of (100,100) for training both the models and these models were not pretrained on images of these sizes.Also smaller size of images affect the quality of predictions due to reduced quality of data.</li>
  <li>I could only generate few augmented samples for each image due to limited computational resources, more data might lead to better performance </li>
  <li>It was quite easy for our model to overfit due to heavy imbalance present.</li>
  <li>Due to limited data and computational resources i could not try finetuning all the layers in both the models.</li>
  <li>Lastly <b>hundreds</b> of errors and bugs during coding.</li>
</ul>
<h4>Improvements and what more can we try</h4>
<ul>
  <li>Using more data and larger image sizes can potentially improve the performance</li>
  <li>Using a weighted mean at the time of combining loss from each of 20 class may handle class imbalance better</li>
  <li>A combination of CNN with attention or ViT with CNN will be interesting to try and see how they perform.</li>
</ul>
<h3>Resources Used</h3>
<ol>
  <li>https://towardsdatascience.com/evaluating-multi-label-classifiers-a31be83da6ea</li>
  <li>https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-imbalanced-classification</li>
</ol>







