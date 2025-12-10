# Demo Spyre AI accelerator with x86 on OpenShift (Technology Preview only)

This demo has been created for use by IBM Research clients who are using the Spyre AI accelerator with x86 on the Red Hat OpenShift platform as a Technology Preview feature.

The following automates the configuration of prerequisites and is specifically intended for
users with `cluster-admin` or an operations team.

[User Model Serving](#user-model-serving) listed below should be able to be run by a user with the `self-provisioner` role or access to create projects / namespaces.

> [!NOTE]
> Verify your permissions if you experience errors.

## Prerequisites

- Red Hat OpenShift 4.11+
- Red Hat OpenShift AI 2.25+
- IBM AIU Spyre 1.0 (DD2)
- OpenShift Web Terminal (see below for installation instructions)
- OpenShift `cluster-admin` permissions

## Install the [OpenShift Web Terminal](https://docs.openshift.com/container-platform/4.12/web_console/web_terminal/installing-web-terminal.html)

> [!NOTE]
> The following icon should appear in the top right of the OpenShift web console after you have installed the operator. Clicking this icon launches the web terminal.

![Web Terminal](docs/images/web-terminal.png "Web Terminal")

NOTE: Reload the page in your browser if you do not see the icon after installing the operator.

## Demo - Manual Installation

If you do not wish to use the `Quick Start`, you may manually perform the demo installation steps using the following <a href="/docs/01-install-spyre-rhoai-from-ocp.md">instructions</a>.

## Demo - Quick Start

> [!IMPORTANT]
> Run the following commands from the enhanced web terminal.
>
> `cluster-admin` is required

```sh
# apply the enhanced (OpenShift) web terminal
oc apply -k https://github.com/redhat-na-ssa/demo-ibm-spyre/demo/web-terminal

# delete old web terminal
$(wtoctl | grep 'oc delete')
```

### Setup Operators + Cluster Configurations

> [!IMPORTANT]
> `cluster-admin` is required

These instructions will setup the operators

```sh
apply_firmly gitops/operators
```

### Setup Model Serving Demo

```sh
apply_firmly gitops/instance/model-serving
```

### User Model Serving

The following will setup model serving for a user with `self-provisioner`

```sh
# create a new project / namespace
oc new-project [username]

# create model inference
oc apply -k gitops/instance/model-serving/base
```

### Setup Workbench Example

```sh
apply_firmly gitops/instance/rhoai-notebooks
```

Once the model is deployed, you can use a curl command to send a request to the model and perform inferencing.  For example:

```sh
curl -k "http://granite-3-1-8b-instruct-predictor.demo-ibm-spyre.svc.cluster.local/v1/completions" \
-H "Content-Type: application/json" \
-d '{"model":"granite-3-1-8b-instruct","prompt":"Write a short poem.","temperature":0,"max_tokens":128}'
```

### Uninstall Demo

```sh
oc delete -k gitops/instance/model-serving
```

## Additional Info

- https://github.com/vllm-project/vllm-spyre
