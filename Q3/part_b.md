<h3>What metric to use to measure likeliness between two vectors</h3>
<h4>Euclidean distance</h4>
<p>One choice can be euclidean distance, lesser the distance closer the two vectors in n-dimesional space meaning they are more similar. But the problem with euclidean distance begins in higher dimension,since things become more sparse in higher dimensions euclidean distances lose there meaning because mean,min,max distance between points become almost equal</p>
<h4>Cosine Similarity</h4>
<p>To dodge the curse of dimensionality we can take help of cosine similarity(or dot product) to find likeliness of two vectors.</p>
<p>More the cos(angle between two vector) lesser is the angle between two vectors.Its value is between [-1,1], 1 representing very similar(happiness,joy) and -1 representing completely opposity(success,failure)</p>
<img height=300 width=500 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q3/cos_sim.webp">
<ul>
  <li>Cosine similarity is scale invariant i.e. Cosine similarity is not affected by the magnitude of the vectors.</li>
  <li>Easy to implement and interpret.</li>
</ul>
<h3>Comparing self-trained skip gram model and pretrained Google Gensim trained on Google news data</h3>
<h4>Self-trained</h4>
