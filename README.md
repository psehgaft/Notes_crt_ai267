# Notes_crt_ai267

Study notes for Red Hat OpenShift AI (course AI267): how to configure and
manage Red Hat OpenShift AI (RHOAI) — data science projects, workbenches,
model servers, and machine learning models on OpenShift.

## Contents

- `notes-ai267.md` — the study notes.
- `README.md` — this file.
- `LICENSE` — MIT license.

## Topics covered

- **Data science projects** — creating a project namespace, labelling it for
  the OpenShift AI dashboard (`opendatahub.io/dashboard: 'true'`) and for
  model serving (`modelmesh-enabled: 'true'`).
- **Users, groups, and permissions** — adding users to groups such as
  `rhods-admins` with `oc adm groups add-users`, and defining groups in YAML.
- **Data science workbenches** — working with workbench images, adding
  key/value configuration, and connecting a workbench to data stored in S3
  using environment variables (`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`,
  `AWS_DEFAULT_REGION`, `AWS_S3_ENDPOINT`, `AWS_S3_BUCKET`).
- **Custom workbench images** — building images from a `Containerfile` with
  `podman build` and pushing them to a registry.
- **Model and notebook sizes** — editing `OdhDashboardConfig` to define
  model server sizes and notebook sizes (Small, Medium, Micro).
- **Collaborative notebooks** — using Git to share Jupyter notebooks.
- **Saving and loading models** — persisting a scikit-learn model with
  `joblib.dump` and restoring it with `joblib.load`.

## Usage

These are reference notes, not an installer. Read `notes-ai267.md` top to
bottom, and adapt the commands to your own cluster. The examples assume:

- An OpenShift cluster with Red Hat OpenShift AI installed.
- The `oc` CLI, authenticated against that cluster.
- `podman` for building and pushing container images.

Example — create a data science project:

```sh
oc create namespace ai-project
oc label namespace ai-project opendatahub.io/dashboard='true' modelmesh-enabled='true'
```

## License

MIT — see `LICENSE`.
