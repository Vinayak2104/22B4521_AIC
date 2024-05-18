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
</ul>
