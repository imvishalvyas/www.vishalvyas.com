#FATAL: too large   

Today I have updated some node version in my gitlab ci pipeline, After upgrading the version I ran the pipeline and I got an error that ERROR: Uploading artifacts as "archive" to coordinator... too large archive.

```
node_modules/: found 57656 matching files and directories 
ERROR: Uploading artifacts as "archive" to coordinator... too large archive  id=31845 responseStatus=413 Payload Too Large status=413 token=YGCc9B7z
FATAL: too large                                   
Cleaning up file based variables
00:00
ERROR: Job failed: command terminated with exit code 1
```


I spent some time debugging this error and finally I fixed this error. Issue was related to the maximum artifact size limit. In my Gitlab maximum artifacts limit was set to 100MB which is the default artifact upload size limit. Here are the steps to resolve this error.

In your Gitlab, Go to Admin settings > Continuous Integration and Deployment > Maximum artifacts size (MB) and increase the value of the artifact size.

You can set this limit to a different level.

### 1. Instance level 
```
Go to Admin Area > Settings > CI/CD and change the value of maximum artifacts size.
```

### 2. Project level
```
Go to `Project's` Settings > CI/CD >  General Pipelines and change the value of maximum artifacts size.
```

### 3. Group level 
```
Go to the Group's Settings > CI/CD >  General Pipelines and change the value of maximum artifacts size.
```

And click on the save changes and re-run the pipeline. 
