---
title: Install CP4A Operator
weight: 310
---
- 
# make sure there is a space after the - so that the TOC is generated
{:toc}

Starting with version 19.0.3, the Cloud Pak for Automation components install is supported by an OCP opreator.
The install steps for the operator are the following.

### Create your CP4A project
Your CP4A project will contain all the components that are deployed through the operator.
In the rest of this documentation, we use `cp4a` as the name of our OCP project.

- Login to your cluster:
```
oc login -u <admin> -p <password>
```

- Create the project and add privileges to it. 
```
oc new-project cp4a
oc adm policy add-scc-to-user privileged -z default
```

### Prepare the PV and PVC

- On the NFS server, under the root of an exported directory (look at the `/etc/export` file to view the exported directories), create a folder for the JDBC drivers and copy these drivers into it:
```
mkdir /storage/persistentvolumes/operator/jdbc/db2
cp /opt/ibm/db2/V11.1/java/db2jcc4.jar /nfs/persistentvolumes/operator/jdbc/db2/
cp /opt/ibm/db2/V11.1/java/db2jcc_license_cu.jar /nfs/persistentvolumes/operator/jdbc/db2/
```

- Copy this [`operator-shared-pv.yaml`]({{ site.github.url }}/assets/automation/operator/operator-shared-pv.yaml) template file to your working directory and update it as needed. In particular, update the `nfs:path` and `nfs:server` properties to fit your NFS setup.

- Deploy the PV:
```
$ oc apply -f operator-shared-pv.yaml
```

- Copy this [`operator-shared-pvc.yaml`]({{ site.github.url }}/assets/automation/operator/operator-shared-pvc.yaml) template file to your working directory and update it as needed. In particular, update the `metadata:namespace` property.

- Deploy the PVC:
```
$ oc apply -f operator-shared-pvc.yaml
```

### Deploy the operator

- In your working directory, download the necessary scripts and Kubernetes descriptors:
```
$ git clone https://github.com/icp4a/cert-kubernetes.git
```

- Change directory to `./cert-kubernetes` and run the `deployOperator.sh` script:
```
cd cert-kubernetes/
./scripts/deployOperator.sh -i $(oc registry info)/cp4a-operator/icp4a-operator:19.0.3
```

- Verify that the operator is running:
```
oc get pods
NAME                                 READY     STATUS    RESTARTS   AGE
ibm-cp4a-operator-7db5cfbb64-mgb2c   2/2       Running   0          5h
```
