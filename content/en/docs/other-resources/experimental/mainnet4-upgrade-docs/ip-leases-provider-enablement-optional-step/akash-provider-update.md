---
title: "Akash Provider Update"
key: "akash-provider-update"
description: ""
lead: ""
date: Thu Dec 29 2022 03:03:46 GMT-0800 (Pacific Standard Time)
lastmod: Thu Dec 29 2022 03:03:46 GMT-0800 (Pacific Standard Time)
draft: false
images: []
weight: 1
toc: true

menu:
    docs:
        parent: "ip-leases-provider-enablement-(optional-step)"

---
Akash Provider Update
=====================

Update your pre-existing Akash provider to support IP Leases.

### Attribute Update

Update your provider to advertise the following attribute. This attribute can be used (by users deploying on Akash) to select providers supporting the IP Lease.

    - key: ip-lease
      value: true
    

### Command Template

    helm upgrade akash-provider akash/provider -n akash-services -f provider.yaml --set ipoperator=true
    

### Expected/Example Output

    root@node1:~/provider# helm upgrade akash-provider akash/provider -n akash-services -f provider.yaml --set ipoperator=true
    Release "akash-provider" has been upgraded. Happy Helming!
    NAME: akash-provider
    LAST DEPLOYED: Wed Aug 10 20:35:10 2022
    NAMESPACE: akash-services
    STATUS: deployed
    REVISION: 2
    TEST SUITE: None