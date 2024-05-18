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
  <li>Here we can observe a clear trend in price on hourly basis. Early mornings prices are low as compared to afternoon and this will be useful in both feature engineering and optimization.One more thing that we observed that prices on an average were decreasing from 2010-2016 but suddenly increased in 2017 there it is possible that 2017 might be an outlier year like covid therefore we have to consider that possibilty also.</li>
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
<p>We also create a feature to differentiate other years from 2017 due to the sudden jump in prices discussed above.</p>
<h3>Step 3:Splitting the data</h3>
<p>Since we are dealing with time series data it is important to maintain the temporal nature of the data, therefore we used data from 2010-2016 for training and 2017 for validation and then after finalising the best model we take the whole data for training the final model.</p>
<h3>Step 4: Finding best model</h3>
<ol>
  <li>First model we tried was random forest regressor.We can use libraries like optuna to find the best hyperparameters.</li>
  <li>Second model we tried was XGBoost regressor.We can again use optuna to tune the hyperparameters</li>
  <li>It is also better and advisable to try models build for timeseries forecasting like ARIMA,SARIMA etc.</li>
</ol>
<h3>Step 5: Evaluating Model Performance</h3>
<p>To know how well your model is performing it is important to choose the correct metric. FOr this regression problem we will use R2 score.</p>
<p>Based on the R2 score of validation set we will select which model to use at the end.</p>
<h3>Step 6: Inferences from the Output</h3>
<p>Using the hourly prices predicted for 2018 we will optimize the daily average eletricity utilization cost of the steel plant. As we observed a hourly trend in the price we will also do the optimization on the hourly basis.</p>
<b>Given information</b>
<ol>
  <li>
    Demand:- 1,200 MWh/ Day
  </li>
  <li>
    Supply capacities:- 
    <ul>
      <li>Solar Power Plant – 150 MWh/day fixed @ 0 EUR</li>
      <li>State Electricity Grid is 57.62 EUR/MWh @ fixed price</li>
      <li>Energy Exchange :- Variable prices per hour</li>
    </ul>
  </li>
  <li>Minimum 20% renewable energy of 1200 MWh is required </li>
  <li>Energy drawn in +ve from each source </li>
</ol>
<b>Assumptions</b>
<ol>
  <li>Total energy requirement is 1200MWh/day so considering steel 
plant is working 24 hrs with same efficiency demand for each hour 
will be 50 MWhr.</li>
  <li>Exchange supply limit is in range of our requirements</li>
  <li>Total solar energy will be used between H11 to H 13, and no 
energy will be drawn from grid and exchange in these hours.Since these are peak sunny hours and also the hours where exchange prices are maximum.</li>
</ol>
<b>Additional contraints for hourly requirements</b>
<ul><li>
  50 MWhr = Energysolar + EnergyExchange + Energygrid
</li></ul>
<p>Since all the constraints are linear we will go with linear programming as it is simple and computationally effective. </p>



