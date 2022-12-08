Applications are groups of services.  USM and Service Catalog support this model.  Take a piece of metadata and link them all together.

USM
- Map Dependiences Automatically
- Establish Consist SLO's across monitors and teams
- Centralize Monitoring and Knowledge - Service Catalog solves this

We can get all this without changing any code.
- Not APM Lite
- Not Cheaper APM
- USM and APM can and should coexist

Help customer answer
- Is there an issue?
- Where is the issue?
- Why did the issue happen?, how do we make sure it doesn't happen again.  USM helps with the first two items.

Cross sell with other App-Layer SKUs.  It sits below synthetics and RUM.

To sell to the User, focus on identifying blind spots in services, they are tasked with rolling out SLOs, but they have a dependency on the apps team.  USM is championed by the Infra team.

To sell to the Buyer, focus on blind spots between teams, it is challenging to standardize metrics and SLOs across different teams.  USM provides tooling to standardize metrics and SLOs.

To sell to the Decision Maker, how can I accelerate time to market.  

Green Flags - Primarily use k8s on Linux 4.14+ and less that 25% APM penetration.  Red flags - Primarily Windows, Large Legacy environment, Broad APM coverage, pain point is mosty monitoring.

Supported use cases - HTTP and HTTPS (OpenSSL & GnuTLS), contrainerized services on Linux, and Windows IIS-based services (support is early).  Coming non-containerized Linux services, Istio mTLS support (boringssl), Java HTTPS, gRPC, Kafka, MySQL/Postgres.

Unsupported - Serverless architecture (Lambda, ECS Fargate, Azure App Services), broader Windows support (non-IIS, encrypted Windows traffic).

Troubleshooting - enable system probe debug log & collect a flare, are they using TLS traffic.  Debugging doc is part of the slide show.