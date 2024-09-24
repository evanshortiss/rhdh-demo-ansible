# RHDH Demo Environment

Note that this environment is currently designed for use with the
[Red Hat Developer Hub Demo](https://github.com/rhdh-demo-gh/) environment on GitHub.

## Setup

### Prerequisites

#### OpenShift

Requires an OpenShift 4.16 cluster. It's possible to use a 
[Single Node OpenShift on AWS](https://developers.redhat.com/articles/2024/04/29/how-install-single-node-openshift-aws#installing_the_ocp_client_and_getting_the_installation_program)
with SSL certificates [configured using Certbot](https://gist.github.com/evanshortiss/c60e0cb394ffa8610ee76bd64e1c3d52).

#### Ansible

This repository has been tested with Ansible 2.17.4 on macOS, using
[`pipx`](https://github.com/pypa/pipx) to manage the Python environment for
Ansible and dependecnies.

```bash
brew install pipx
pipx ensurepath

# Install Ansible
pipx install --include-deps ansible

# Install dependencies required by the playbooks
pipx inject ansible kubernetes jmespath
```

## Setup & Usage

Login to your OpenShift instance using the `oc` CLI, prepare environment
variables, and run the installation playbook.

```bash
oc login --token $TOKEN --server=-server=https://api.yourcluster.com:6443

cp .env.example .env

ansible-playbook playbooks/ocp4_workload_platform_engineering_workshop.yml \
-e rhdh_gh_pat=$GH_PAT \
-e techdocs_bucketname=$TECHDOCS_BUCKETNAME \
-e techdocs_accesskeyid=$TECHDOCS_ACCESSKEYID \
-e techdocs_secretaccesskey=$TECHDOCS_SECRETACCESSKEY \
-e techdocs_region=$TECHDOCS_REGION
```

After the playbook has run, you can login to Red Hat Developer Hub as `johndoe`
using the password `password`.