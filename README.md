# k8s-metadata-service
Kubernetes repo holding metadata-service manifests

What it is: an EC2-compatible metadata service. The successor to Kant.

App repo: https://github.com/metal-toolbox/hollow-metadataservice

# DB Usage

By default, this helm chart *disables* the database backend of metadata-service, disabling the caching of metadata, and causing all requests to be sent to the upstream source of truth. If you wish to enable the database, be sure to change the `METADATASERVICE_CRDB_ENABLED` flag from "false" to "true". In doing so, be aware that metadata-service is susceptible to race conditions, unless a mechanism is used to ensure updates are sent to it and processed in-order (e.g, via the use of a message queue).
