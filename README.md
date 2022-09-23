# cloudfront-cookiemodel
cloudfront-lambdA edge and s3

use case:
user want to run the new UI but he not sure how the people respond to it ,so we created an lambda edghe function which takes cookies  and allow the user to  to new or old page UI without using fifferen domain or even redirect. 

old application is in S3 bucket,so does the new s3 bucket
Both the S# buckets are static webhosting is enabled so both are public,we have cloudfront distribution which will do all the cahing,
once the user is requesting the website it will redirected to old one
then once it got viewed to old one user has an option to move to the new one or the old one
In cludfront we're using lanbda edge fuction
there are four lambdaedge function ,lets take it two sides one is user's side and another is origin side.two lamda function is trigeerd at certain point of time, now frst lamda function iscalled when viewer request before it cached before cloudfront
once it goes to backen(s3) then the return responce is triggered by second viewer side lambda.
similarly we have the origin side we have two lamda function that get triggered when the request is cahched at cloudfront level .
this origin req lambda func decides which origin the req is forwarded to.
the next lambda is triggered when the responce is passed from new or origin basically

let me give a overview how the user selects the origin .
once the old application is served in that they have a button ,in the buttonwe can set a cookie in this case we set a cookie called version .
if user want to see new applicaation we set the version to new at origin req lambda we'll chcek what is the cookie is (is it new or old)according to that the we will move to that s3 bucket.
