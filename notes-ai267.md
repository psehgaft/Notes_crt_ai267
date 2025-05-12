# Configure and manage RHOAI

# Work with data science projects

- Create a Project
- Asign user permisions users and grups
- Add Key / Value config map to workbench

- Modify workbench images

## Create a workbech with data base access

´´´śh
import os

key_id = os.getenv("AWS_ACCESS_KEY_ID")
secret_key = os.getenv("AWS_SECRET_ACCESS_KEY")
region = os.getenv("AWS_DEFAULT_REGION")
endpoint = os.getenv("AWS_S3_ENDPOINT")
bucket_name = os.getenv("AWS_S3_BUCKET")
´´´

# Use data science workbenches

## Edit ODH modelserverSizes

´´´OdhDashboardConfig.yaml
apiVersion: opendatahub.io/v1alpha
kind: OdhDashboardConfig
metadata:
  annotations:
    internal.config.kubernetes.io/previousKinds: OdhDashboardConfig
    internal.config.kubernetes.io/previousNames: odh-dashboard-config
    internal.config.kubernetes.io/previousNamespaces: default
  name: odh-dashboard-config 1
  namespace: redhat-ods-applications 2
  labels:
    app.kubernetes.io/part-of: rhods-dashboard
    app.opendatahub.io/rhods-dashboard: 'true'
spec:
...output omitted...
  modelServerSizes: 3
    - name: Small
    ...
    - name: Medium
    ...
    - name: Micro
´´´

## Deploy an image

´´´
podman build . -t [image-name]:[tag]
podman push [registry]/[image-name]:[tag]
´´´
# Use Git to manage Jupyter notebooks collaboratively

# Work with machine learning models

# Save and load models
