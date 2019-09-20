# Monitor gcp stackdriver in grafana.

We want to monitor GCP resources graph and logs in grafana. For that we will have to configure stackdriver in grafana. We will add Stackdriver as a datasource in Grafana and then you can see stackdriver dashboard metrics in Grafana dashboard. Grafana is widely used to monitor resoucers and visulize monitoring graphs. So here are some steps to configure GCP stackdriver in grafana. I assumed that you have installed grafana.


### 1. Create GCP service account JSON file.

To authenticate with stackdriver from grafana, we need to create a service account for the GCP project which want to monitor.

* Login into the GCP consol.

* Go to the `IAM & ADMIN` and click on `Service Accounts`.

* Click on `CREATE SERVICE ACCOUNT`

* Type service account `name` and click on create button.

Now it will ask for service account permission, As we just want to monitoring permission so we will select `Monitoring Viewer` role and continue.

* Click on `create key` and select key type JSON.

* Key will be downloaded in your machine.


Now we have GCP project key with monitoring permission, So we will import this key in grafana to allow stackdriver monitoring.


### 2. Configure Grafana.
Now we have GCP project key with monitoring permission, So we will import this key in grafana to allow stackdriver monitoring.

* Login to the Grafana.

* Go to `setting` configuration and click on `datasource`.

* Select Datasource `Stackdricer`.

* Under Authentication, click on `Upload Service Account File`. 

* Upload the keys and click on `Save & Test`.

Now you can see that `Successfully queried the Stackdriver API.` in green background. So till now we have added datasource in grafana.


### 3. Create dashboard and visulize metrics.

* Go to the `manage`.

* Click on `New Dashboard` and `Add Query`.

* Select `Stackdriver` as a query.

You can see that all the GCP services are in the list in service, which you can monitor.

Here i want to monitor my GCP `compute vm`. So i will select `Compute` from the service and use `CPU Utilization` metric.


You can see that graph generated for the compute engine we selected. you can also filter it by `instance name`, `PROJECT`, `zone` etc. Also you can add multiple instance in the graph by adding new query. 

Hope you like this article. give your suggestion and feedback also.
 
