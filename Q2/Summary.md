<h2>Dual Chatbot System</h2>
<h3>Motivation behind making this</h3>
<p>There are many times when we come across a research paper and we are not able to understand it or have many doubts in those situations we can just simply make a chatbot and provide it relevant documents and it can answer your questions.</p>
<p>But sometimes we dont even know what questions to ask specially when reading a paper from another domain, in those kind of situations this dual chatbot system will ask the right questions and also provide answers to them.</p>
<img width= 500 height=300 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q2/overview2.png">
<p>The above figure shows a high level overview of how will be the flow.</p>
<p>We will be using the original paper of ViT to evaluate the performance, this will also help in bonus part of Q1 ;)</p>
<p>Also after every question-answer pair the user is given choice to ask there own questions in case they want a more elaborate explanation on some specific topic.</p>
<h3>Example</h3>
<img src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q2/eg1.png">
<img src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q2/eg2.png">
<h3>Stack used while making the chatbot </h3>
<ul>
  <li>Langchain</li>
  <li>gpt-3.5 turbo as base llm.</li>
  <li>OpenAI embeddings to generate embeddings.</li>
  <li>FAISS vector store for storing the embeddings.</li>
</ul>
<h3>Observations</h3>
<ul>
  <li>We can observe that without any user interaction the journalist bot beautifully drives the interview and asks relevant questions.</li>
  <li>Implementation of RAG also helps model to reduce halucination since we are providing the relevant context from the paper which makes sure the llm uses that information rather than creating something of its own.</li>
  <li>Implementation of RAG also improves transparency since for every answer we are given the page-numbers to refer and i have also added feature where the relevant parts are highlighted in the pdf of paper also.</li>
  <img width=500 src="https://github.com/Vinayak2104/22B4521_AIC/blob/main/Q2/highlight.png">
  <li>RAG also enables us to use llms on our own data without fine-tuning which requires lot of data and computational power.</li>
  <li>RAG also enables us to use llms on our own data without compromising privacy.</li>
</ul>
<h4>Role of Attension in improving chatbot performance</h4>
<p>We have used "gpt-3.5" turbo which has attention built-in in its architecture</p>
<ul>
  <li>Imagine we have a sentence, and you want to predict the next word. The attention mechanism will look at all the previous words and decide which ones are most relevant to making the prediction. It does this by assigning a numerical value (weight) to each word. Words with higher weights have more influence on the prediction.</li>
  <li>For eg the meaning of model in "A machine learning <b>model</b>" is different from model in "A fashion <b>model</b>".The attention block is whats responsible for figuring out which words in the context are relevant for updating the meaning of which other words and how exactly those meanings or embeddings of each word should be updated.</li>
  <li>Attention in makes the raw word/token embeddings more richer in terms of context in which they are used.</li>
</ul>
<h3>Improvements that can be done</h3>
<ul>
  <li>Provide a transcript of conversation in PDF format</li>
  <li>Create a user friendly UI for the chatbot</li>
  <li>Since the generated interview scripts can serve as condensed yet richer (than paper abstracts) versions of the full papers, we could first accumulate the scripts for a variety of papers in a specific research field, and then request a separate llm to generate comprehensive reviews of that field, based on analyzing the accumulated interview scripts. This feature would be especially valuable for researchers when they are initiating a new research project or a literature review paper.</li>
</ul>
<h3>Limitations</h3>
<ul>
  <li>The author bot still cannot explain complex mathematics in simple terms using simple notations it just gives an high level overview of whats being done.</li>
  <li>While we have reduced the amount of halucination by using RAG it is possible that in some cases it still gives non-sensical answers.</li>
  <li>When users asks its own question in the middle, it doesn't affect how the journalist bot will steer the conversation further which can lead to duplicate questions being asked somtimes.Although we can maybe fix that by adding the questions asked by user into memory of journalist bot.</li>
</ul>
<h3>Answer to bonus question of Q1 provided by our chatbot</h3>
<p>The Vision Transformer (ViT) architecture differs from traditional Convolutional Neural Networks (CNNs) in processing image data for classification tasks by utilizing a pure transformer approach. Unlike CNNs, which rely on convolutional operations to extract features hierarchically, ViT applies self-attention mechanisms to capture global dependencies between image patches. This means that ViT processes images by dividing them into patches, flattening these patches into sequences, and then applying transformer blocks to learn relationships between patches directly. This allows ViT to perform well on image classification tasks, especially when pre-trained on large datasets, while requiring fewer computational resources compared to traditional CNNs.</p>


