## About

This project is a web tool that allows users to run Natural Languange Processing (NLP) on articles or blogs found on other websites. NLP is the ability of an application to undestand the human language, written or oral. 
This project is used with external API called MeaningCloud. 

## How it works

![ezgif com-video-to-gif-12](https://user-images.githubusercontent.com/71527795/100224442-bce66800-2f14-11eb-9b41-c5506d4f492c.gif)

### Getting Started 

Fork the projet Github repo and install the following loaders and plugins: 
```
cd<project directory>
npm install
npm i -D @babel/core @babel/preset-env babel-loader
npm i -D style-loader node-sass css-loader sass-loader
npm i -D clean-webpack-plugin
npm i -D html-webpack-plugin
npm i -D mini-css-extract-plugin
npm i -D optimize-css-assets-webpack-plugin terser-webpack-plugin
```
### Set up the API 
I am using MeaningCloud Sentiment Analysis API for this project. 
Sign up for an API key. Once creating an account with MeaningCloud, licence key will be given to start using the API.

1.To configure environment variables (variables thats only belong to local system) we need to install dotenv package: 
```
npm install dotenev
```
2.Create a new ```env``` file in the root of the project and fill the file with the API key: 
```
API_ID=************************(your API key instead of *)
```
3.To refer ennvironmental variable I am using process.enc. in front of the variable with API credentials. 

4.Create .gitignore file in the project root and add .env file. This will allow us not to push our environmental variables to Github. API key is personal!

### Using the API
The app is listening port 8083. I've set 2 variables **baseURL** and **API_KEY** in source/server/index.js file and have created a post request passing on /test with the required outcome I wanted to get from this request: _polarity, confidence, irony, subjectivity._ 
In a client side of code in client/js/formHandler.js I created a function that checks what text is put in to the form fiels and have requested the form field to show the data requested from my **POST** request: _irony, confidence, polarity, subjectivity._
I also made an asynchronous fetch function **postData**.

### Testing the code with Jest
1.Install Jest ```npm install --save-dev jest```
2.You can find test files in the folder called --test-- in the root of the project. There is located 3 files: 
- **formHandler.spec.js** file is testing if handleSubmit function exists and it is testing the postData. 
- **server.spec.js** file is testing post enpoint of the project
- **urlChecker.spec.js** is trying to see if test returns true on valid url, in other words if URL exists the test passes and if false input is added to the field (text or unknown URL) it returns false. 
3.To test the project run npm run test

### Service Workers
Service workers are installed in order for the project to be available when server is stopped. 

### Information about the files
In the file root you can fing package.json (dependencies), Procfile(used for testing and pointing to the root of the project where it needs to run), webpack.dev.js & webpack.prod.js (plugins and module.exports), .babelrc (presets and plugins), source folder with client and server side files and finally the test file. 

### Bugs 
There might be a bug related to Jest. When trying to run the test it's passed however doesn't exit one second after the test run had completed. It was reported in the forum that it might be a bug, also no other suggestions worked for me to fix this issue. 

