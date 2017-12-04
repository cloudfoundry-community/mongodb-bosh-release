# MongoDB BOSH release

This MongoDB deployment is intended for use with BOSH deployment  

## Prerequisites

1. A deployment of [BOSH](https://github.com/cloudfoundry/bosh)
2. Tested environment

Name | Version
------------ | -------------
MongoDB | 3
BOSH | 261.1
bosh-vsphere-cpi-release | v38
bosh-vsphere-esxi-ubuntu-trusty-go_agent | 3363.1

## Features 

1. Bosh deployed

2. Single multi-tenant back-end cluster

3. service instances represent logical databases on the shared server  

4. Authentication supported 

## How to use

1. You can follow the [bosh document](http://bosh.io/docs) to install BOSH firstly

2. Create manifest file. You can find example mongodb3-release.manifest under examples folder as reference

3. Create and upload release

    `bosh create-release --force`
    
    `bosh upload-release`

4. Deploy 

    `bosh deployment your_deployment_manifest_file`
    
    `bosh -n deploy`
    
    `bosh run-errand replset --keep-alive`

5. When it completes ,you can check mongodb node using

    `bosh vms`
6. After some months usage, we suggest not to use haproxy to connect the mongo broker and app in the cloudfoudry.
   
   Because the connection between app and mongo will not reconnect if some replset is down, 
   
   But can use the haproxy for date export/import.
   
   
## Road-map
 
1. Dashboard 

## Contribution 

Welcome to contribute through pull request  
