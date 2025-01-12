# Generative AI on Cloud

## Gen AI Project Life Cycle
### 1: Defining the Use Case (Scope)
### 2: Choosing the right model 
#### 2.1: Foundation Models 
- AI21 labs (Jurassic-2 Series)
- Titan by Amazon
- Claude by Anthropic
- Command by Cohere
- Llama 3 by Meta
- Mistral by Mistral AI
- Stable Diffusion by Stability AI
#### 2.2: Custom LLM
### 3: Adapt and Align Modules 
#### 3.1: Prompt Engineering, FineTuning, Training with Human Feedback
#### 3.2: Evaluation
### 4: Deployment
### 5: Application Integration
#### 5.1: LLMOps: Optimize and Deploy models for Inferencing (Eg: Groq-LPU)
- Use AWS, Azure, GCP
#### 5.2: Build LLM Powered Application

## End to End Usecase using AWS Cloud (Blog Generation in AWS)
![Screenshot 2025-01-11 142208](https://github.com/user-attachments/assets/bf3426e4-2075-4f5d-a5cf-04ee26caddbc)
### AWS Lambda 
#### Code to trigger Lambda function 
- imports boto3, botocore.config, json, response
      - boto3: AWS SDK that provides Python API to build apps on S3, EC2, DynamoDB. *allows you to create, configure and manage AWS services.*
          - Configure a service: boto3.client(*params to specify Configurations*)
- Function 1: Blog generate using Bedrock(blogtopic)
      - Provide prompt and its output configurations(max_gen_length, temperature, top_p)
      - Configure bedrock (boto3.client), invoke the model (invoke_model), get response content from the response (response.get()), convert it from JSON string to python dictionary (json.loads()),print it, retrieve only necessary key value pairs from dictionary and return it.
- Function 2: Save Blog Details in S3
      - Configure S3 (boto3.client), specify bucket, key, body and put object in the bucket.
- Function 3: Lambda Handler
      - Whenever API gateway sends a post event (i.e. Fn 1 is triggered), capture response along with timestamp and store it in S3 bucket (i.e. Trigger Fn 2)
  
- Note: Use layers in Lambda to add/update any packages. (*Makes sure that packages are up-to-date*)
      - Choices: AWS layers, Custom layers, Specify an ARN.
      - Can upload package file, selection Programming language version etc

### Create API gateway and integrate it with Lambda. 
- **Develop: Routes, Authorizations, Integrations, CORS, Reimport, Export**
- Choose Type of API (HTTP, WebSocket, etc) and add routes and methods (POST, /blog), it will provide you an ARN. *Authorization can be used to protect API from unauthorized access.*
- **Deploy: Stages**
- Automatic deployment of API is triggered in specified environment.(Dev, QA, Staging). It will give you a URL to invoke this API.

### Create S3 bucket
- Bucket name has to be unique
- **(Create Bucket, Bucket versioning, Upload Data, Manage Permissions,Set Configurations,Enable Replication, Lifecycle Management, Data Management, Monitoring and Logging)

### Deployment of Hugging face models using Sagemaker
- Sagemaker provides ML capabilities that are purpose built for data scientists and developers to prepare, build, train and deploy high quality ML models efficiently.
1. Create a Domain (Set up for Organization/ Single User)
    - User profiles: 1 user is created by default. *Users can launch Studio, Canvas, Tensorboard, and Profiler*) separately.
    - Environment: 
    - Domain Settings:
2. Sagemaker Studio has an entire ecosystem
    - JupyterLab, Code Editor
    - Prebuilt & automated solutions:  JumpStart, Model evaluations, AutoML.
3. Create a JupyterLab Space
   - Space Mgmt: self-contained, durable storage container (like a filesystem), to which the app can be attached. (Storage, Lifecycle Config, Attach custom EBS) => *Run Spaces*
4. Choose options for Notebook, Console, Terminal, Markdown file etc  
   
   

  
