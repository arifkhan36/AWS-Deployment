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
20. Sanity check, type on command line: ```aws s3 ls``` It should return a list of buckets available 
21. Sync the folder with the bucket: ```aws s3 sync build/ s3://bucket-seca-md```
NOTE IF YOU GOT ACCESS ERROR:
Go to your bucket and choose overview and select upload: Choose upload and upload all the content from inside of your build directory.

Once is done, choose properties and click on Static website hosting and you might see the link there, click on it and you will see your website hosting.

# Updating and configure your server for scalability
1. Go to EC2 and choose launch instance
2. Choose Ubuntu Server 16.04
3. Choosing the free tier for Microservices is not good... So choose T2 Large
4. Don't choose nothing on step 3
5. Step 4 choose 16 Gb
6. Step 5 add tags don't add one now
7. Step 6 Configuring SSH
 * Add a rule 'Custom TCP' 8080 (for our API gateway)
 * Add a rule 'Custom TCP' 8761 (for Eureka)
 * Add a rule 'Custom TCP' 5432 (for the database)
NOTE: Make sure every source field is set to: 0.0.0.0/0, ::/0

8. Review and launch
9. It's going to as for a key pair. Choose create a key pair and add key-pair and download it.
10. Launch and see.
11. At the bottom of the screen you will PUBLIC DNS (IPV4) copy that and:
