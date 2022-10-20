com.datadoghq.ad.logs: '[{"source": "agent", "service": "agent"}]'

The attribute that defines which integration is sending the logs. Datadog identifies the log source for the container and automatically uses corresponding integrations, if available. This **Autodiscovery** feature speeds up the setup process for log collection and processing. To learn more, view the [Docker Log Collection](https://docs.datadoghq.com/agent/docker/log/?tab=dockercompose#activate-log-integrations) documentation. If the logs do not come from an existing integration, then this field may include a custom source name