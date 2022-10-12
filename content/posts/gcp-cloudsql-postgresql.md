---
title: "Gcp Cloudsql Postgresql"
date: 2022-10-12T14:52:53-07:00
draft: false
---

# Google GCP CloudSQL PostgreSQL Administration  


I like to configure most of my infrastructure in Hashicorp terraform. The terraform was not developer friendly in my experience because it had a lot of prerequsites on defining the server config, instead of picking a class that just seems right. Building custom things, allows for varience. Thus I built and am administring the CloudSQL artifacts through the desktop cloudsql interface. So far so good.


# Constraints when using CloudSQL Postgres


## Importing Data

Data additions from a pg_dump archive file to a pg_restore requires the administrator to filter out any extentions that your source database created. Personally I find that because Google installs extentions by defaults Google need you to disable the extentions defined from a source database. That's fine but not an experince a developer would look to and require an error instead an ignore of the dataset to be copied.


## Forign Data Wrappers

The FDW does not work for CloudSQL outside of a private and or local network. For instance, let's say you have a public cloudsql server, in the same account on a public address you cannot connect to that other cloudsql instance, YET, the server can resolve DNS, and can connect to its public ip.

This is very hard to work with, when you require a data from one server to merge with data of another. AWS allows this.

## Disk size, server size, re-size

This is an awesome feature of GCP. You can increase the disk size of the instance without having to reset connections or interrupt processing of the running server.


## Conclusions 

Over all its overly opininated complext proxy connection system is a bit much. I just want to connect to my database from outside of my network until I can pull the endpoints behind the firewall. I do not want to create a sidecar to connect to my database. Server configuration is awesome though, and finally the incompatibilities around some features is rather annoying.



