title : Free Services for Mark
author : Mark Nielsen
copyright : August 2024
---


Free Cloud services for Mark
==============================

_**by Mark Nielsen
Original Copyright August 2024**_


These are Cloud services I am interested in and how to use them. Its really easy, get an account and use their dashboards. I focus on free always accounts.
Most free accounts have limitations. GCP and AWS have many more free always services and some trial services, but I just list the ones I am mainly interested in. 

1. [GCP](#g)
2. [AWS](#a)
3. [MongoDB](#m)
4. [CockroachDB](#c)
5. [New Relic](#n)
6. [Snowflake](#s)


* * *
<a name=g></a>GCP
-----

* [GCP](https://cloud.google.com/free)
   * Storage
       * Cloud storage ; 5GB and traffic -- enough for testing
       * database
          * Big Query, pub/sub, firestore
       * Programming -- secret manager


* * *
<a name=a></a>AWS
-----

* [AWS](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=tier%23always-free&awsf.Free%20Tier%20Categories=*all)
   * Limits by usage == TODO update this list  
       * database : Dynamo, SimpleDB
       * Monitoring -- GLue, Key management
       * Programming -- lambda
       * Infrastructure -- CLoudFront, Route
   * ALmost free
          * S3 -- first 12 months free, if less than 10 GB of diskspace, very cheap
	  

   * No longer
      * EC2 -- now if you make a 3 year contract, you pay per month for your ip address. GCP per month at the lowest costs is about $4 per month.
      I am paying over $10 a month with a 3 year contract. Its better to just stop using AWS and use GCP. You recover your costs quickly if you switch from AWS to GCP when you
      just want to test.
   * There are other free services, but I am not interested in them right now.
   * For GCP with no committment, I got a a vm for about $3.26 a month. $40  year. With AWS I pay now $11 a month for some reason, probably because of ip address and with a 3 year
   payment. I will update the true cost of the GCP server later --- estimates are not very good usually. AWS seems to have reduced its committed servers, but they have in small print
   costs doesn't include usage of services. That's were I get charged $11 a month. We will see if GCP does something similar. 


* * *
<a name=m></a>MongoDB
-----
MongoDB is not always free on the cloud.

But you can get free monitoring : https://www.mongodb.com/docs/v4.0/administration/free-monitoring/

* * *
<a name=c></a>CockroachDB
-----

Free : https://www.cockroachlabs.com/pricing/

* Make sure you use GCP --- I believe AWS charges for traffic. Be careful what region you chose in GCP. Check the charts. 


* * *
<a name=n></a>New Relic
-----

* https://newrelic.com/pricing/free-tier

Free monitoring. Be careful how often you alert and load data. You have 100 GB free a month.Reduce the checking of your servers.

Edit monitors:
* https://docs.newrelic.com/docs/synthetics/synthetic-monitoring/using-monitors/add-edit-monitors/
* In accounts: go to Synthetic Monitoring
    * edit /etc/newrelic-infra.yml
    * Use the template at https://github.com/newrelic/infrastructure-agent/blob/master/assets/examples/infrastructure/newrelic-infra-template.yml.example
    * wget -O /etc/newrelic-infra.yml https://raw.githubusercontent.com/newrelic/infrastructure-agent/master/assets/examples/infrastructure/newrelic-infra-template.yml.example
* Commands
    * Start/Stop : https://docs.newrelic.com/docs/infrastructure/install-infrastructure-agent/manage-your-agent/start-stop-restart-infrastructure-agent/
    * sudo systemctl restart newrelic-infra

NOTE: I could not change the metric settings in the yml file because it would not accept the license key. Then when I removed the yml file, it still would not restart.
I think the license key is stored temporarily somewhere and when you make your yml file is deletes the previous config and then won't work again. You have to remove
and install again. And you cannot get support for free accounts. I think the license key is intentionally less than 40 characters so you can't reduce the monitor rate by making your
own yml file. Be careful not to go over the 100 GB a month. 

For paid accounts to change the rate of monitoring....

```
 # Put in your license key first. 

 ### add this to config file for once an hour -- for testng purposes. 

metrics_network_sample_rate: 3600
metrics_process_sample_rate: 3600
metrics_storage_sample_rate: 3600
metrics_system_sample_rate: 3600

### restart
sudo systemctl restart newrelic-infra
sudo systemctl status newrelic-infra

```
* * *
<a name=s></a>Snowflake
-----
You can sign up with the same email every 30 days. It means, you can make it always free, but you have to sign up again. 

https://signup.snowflake.com/

I recommend using the $2 option per month and limiting the amount of data and traffic after the free month

