### How to create a GCP storage bucket using cli.

In this tutorial I will explain to you how to manage and perform basic tasks in GCP cloud storage using command line. Cloud storage is worldwide and highly durable object base storage. You can access data instantly any time from storage class. To manage cloud storage using command line we need to configure `gsutils`

### Install `gsutil` on Ubuntu 18.04.
Using `gsutil` you can manage gcp cloud storage. You can perform tasks related to cloud storage using `gsutil` command. So let's install `gsutil` on ubuntu.

There are different methods to install `gsutil` But here I will install it using python package Index pip.

* Install required packages.
```
sudo apt-get install gcc python-dev python-setuptools libffi-dev
```

* Install pip installer.
```
sudo apt-get install python-pip
```

* Install `gsutil` using pip.
```
sudo pip install gsutil
```

Now, You are ready to use `gsutil`.


## OR Gcloud-sdk.
You can also install gcloud sdk to access and manage all the gcp cloud resources.
```
curl https://sdk.cloud.google.com | bash
```
```
exec -l $SHELL
```
```
gcloud init
```



### Create gcloud storage bucket.
Using the `gsutil mb`  command you can create a new bucket in gcp cloud storage. Let's start our first cloud storage bucket `vishalvyas-bucket`.

```
gsutil mb gs://vishalvyas-bucket/
```
`Creating gs://vishalvyas-bucket/...`

Our fist bucket is created. Let's check the bucket.

`Note` : You can specify `-l` for the location of your bucket. like `ASIA-EAST1

### List the bucket.
You can list the buckets ugin `ls` command.

```
gsutil ls
```
`gs://vishalvyas-bucket/`
You can see that bucket in GCP storage.

### Upload content to the GCP bucket.
Now, Let' play with the bucket and upload some content on it. I have 2 files called `1.txt` & `2.txt` in my pc. I want to upload that files in the bucket which we have created. We will use `cp` to upload objects from local to storage bucket. Let's upload it.

```
gsutil cp 1.txt 2.txt gs://vishalvyas-bucket

```
```
Copying file://1.txt [Content-Type=text/plain]...
Copying file://2.txt [Content-Type=text/plain]...                               
/ [2 files][    0.0 B/    0.0 B]                                                
Operation completed over 2 objects.                                              
```
You can see that 2 objects has been uploded. let's view it.

```
gsutil ls gs://vishalvyas-bucket/
gs://vishalvyas-bucket/1.txt
gs://vishalvyas-bucket/2.txt

```
You can see that object which we have uploaded.

### Download object from GCP bucket to pc.
Let's download the data from the GCP bucket. I want to download `2.txt file from bucket`.

```
gsutil cp gs://vishalvyas-bucket/2.txt .
Copying gs://vishalvyas-bucket/2.txt...
/ [1 files][    0.0 B/    0.0 B]                                                
Operation completed over 1 objects.  
```
You can find the download file in your working directory.

### Make bucket objects publically accessible.

You can make your object publically accessible using `acl ch` command. So that all the users can use that object.

```
gsutil acl ch -u AllUsers:R gs://vishalvyas-bucket/2.txt
Updated ACL on gs://vishalvyas-bucket/2.txt
```
Now all the users can access 2.txt file. To remove the permission, Use the below command.

```
gsutil acl ch -d AllUsers gs://vishalvyas-bucket/2.txt
Updated ACL on gs://vishalvyas-bucket/2.txt
```
Now, Only you can access that file.


### Give bucket access to particular user
You can share your bucket object with users you want. You want to just give their email ID and permission to the bucket.

```
gsutil iam ch user:shiva@companyid.com:objectCreator,objectViewer gs://vishalvyas-bucket
```

Now, User with the above email id will access and view your bucket object with given permission.

You can remove the permission using the command below.

```
gsutil iam ch -d user:shiva@companyid.com:objectCreator,objectViewer gs://my-awesome-bucket

```
Now, We have removed the user access to this bucket.


### Delete objects
Let's delete the bucket now. You can delete the bucket using `rm -r` command.
```
❯ gsutil rm -r gs://vishalvyas-bucket

```

```
Removing gs://vishalvyas-bucket/1.txt#1581571948280886...
Removing gs://vishalvyas-bucket/2.txt#1581571949191136...                       
/ [2 objects]                                                                   
Operation completed over 2 objects.                                              
Removing gs://vishalvyas-bucket/...
```
Bucket and its contents are deleted now, As You can see that everything is deleted now.

Hope this tutorial will help you to learn and manage GCP cloud storage.
