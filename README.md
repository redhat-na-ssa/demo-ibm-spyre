# demo-ibm-spyre

Use IBM Spyre Hardware on OCP

## Setup OCP Web Terminal

### Install the [OpenShift Web Terminal](https://docs.openshift.com/container-platform/4.12/web_console/web_terminal/installing-web-terminal.html)

The following icon should appear in the top right of the OpenShift web console after you have installed the operator. Clicking this icon launches the web terminal.

![Web Terminal](docs/images/web-terminal.png "Web Terminal")

### Quick Start
NOTE: Reload the page in your browser if you do not see the icon after installing the operator.

> [!IMPORTANT]  
> Run the following commands from the enhanced web terminal

```sh
# apply the enhanced web terminal
oc apply -k https://github.com/redhat-na-ssa/demo-ibm-spyre/demo/web-terminal

# delete old web terminal
$(wtoctl | grep 'oc delete')
```

Setup Operators + Configurations

```sh
oc apply -k gitops
```

Setup Model Serving Demo

```sh
oc apply -k demo/spyre
```
