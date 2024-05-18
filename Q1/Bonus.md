<h2>Vision Transformers(ViT) and how they are different form CNN</h2>
<h3>Brief decription of CNN</h3>
<p>The typical CNN architecture starts with convolutional layers that pass through the kernels or filters, from left to right of the image, extracting computationally interpretable features. The first layer extracts low-level features (e.g., colours, gradient orientation, edges, etc.), and subsequent layers extract high-level features. Next, the pooling layers reduce the information extracted by the convolutional layers, preserving the most important features. Finally, the fully-connected layers are fed with the flattened output of the convolutional and pooling layers and perform the classification</p>
<img src="https://www.mdpi.com/applsci/applsci-13-05521/article_deploy/html/images/applsci-13-05521-g002-550.jpg">
<h3>Brief decription of ViT</h3>
<p>ViTs revolutionize image recognition by converting pixels into a series of image patches, subsequently embedding these as tokens in a manner similar to word embeddings in NLP. This method breaks down the image into manageable, comparable pieces, each represented as a vector. These vectors — embedded and processed through the transformer’s layers — allow the model to understand and interpret the visual data’s intricate patterns and correlations, further proving that an image is worth 16x16 words, metaphorically speaking.</p>
<img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*TZAy8tvsN7pMhrEpKVH2Og.jpeg">
<h4>Adapting Self-Attention Mechanisms for Visual Data</h4>
<p>By focusing on the relationships and relevance of different image patches, the architecture facilitates a deeper understanding of the visual content.</p>
<img height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q1/attention_eg.png">
<h4>The Role of Positional Embeddings in Image Recognition Tasks</h4>
<p>Positional embeddings play a critical role in maintaining the spatial hierarchy of visual data, a necessity the pure transformer needed to adapt from NLP to computer vision. These embeddings ensure that despite the non-sequential processing of image patches, the model retains an awareness of their original positioning within the image, enhancing its ability to accurately interpret and classify visual information.</p>
<h3>Differences</h3>
<p>Unlike CNNs, which process images through localized filters, ViTs assess the image in its entirety, providing a more holistic understanding. This distinction enables transformers for image recognition to outperform CNNs, particularly in tasks that benefit from a broader perspective and intricate pattern recognition across the image.</p>
<p>ViT can produce at par results with models like ResNet50 while using lesser computation resources </p>
