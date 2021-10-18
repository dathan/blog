---
title: "Upgrading_operator_sdk_without_ever_using_it"
date: 2021-10-15T19:43:10-07:00
draft: true
---

Migrating Go projects to the new Kubebuilder aligned project layout
See the v0.19.0 project migration guide that walks through an example of how to migrate a Go based operator project from the old layout to the v0.19.0 layout. Migrating to v0.19.0 before v1.0.0 is practical if you plan to migrate your project between one minor version at a time.

If you wish to migrate directly from the old layout to the latest v1.0.0+ layout, see the latest migration guide.

See #3190 for more details.



https://v0-19-x.sdk.operatorframework.io/docs/golang/project_migration_guide/


--- 
The version I am upgrading from is operator-sdk 0.11 to 1.13.1

according to this url https://sdk.operatorframework.io/docs/upgrading-sdk-version/v1.0.0/

the instructions of 

`operator-sdk generate k8s` has been switched to => `Use make generate` -- this is an aha moment. The version change is so drastic I just need to start from the quickstart guide and port over the added logic from the repo.

---
