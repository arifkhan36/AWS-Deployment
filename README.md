# AWS SITE DEPLOYMENT
1.  Click on the services
2.  Click on the Storage S3
3.  Create a bucket
4. Name a bucket and hit next skipping all the steps until you create the bucket
5. Click on the bucket and then choose properties tab
6. Choose Static website hosting and choose "Use this bucket to host a website"
# FrontEnd/REACT SIDE
1. Create a .env file in the root folder and add this local variable
```
REACT_APP_HOST=http://localhost:8080
```
Note: YOU GOTTA HAVE REACT_APP

2.  Remove proxy containng http://localhost:8080 from package.json
3.  Remove registerServiceWorker(); from index.js file
4.  Fixing axios in the app.js
```
await axios.get(process.env.REACT_APP_HOST +'/users')
```
