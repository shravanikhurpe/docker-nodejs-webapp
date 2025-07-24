// install nodejs
https://nodejs.org/en

// open powershell as a admin
winget install git -y 


powershell -c "irm https://community.chocolatey.org/install.ps1|iex"
choco install nodejs-lts --version="22"
node -v
npm -v 

git --version

git clone https://github.com/atulkamble/azure-nodejs-webapp-pipeline.git
cd azure-nodejs-webapp-pipeline
npm install express
node index.js

http://localhost:3000
