# demo-ibm-spyre
This demo has been created for use with IBM Spyre Hardware on the Red Hat OpenShift platform.  The following prerequisites must be satisfied before executing this demo script.

## Prerequisites

- Red Hat OpenShift 4.11+ 
- Red Hat OpenShift AI 2.25+
- IBM AIU Spyre 1.0 (DD2)
- OpenShift Web Terminal (see below for installation instructions)


## Install the [OpenShift Web Terminal](https://docs.openshift.com/container-platform/4.12/web_console/web_terminal/installing-web-terminal.html)

> [!IMPORTANT]  
> following icon should appear in the top right of the OpenShift web console after you have installed the operator. Clicking this icon launches the web terminal.

![Web Terminal](docs/images/web-terminal.png "Web Terminal")

NOTE: Reload the page in your browser if you do not see the icon after installing the operator.

## Demo - Mannual Installation
If you do not wish to use the 'Quick Start', you may mannually perform the demo installation steps using the following <a href="/docs/01-install-spyre-rhoai-from-ocp.md">instructions</a>. 

## Demo - Quick Start

> [!IMPORTANT]  
> Run the following commands from the enhanced web terminal

```sh
# apply the enhanced (OpenShift) web terminal
oc apply -k https://github.com/redhat-na-ssa/demo-ibm-spyre/demo/web-terminal

# delete old web terminal
$(wtoctl | grep 'oc delete')
```

Setup Operators + Configurations

```sh
apply_firmly gitops
```

Setup Model Serving Demo

```sh
apply_firmly demo/spyre
```

Uninstall Demo

```sh
oc delete -k demo/spyre
```

## Additional Info

- https://github.com/vllm-project/vllm-spyre
