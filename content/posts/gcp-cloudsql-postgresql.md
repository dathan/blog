---
title: "Gcp Cloudsql Postgresql"
date: 2022-10-12T14:52:53-07:00
draft: false
---
## Google GCP CloudSQL PostgreSQL Administration
I like to configure most of my infrastructure in Hashicorp terraform. The terraform was not developer friendly in my experience because it had a lot of prerequisites for defining the server config, instead of picking a class that just seems right. Building custom things allows for variance. Thus I built and am administering the CloudSQL artifacts through the desktop cloud SQL interface. So far so good.

## Constraints when using CloudSQL Postgres
### Importing Data
Data additions from a pg_dump archive file to a pg_restore require the administrator to filter out any extensions that your source database created. I find that because Google installs extensions by default Google needs you to disable the extensions defined from a source database. That’s fine but not an experience a developer would look to and require an error instead an ignore of the dataset to be copied.
### Foreign Data Wrappers
The FDW does not work for CloudSQL outside of a private and or local network. For instance, let’s say you have a public cloud SQL server, but in the same account on a public address you cannot connect to that other cloud SQL instance, YET, the server can resolve DNS, and can connect to its public IP.
This is very hard to work with when you require data from one server to merge with data from another. AWS allows this.
### Disk size, server size, re-size
This is an awesome feature of GCP. You can increase the disk size of the instance without having to reset connections or interrupt the processing of the running server.
### Conclusions
Overall its overly opinionated complete proxy connection system is a bit much. I just want to connect to my database from outside of my network until I can pull the endpoints behind the firewall. I do not want to create a sidecar to connect to my database. Server configuration is awesome though, and finally, the incompatibilities around some features are rather annoying.
