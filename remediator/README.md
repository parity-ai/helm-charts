# `remediator`

These are the charts for installing the `remediator` service, which connects to our services and allows our agents to gather info from your cluster.

You must have `helm` installed and be able to connect to your cluster to complete these steps. You can check out [the documentation](https://helm.sh/docs/intro/install/) for instructions on installing `helm` if you haven't already.

## Installation Steps

1. Clone this repository locally.

1. Update the `parity.apikey` value in `values.yaml` with your API key. Visit [our website](https://auth.tryparity.com/org/api_keys) to generate an API key.

1. Update `parity.tag` with the latest version from https://hub.docker.com/repository/docker/parityai/remediator/tags. We recommend not using the tag `latest`.

1. (optional) Double check that the rest of the values in `values.yaml` are to your liking. We generated these using `helm create`, and left almost everything as default. Please ensure that `replicaCount` remains `1`.

1. Run the following command to create a `parity` namespace in your cluster

    ```
    kubectl create namespace parity
    ```

    If you already have a namespace `parity` in use, create a new namespace with a different name of your choise and update `parity.namespace` in `values.yaml`.

1. `cd` into this directory.

1. Replacing `<NAMESPACE>` with the namespace you created before, run the command

    ```
    helm install -n <NAMESPACE> parity-remediator .
    ```

    Now `remediator` is installed in your cluster!

    If you need to update `values.yaml` later, run

    ```
    helm upgrade -n <NAMESPACE> parity-remediator . --values values.yaml
    ```

    from this directory to apply the changes.