<h2>Step by step approach to tackle a AI/ML problem</h2>
<h4>I will take up the problem statement of Sustanify'24 in which our team secured a 2nd place position out of 250+ team</h4>
<p>Problem Statement and detailed report: https://drive.google.com/drive/folders/1kvJ0W8MhokCaD0rPeLXSgZWnNPnXCRir</p>
<p>Briefly the problem statment wanted us to predict daily average prices of elctricity exchange(similar to stock markets but of electricity) and after that perform a constrained optimization to minimize electricity
procurement cost of a steel plant </p>
<h3>Step 1:Understanding the dataset</h3>
<p>It is very important to understand the data in hand. We should be clear what each column represents and what is its importance</p>
<b>Some key points to keep in mind</b>
<ul>
  <li>Convert each column to correct and optimal datatype. For eg fr storing age you dont need int64,int16 will also work and take up less space</li>
  <li>Looking for outiers in each column that might affect our model performance.</li>
  <img height=300 width=500 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/nontech_Q1/nontech_outlier.png">
  <li>We can see above, the prices for 2010 data had an outlier which had to be removed</li>
  <li>Try to plot graph of each column with output column we might be able to find a mathematical relation like quadratic and make new features using that information.We can also use sone statistical methods like linear collinearity to find linear relations or Spearman's coefficient to capture non linear relations.</li>
  <h4>Daily avg price Vs volume traded for 2010</h4>
  <img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/nontech_Q1/price_vs_volume.png">
  <p>We can observe that there is no relation between daily avg price and volume traded therefore it might not be a important feature</p>
  <h4>Price fluctution at hourly basis</h4>
  <img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/nontech_Q1/Screenshot%202024-05-18%20231520.png">
  <li>Here we can observe a clear trend in price on hourly basis. Early mornings prices are low as compared to afternoon and this will be useful in both feature engineering and optimization.</li>
  <h4>Price fluctution at monthly basis</h4>
  <img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/nontech_Q1/monthly_var.png">
  <li>We can see some months have have higher prices and some have less therefore month or week can also be important features </li>
</ul>
<h3>Step 2: Feature Engineering</h3>
<p>Based on the insights gathered from the analysis above we will now construct some important features.</p>
<p>We found out that hour,week,month are some important factors but there are cyclic in nature therefore we have to find out some way to capture the cyclic nature </p>
<h4>Cosine and Sin of hours,week,month</h4>
<img width=500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/nontech_Q1/sin_cos.png">
<p>Using sine and cosine both we can capture the cyclicity as depicted in the image above.</p>



