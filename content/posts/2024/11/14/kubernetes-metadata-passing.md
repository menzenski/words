---
title: "YAML Test"
date: "2024-11-14T12:51:07-06:00"
disableShare: true
---

This is YAML:

```yaml
apiVersion: external-secrets.io/v1alpha1
kind: ExternalSecret
metadata:
  name: "hello-world"
  labels:
    acme.org/owned-by: "q-team"
  annotations:
    acme.org/sha: 1234
spec:
  secretStoreRef:
    name: secret-store-name
    kind: SecretStore  # or ClusterSecretStore
  refreshInterval: "1h"
  target:
    name: my-secret

    # Enum with values: 'Owner', 'Merge', or 'None'
    # Default value of 'Owner'
    # Owner creates the secret and sets .metadata.ownerReferences of the resource
    # Merge does not create the secret, but merges in the data fields to the secret
    # None does not create a secret (future use with injector)
    creationPolicy: 'Merge'

    # Specify a blueprint for the resulting Kind=Secret
    template:
      type: kubernetes.io/dockerconfigjson # or TLS...

      metadata:
        annotations: {}
        labels: {}

      # Use inline templates to construct your desired config file that contains your secret
      data:
        config.yml: |
          endpoints:
          - https://{{ .data.user }}:{{ .data.password }}@api.exmaple.com

      # Uses an existing template from configmap
      # Secret is fetched, merged and templated within the referenced configMap data
      # It does not update the configmap, it creates a secret with: data["alertmanager.yml"] = ...result...
      templateFrom:
      - configMap:
          name: alertmanager
          items:
          - key: alertmanager.yaml

  # Data defines the connection between the Kubernetes Secret keys and the Provider data
  data:
    - secretKey: secret-key-to-be-managed
      remoteRef:
        key: provider-key
        version: provider-key-version
        property: provider-key-property

  # Used to fetch all properties from the Provider key
  # If multiple dataFrom are specified, secrets are merged in the specified order
  dataFrom:
  - key: provider-key
    version: provider-key-version
    property: provider-key-property

status:
  # refreshTime is the time and date the external secret was fetched and
  # the target secret updated
  refreshTime: "2019-08-12T12:33:02Z"
  # Standard condition schema
  conditions:
  # ExternalSecret ready condition indicates the secret is ready for use.
  # This is defined as:
  # - The target secret exists
  # - The target secret has been refreshed within the last refreshInterval
  # - The target secret content is up-to-date based on any target templates
  - type: Ready
    status: "True" # False if last refresh was not successful
    reason: "SecretSynced"
    message: "Secret was synced"
    lastTransitionTime: "2019-08-12T12:33:02Z"

```
