# demo-ibm-spyre

Use IBM Spyre Hardware on OCP

## Setup OCP Web Terminal

### Install the [OpenShift Web Terminal](https://docs.openshift.com/container-platform/4.12/web_console/web_terminal/installing-web-terminal.html)

The following icon should appear in the top right of the OpenShift web console after you have installed the operator. Clicking this icon launches the web terminal.

![Web Terminal](docs/images/web-terminal.png "Web Terminal")

NOTE: Reload the page in your browser if you do not see the icon after installing the operator.

### Quick Start

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
apply_firmly gitops
```

Setup Model Serving Demo

```sh
apply_firmly demo/spyre
```

## Additional Info

- https://github.com/vllm-project/vllm-spyre
