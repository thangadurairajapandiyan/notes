# Jenkins build triggers

### Reference
https://blog.knoldus.com/jenkins-build-triggers/

### Github webhook
Github will notify the jenkins when some commits are pushed to remote repository.

Github webhook will work only when jenkins address is reachable from github

### Polling scm
Jenkins will check the Github periodically for any new commits has pushed. Uses cron to define how frequent it has to check

Polling is helpful, when jenkins is not reachable from github.

### Build periodically
Uses the cron to trigger the job periodically

### Trigger builds remotely
Trigger the jenkins job using rest api.

eg: curl JENKINS_URL/job/vignesh/job/freestyle-helloworld-build-deploy/build?token=TOKEN_NAME

TOKEN_NAME - which we have configured in jenkins job trigger.
```
curl http://localhost:8080/job/vignesh/job/freestyle-helloworld-build-deploy/build?token=12345
```
