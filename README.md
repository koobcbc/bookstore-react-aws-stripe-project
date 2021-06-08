## Setting Up / Installation
- You need node.js, npm, git
- https://docs.amplify.aws/start/getting-started/installation/q/integration/react
- Sign up for AWS account
- 
## Initialize Amplified Project


### `install amplified cli`
```
npm i -g @aws-amplify/cli@4.24
```
or do
```
sudo npm install -g @aws-amplify/cli --unsafe-perm=true
```

### Error I encountered
I got a messege saying `amplify configure -bash: amplify: command not found`
I fixed the issue by changing environment installation path and node.js path.
```
export PATH="/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/Users/BeechuiKoo/.npm-global/bin"
```

### `configure aws/cli`
```
amplify configure
```

#### `set up the new user`
I used amplify-user for the new IAM user name / default for the profile name

Initialize and connect project in the cloud
```
amplify init
```

### `Adding Authentication with Cognito`
```
amplify add auth
```

## Create S3 Bucket to store images
```
amplify add storage
```
- I used "bookImages" for the name of my resource
- Use default bucket name (because it has to be unique)
- Who should have access: Choose "Auth and guest users"
    - Because you want the guest to view and read the books as well.
- For Authenticated Users: You want them to do all of "create/update", "read", "delete"
- For Guest Users: Only the "read"
- "No" Lambda Trigger
S3 Bucket is created successfully.

## Lambda functions to process book orders.
- AWS Lambda is a serverless compute service that runs your code in response to events and automatically manages the underlying compute resources for you. You can use AWS Lambda to extend other AWS services with custom logic, or create your own back-end services that operate at AWS scale, performance, and security.

```
amplify add function
```
- I used "processPayment" for the name/label
```
? Select which capability you want to add: Lambda function (serverless function)
? Provide an AWS Lambda function name: processPayment
? Choose the runtime that you want to use: NodeJS
? Choose the function template that you want to use: Hello World

? Do you want to configure advanced settings? Yes
? Do you want to access other resources in this project from your Lambda function? No
? Do you want to invoke this function on a recurring schedule? No
? Do you want to configure Lambda layers for this function? No
? Do you want to edit the local lambda function now? No
```

I want to add another lambda function
```
amplify add function
```
