# openshift-secondary-scheduler-operator

The Secondary Scheduler Operator provides the ability to use a customized scheduler image that was developed using the scheduler plugin framework as a secondary scheduler in OpenShift.

## Secondary Scheduler Configuration

Once the Secondary Scheduler Operator is installed, you can configure the plugins to run for your secondary scheduler.

The configuration of the secondary scheduler is defined through a config map that wraps the KubeSchedulerConfiguration YAML file in "config.yaml".

## Additional Parameters

Additionally, the following parameters can be configured:

* `schedulerConfig` - Set the config map configuration for the secondary scheduler.
* `schedulerImage` - Set the default operand image for the secondary scheduler.
