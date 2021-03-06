---
title: Install Developer Tools (Mac OSx)
weight: 400
---

{:toc}

## Prerequisites

Before beginning these steps you should have:
1. A github account (or Github Enterprise)
1. A Dockerhub account (needed to install docker)
1. A Red Hat entitled customer account (to install oc)
1. An IDE (Eclipse or VS Code to use with Codewind)
1. A login for your Openshift Container cluster


## Installing Client tools from web pages on the cluster

A landing page is created during the install of Cloud Pak for Applications.
The landing page is available in the top menu bar and is named Cloud Pak Console.
The landing page is also found in the Administrator Console under Networking::Routes and is named icpa-landing in the kabanero namespace.
The Cloud Pak Console pages provide the most current installation information about the client tools.
This document will also provide links to these tools on the web.

When the OpenShift cluster is created, a reference page is generated for the OpenShift command line tools. There are several useful links on this page. Get this URL from your administrator.
TODO: update images
{%
 include figure.html
 src="/assets/img/cp4a/cmdline_tools.png"
 alt="Command Line Tools"
%}

**Note:** You will need to authenticate (login) to your cluster.

The Cloud Pak Console provides additional information on installing additional development tools.  In the Console page, select the Setup dev tools button and follow instructions in the pop-up.
TODO: UPDATE IMAGES
{%
 include figure.html
 src="/assets/img/cp4a/kabanero.png"
 alt="Setup Dev Tools"
%}

**Note:** You will need to authenticate (login) to your cluster.

## Command line tools

#### git
On mac `git` is installed by default. You may use `which git` to validate that it is installed.

### OpenShift command line interface (oc)

Recommend to download from OpenShift cluster using instructions with Setup Dev Tools.
Alternatively, more information can be found here:
https://docs.openshift.com/container-platform/4.2/cli_reference/openshift_cli/getting-started-cli.html For complete installation instructions there is a video you should watch.
**Note:** You will need to login using your RedHat customer account.

oc is also available from https://mirror.openshift.com/pub/openshift-v4/clients/oc/latest/macosx/

### docker
Install docker from here:
https://docs.docker.com/install/
**Note:** You will need to authenticate (login) to docker.

### appsody

Multiple platform installation instructions https://appsody.dev/docs/getting-started/installation

## IDE: Codewind with Eclipse or VS Code

* Eclipse installation https://www.eclipse.org/codewind/mdteclipsegettingstarted.html
* VS Code installation: https://www.eclipse.org/codewind/mdt-vsc-getting-started.html
