# Step by Step how to deploy an app using AWS Elastic BeanStalk and working node.js

## Step 1: Set Up Your AWS Account

-> Make sure you  have an AWS account. If not, sign up at aws.amazon.com.

-> IAM Users and Roles: Create IAM users and roles with appropriate permissions to use Elastic Beanstalk.

## Step 2: Install the AWS CLI and EB CLI

-> AWS CLI: Install the AWS CLI. (For MacOS it is easier to install via homebrew).

-> EB CLI: Install the EB CLI. (For MacOS it is easier to install via homebrew)

## Step 3: Make sure you have node.js server installed on your machine

To install node.js follow the sreps belllow: 

#### install nvm (Node Version Manager)

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# download and install Node.js (you may need to restart the terminal)

nvm install 20

#### verify the right Node.js version is in the environment

node -v # should print `v20.14.0`

#### verify the right NPM version is in the environment

npm -v # should print `10.7.0`

## Step 4: Create an Elastic Beanstalk Application

#### phase 1:Create the required working directory for nodejs:

-> mkdir eb-nodejs

-> cd eb-nodejs

#### Phase 2: Creating an Application to deploy

-> nano server.js

Add the following content:

const http = require('node:http');

const hostname = '127.0.0.1';
const port = 8080;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello T2 Geniuses!\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
  
The application will open a listener on port 8080, and Elastic Beanstalk will forward requests to the application on port 8080 by default for Node.js.

#### Phase 3: Test your application locally

-> node server.js

You will see this: Server running at http://127.0.0.1:8080/

#### Phase 4: Deploy your Node.js application with the EB CLI

-> eb init

The command will initialize your EB CLI repository with the "eb init" command. Follow the prompts.

#### Phase 5: Create the environment for your App

-> eb create nodejs-env

#### Phase 6: Open your website App

-> eb open

 The above command will open the Application on a Web browser. 
 
--> curl http://nodejs-env.eba-xqpgtp47.us-east-1.elasticbeanstalk.com/

 You get this from the Environments Dashboard under "Domain."
 
#### Phase 7: Clean Up

-> eb terminate

#### Initialize the Application:

-> eb init

## Step 5: Create and Deploy an Environment

#### Create an Environment:

-> eb create

#### Deploy Your Application:

-> eb deploy

#### Managing Environments

##### List Environments:

-> eb list

##### Open Environments:
-> eb open

##### Terminate Environments:
-> eb terminate
