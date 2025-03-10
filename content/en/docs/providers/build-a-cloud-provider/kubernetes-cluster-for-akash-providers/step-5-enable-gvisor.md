---
title: "STEP 5 - Additional Verifications/Config"
key: "step-5-additional-verificationsconfig"
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
        parent: "kubernetes-cluster-for-akash-providers"

---
STEP 5 - Enable gVisor
======================

In this section we will enable gVisor which provides basic container security.

Containerd Edit/Verification
----------------------------

*   Change into the directory of the config file

    cd ~/kubespray/inventory/akash/group_vars/k8s_cluster
    

*   Using VI or nano edit the k8s-cluster.yml file:

    vi k8s-cluster.yml
    

*   Add/update the container\_manager key if necessary to containerd

    container_manager: containerd
    

**gVisor Issue - No system-cgroup v2 Support**
----------------------------------------------

If you are using a newer systemd version, your container will get stuck in ContainerCreating state on your provider with gVisor enabled. Please reference [this document](../../../other-resources/archived-resources/build-a-cloud-provider/gvisor-issue-no-system-cgroup-v2-support.md) for details regarding this issue and the recommended workaround.