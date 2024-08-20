# Kubernetes PostgreSQL Operator

## Overview

This project provides Kubernetes configuration files to set up and manage a PostgreSQL database using the Crunchy PostgreSQL Operator. It includes the necessary YAML files to deploy the operator, configure the PostgreSQL cluster, and expose the service.

## Components

1. **`service.yaml`**:
    * Defines a Kubernetes Service of type `NodePort` to expose the PostgreSQL Operator.
    * Configures the service to listen on port 8443 and map it to node port 32443.
    * Ensures connectivity to the PostgreSQL Operator by selecting pods with specific labels.

2. **`postgresql.yaml`**:
    * Sets up the PostgreSQL environment within the Kubernetes cluster.
    * Creates a namespace `pgo` for PostgreSQL resources.
    * Configures an OperatorGroup and Subscription for the PostgreSQL Operator, pulling from the `operatorhubio-catalog` source.

3. **`pgcluster.yaml`**:
    * Configures a PostgreSQL cluster using the Crunchy PostgreSQL Operator.
    * Defines storage requirements for primary, replica, and Backrest volumes.
    * Sets up database specifications, image configurations, and user credentials.
    * Includes settings for cluster management, such as resource limits, pod anti-affinity, and tolerations.

## Setup Instructions

1. **Deploy the PostgreSQL Operator**:
    * Apply the `postgresql.yaml` file to create the necessary namespace, OperatorGroup, and Subscription.

2. **Expose the Operator Service**:
    * Apply the `service.yaml` file to create a NodePort service for accessing the PostgreSQL Operator.

3. **Create and Configure PostgreSQL Cluster**:
    * Apply the `pgcluster.yaml` file to set up the PostgreSQL cluster with the specified configurations.

## Usage

* Ensure you have `kubectl` installed and configured to interact with your Kubernetes cluster.
* Apply each YAML file using `kubectl apply -f <filename>.yaml`.
* Monitor the status of the deployed resources using `kubectl get all -n pgo`.

## Additional Information

* For more details on the Crunchy PostgreSQL Operator, visit the [Crunchy Data documentation](https://www.crunchydata.com/).
* Adjust configurations in the YAML files as needed to fit your specific environment and requirements.
