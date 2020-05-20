HI 

In this repo, i will configure a jenkins job to triger on every commmit.
for that i will use github-hook. this github-hook push code to jenkins to trigger a new build after every commit.
to create a webhoook, go to repo settings, and webhooks. Create new webhook. and provide jenkins url

Payload URL --> http://<JENKINS-URL:PORT>/github-webhook/

Content type --> Application/JSON

Which events would you like to trigger this webhook? --> Just the push event.

Click Add Webhook.

Go to manage jenkins, install github integration plugin...

Now go to jenkkins job and in post build acttions,  select  Set github commit status (Universal)
Add github repo as source in job and in build triger option select --> GitHub hook trigger for GITScm polling
Save the job connfiguration.


Thus when any developer commit code it will automatically triger a build.
##########################

##########################

Adding automatic job status update in github commit, so after commit jenkins build will triggered but developer will have no 
information regarding build fail or success. They need to check jenkins everytime. Now addding feature that will update build 
result ONLY success or fail status to commit.

Developer neeed to check jenkins only of job fail.


I github account got to profile --> settings --> developer settings -> Personal Access Token
Click on GENERATE new token.
  Select scope of new token...
    (There is a big list of token scope option available)
  Click on Generate token.
  Copy this toekn.....    >>------------------------------------->>
                                                                   \/
                                                                   |
Go to manage jenkins , configure System....                        |
In GIT SERVER section,                                             |
add new git server,                                                |
give name of this connection,                                      |
api URL let it be default,                                         |
In credentials add jenkins                                         |
  Domain --> Global Credentials                                    |
  Kind --> secret text                                             |
  Scope --> choose scope...(Global default)                        |
  Secret --> Here goes the secret token copied from github <<---<< \/
  ID --> any relevent ID fotr this token
  Add description
  Click --> ADD
In credentisla type select name of the created token and test connection. 
Git hub account verify the token.


Make changes in repository. 
new changes triger a new build  and build status will be updated in commit section..

Thank You.
