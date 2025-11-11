# demo-ibm-spyre
This demo has been created for use with IBM Spyre Hardware on the Red Hat OpenShift platform.  The following prerequisites must be satisfied before executing this demo script.

## Prerequisites

- Red Hat OpenShift 4.11+ 
- Red Hat OpenShift AI 2.25+
- IBM AIU Spyre 1.0 (DD2)
- OpenShift Web Terminal (installed via Red Hat OpenShift Operators menu)

### Install the [OpenShift Web Terminal](https://docs.openshift.com/container-platform/4.12/web_console/web_terminal/installing-web-terminal.html)

### Rationale

- Provide a consistent terminal experience for those using Microsoft OS or MacOS
- Minimize context switching

### Takeaways

- Many times we are shoulder surfing during deployments and this minimizes issues with different OSs (bash, zsh, etc.)
- You can do the rest of this deployment in the terminal with your new user


> [!IMPORTANT]  
> following icon should appear in the top right of the OpenShift web console after you have installed the operator. Clicking this icon launches the web terminal.

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

Uninstall Demo

```sh
oc delete -k demo/spyre
```

## Additional Info

- https://github.com/vllm-project/vllm-spyre
