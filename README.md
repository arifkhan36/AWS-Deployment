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
3.  Remove ``` registerServiceWorker();``` from index.js file
4.  Fixing axios in the app.js
```
await axios.get(process.env.REACT_APP_HOST +'/users')
```
NOTE: do this for all the requests involving the link
# BACK to AMAZON site
5. Config AWS CLI.
6. Go to AWS console at the website and choose the IAM console
7. Hit next permissions and Create a user group
8. Name the group: 'SecaAdmins'
9. Once it's createad click on the SecaAdmin
10. Choose users
11. Choose new user
12. Add a user name and choose Progammatic access hit next
13. you should have the access key ID and Secret key access
14. Save the key id and secret key access
15. Close it
# COMMAND LINE
16. At the command line type ```aws configure```
17. Add your keys and region:
    ```
    AWS Access Key ID [None]: **********************
    AWS Secret Access Key [None]: **********************
    Default region name [None]: us-east-1
    Default output format [None]: json
    ```
18. npm install 
19. npm run build 
20. Sanity check, type on command line: aws s3 ls It should return a list of buckets available 
21. Sync the folder with the bucket: aws s3 sync build/ s3://bucket-seca-md
