# AWS-Unity-CloudFormation

### What is this?

This is an aws cloud formation template along with build scripts to create a back-end for a unity game.

### What does it create?

+ S3 bucket where you can put downloadable content for your game.
+ Roles and policies for the identity pools below.
+ Identity pool with logins for google play, facebook, twitter, google+ (twitter and google+ are pretty untested).
    * Unauth users have access to public folder in bucket and public lambdas.
    * Auth users have access to public/private folder in bucket and public/private lambdas.
+ Identity pool with full unauth access for developer to upload content from the unity editor to the bucket
    * This is for editor use only. Don't include this identity pool ID in your unity build.

### How to use it:

Before using this, you need to go through the awful process of setting up the google play API, facebook API, and twitter API.
If you don't want to use them, at this point in time you'll have to delete them manually from the template and the deploy script.

1. In the config file, set all the variables. For template bucket, create a bucket in advance to store your cloud formation templates and put the name there. (Or use any bucket you already have). If you don't want to include any lambdas, delete that manually.

2. If you don't have google set as an open id connect provider: `createOpenIdConnectProvider.txt`

3. `./deployStackOnly.txt`
