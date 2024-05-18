<h2>Dual Chatbot System</h2>
<h3>Motivation behind making this</h3>
<p>There are many times when we come across a research paper and we are not able to understand it or have many doubts in those situations we can just simply make a chatbot and provide it relevant documents and it can answer your questions.</p>
<p>But sometimes we dont even know what questions to ask specially when reading a paper from another domain, in those kind of situations this dual chatbot system will ask the right questions and also provide answers to them.</p>
<img width= 500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q2/overview2.png">
<p>The above figure shows a high level overview of how will be the flow.</p>
<p>We will be using the original paper of ViT to evaluate the performance, this will also help in bonus part of Q1 ;)</p>
<h3>Example</h3>
<img src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q2/eg1.png">
<img src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q2/eg2.png">
<h3>Observations</h3>
<ul>
  <li>We can observe that without any user interaction the journalist bot beautifully drives the interview and asks relevant questions.</li>
  <li>Implementation of RAG also helps model to reduce halucination since we are providing the relevant context from the paper which makes sure the llm uses that information rather than creating something of its own.</li>
  <li>Implementation of RAG also improves transparency since for every answer we are given the page-numbers to refer and i have also added feature where the relevant parts are highlighted in the pdf of paper also.</li>
  
</ul>
