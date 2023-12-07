# Dockerfile_for_node
A basic node project with commands which you can deploy using Dockerfile.!

Commands below , using you can create node application and dockerize easily..


  Install npm (i am using redhat)

  sudo yum install npm

  after installing npm check , it is installed or not using below command

  npm --version
  node -v

  when it works successfully and show you version related to this , you can start creating your node project

  run command
     ---->      npm init
     it will provide you (package.json) which is most importnat file of node
     ----->     npm install express --save
     To Run this command you will get node_module and package-lock.json files which are install all dependencies for running your node project

  now create your index.js file with below code
  --------> vi index.js

  //Load express module with `require` directive
var express = require('express')
var app = express()

//Define request response in root URL (/)
app.get('/', function (req, res) {
  res.send('Hello Ashwani Sir!')
})

//Launch listening server on port 8081
app.listen(8081, function () {
  console.log('app listening on port 8081!')
})

-------> node index.js   (Run this command and browse your application on chrome or any other browser you have will show you Hello Ashwani Sir!)


<--------------Dockerize your application------------->

vi Dockerfile

FROM node:12-alpine3.14
WORKDIR /app
COPY package.json /app
RUN npm install --only=production && npm cache clean --force
COPY . /app
CMD node index.js
EXPOSE 8081

<-------------------------------------------------------->

above dockerfile you can check my repository also

next step is creating an image for node project

Run command

---------> docker run -t youdockerhubusername/choice-image-name:choice-tag          (in my case i used ashwanidevops321/my-node-app:latest)

docker login 
your username & password

docker push yourdockerhubusername/choice-image-name:choice-tag                   (in my case it was docker push ashwanidevops321/my-node-app:latest)

after completing all this you can create container for running application using command

docker run -td --name your-container-name -p 8081:8081 your-image-id


thank you for reading this
Ashwani Gupta

