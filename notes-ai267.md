# Configure and manage RHOAI
## Work with data science projects

```ia-namespace.yaml
kind: Project                             
apiVersion: project.openshift.io/v1
metadata:
  name: ai-project                    
  labels:
    kubernetes.io/metadata.name: ai-project
    modelmesh-enabled: 'true'
    opendatahub.io/dashboard: 'true'     
    ...output omitted...
```

## Create a Project

```sh
oc create namespace ai-project
oc label namespace ai-project opendatahub.io/dashboard='true' modelmesh-enabled='true'
```

## Asign user permisions users and grups

```sh
oc adm groups add-users rhods-admins ai-user1 ai-user2
```

Groups

```sh
apiVersion: user.openshift.io/v1
kind: Group
metadata:
  name: ai-group
users:
  - ai-user1
```

- Add Key / Value config map to workbench

- Modify workbench images

```sh
s3://[buket_name]/file
```

## Create a workbech with data base access

```jupiter
import os

key_id = os.getenv("AWS_ACCESS_KEY_ID")
secret_key = os.getenv("AWS_SECRET_ACCESS_KEY")
region = os.getenv("AWS_DEFAULT_REGION")
endpoint = os.getenv("AWS_S3_ENDPOINT") # important to use https://[AWS_S3_ENDPOINT]
bucket_name = os.getenv("AWS_S3_BUCKET")
```

# Use data science workbenches

```sh
cat Containerfile

FROM registry....
COPY requirements.txt ./

```

```sh
 echo "phyton==0.12.2" >> requirements.txt

podman build . -t registry.ocp4.example.com:8443/[image]:1.0
```

## Edit ODH modelserverSizes

```OdhDashboardConfig.yaml
apiVersion: opendatahub.io/v1alpha
kind: OdhDashboardConfig
metadata:
  annotations:
    internal.config.kubernetes.io/previousKinds: OdhDashboardConfig
    internal.config.kubernetes.io/previousNames: odh-dashboard-config
    internal.config.kubernetes.io/previousNamespaces: default
  name: odh-dashboard-config 
  namespace: redhat-ods-applications 
  labels:
    app.kubernetes.io/part-of: rhods-dashboard
    app.opendatahub.io/rhods-dashboard: 'true'
spec:
...output omitted...
  modelServerSizes: 
    - name: Small
    ...
    - name: Medium
    ...
  notebookSizes:
    - name: Small
    ...
    - name: Medium
    ...
    - name: Micro
```

## Deploy an image

```sh
podman build . -t [image-name]:[tag]
podman push [registry]/[image-name]:[tag]
```

# Use Git to manage Jupyter notebooks collaboratively

- Use git clone for clone repo
- Push commit

# Work with machine learning models
- Save and recharge kernel is important thing after external changes

# Save and load models

```sh
import joblib
from sklearn.linear_model import LogisticRegression
model = LogisticRegression()
filename = my_model.joblib
```

## Save

```output
joblib.dump(model, filename)
```
## load

```sh
model = joblib.load(filename)
```
