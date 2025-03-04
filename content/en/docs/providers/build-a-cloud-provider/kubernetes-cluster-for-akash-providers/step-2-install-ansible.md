---
title: "STEP 2 - Install Ansible"
key: "step-2-install-ansible"
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
STEP 2 - Install Ansible
========================

When you launch Kubespray it will use an Ansible playbook to deploy a Kubernetes cluster. In this step we will install Ansible.

Depending on your operating system it may be necessary to install OS patches, pip3, and virtualenv. Example steps for a Ubuntu OS are detailed below.

    apt-get update ; apt-get install -y python3-pip virtualenv
    

Within the kubespray directory use the following commands for the purpose of:

*   Opening a Python virtual environment for the Ansible install
*   Installing Ansible and other necessary packages specified in the requirements.txt file
*   Please remember to `cd kubepsray; source venv/bin/activate` each time you want to use `ansible-playbook` command as detailed below.

    cd ~/kubespray
    
    virtualenv --python=python3 venv
    
    source venv/bin/activate
    
    pip3 install -r requirements.txt