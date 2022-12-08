version: '3'

services:

agent:

image: "datadog/agent:7.31.1"

environment:

- DD_API_KEY

- DD_APM_ENABLED=true

- DD_LOGS_ENABLED=true

- DD_LOGS_CONFIG_CONTAINER_COLLECT_ALL=true

- DD_PROCESS_AGENT_ENABLED=true

- DD_DOCKER_LABELS_AS_TAGS={"my.custom.label.team":"team"}

- DD_TAGS='env:intro-to-logs'

- DD_HOSTNAME=intro-logs-host

ports:

- "8126:8126"

volumes:

- /var/run/docker.sock:/var/run/docker.sock:ro

- /proc/:/host/proc/:ro

- /sys/fs/cgroup/:/host/sys/fs/cgroup:ro

labels:

com.datadoghq.ad.logs: '[{"source": "agent", "service": "agent"}]'

discounts:

environment:

- FLASK_APP=discounts.py

- FLASK_DEBUG=1

- POSTGRES_PASSWORD

- POSTGRES_USER

- POSTGRES_HOST=db

- DD_ENV=intro-to-logs

- DD_SERVICE=discounts-service

- DD_VERSION=1.1

- DD_AGENT_HOST=agent

- DD_LOGS_INJECTION=true

- DD_TRACE_SAMPLE_RATE=1.0

- DD_PROFILING_ENABLED=true

image: "ddtraining/discounts:2.1.2"

command:

[

sh,

-c,

"ddtrace-run flask run --port=5001 --host=0.0.0.0"

]

ports:

- "5001:5001"

volumes:

- "/ecommworkshop/discounts-service-fixed:/app"

depends_on:

- agent

- db

labels:

com.datadoghq.tags.env: "intro-to-logs"

com.datadoghq.tags.service: "discounts-service"

com.datadoghq.tags.version: "1.1"

my.custom.label.team: "discounts"

frontend:

environment:

- DD_AGENT_HOST=agent

- DD_TRACE_SAMPLE_RATE=1.0

- DD_ENV=intro-to-logs

- DD_SERVICE=store-frontend

- DD_VERSION=1.1

- DB_USERNAME

- DB_PASSWORD

- DD_CLIENT_TOKEN

- DD_APPLICATION_ID

image: "ddtraining/storefront:2.1.2"

command: sh docker-entrypoint.sh

ports:

- "3000:3000"

volumes:

- "/ecommworkshop/store-frontend-instrumented-fixed:/spree"