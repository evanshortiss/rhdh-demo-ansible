# RHDH Demo Environment

## Setup

Requires and OpenShift 4.16 cluster.

```bash
oc login --token $TOKEN --server=https://api.yourcluster.com:6443

ansible-playbook playbooks/ocp4_workload_platform_engineering_workshop.yml \
-e rhdh_gh_pat=ghp_replacewithtoken
```

## Usage

After setup, you can login to Red Hat Developer Hub as `user1` using the
password `password`.