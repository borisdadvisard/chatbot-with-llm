# chatbot-with-llm
DEPLOYMENT & INTEGRATION OF A PRE-TRAINED CHATBOT USING DOCKER CONTAINER 

--------
# Business Context: 
A global enterprise in the retail industry wants to deploy an AI assistant to all its employees internally and asked me to implement a proof of concept. I use Amazon SageMaker to host the open-source HuggingFace FLAN-T5 XL model, which is designed for multiple Text2Text generation tasks. I integrate AWS Lambda functions and Amazon Lex v2 interface to provide a sophisticated chatbot that is ideal for enhancing customer support, streamlining business queries and providing a seamless conversational experience in multiple languages. See the solution architecture diagram below.

![Solution Architecture Diagram](https://github.com/user-attachments/assets/a935be36-59c2-4b23-8870-72055c8aee06)


-------
# Integration Steps (see Jupyter notebook):
- 1/ Download the open-source encoder-decoder LLM model FLAN-T5 XL from HuggingFace
- 2/ Configure bot's intent and fallback intent for unmatched user inputs (Lex V2)
- 3/ Select hardware (high-performance GPU-based instances for ML inference: ml.g5.2xlarge)
- 4/ Retrieve the inference docker container uri with script_uris.retrieve() method
- 5/ Create an Amazon SageMaker real-time inference endpoint programmatically, using SageMaker Python SDK (IaaS)
- 6/ Define functions: query_endpoint() and parse_response()
- 7/ Deploy with model_predictor = model.deploy() method (it can take up to 15min)
- 8/ Test functionality with 3 example prompts
- 9/ Serve the model through API: configure AWS Lambda to invoke the endpoint
- 10/ Expose a basic front-end interface to enable message interactions through Amazon Lex V2, invoking the Lambda function just created
- 11/ Test by interacting with the bot from the interface (see screenshot below).
=> This is an end-to-end, functional proof of concept of a conversational chatbot solution with minimal operational overhead.


![Demo Chatbot Interface](https://github.com/user-attachments/assets/03b8b620-54a5-4d10-a0af-5c3068d1f8a5)

-------
# Key Learnings: 
- No need to reinvent the wheel - use what's already available and build on top
- Speed, accuracy, safety and reliability are key to a high user adoption

