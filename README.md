# Running your own Backstage App on Kubernetes

This repository is a example of a Backstage App for running on Kubernetes cluster. Tested on my local K3S cluster.

## Prerequisites
- NodeJS
- Yarn
- A running Kubernetes cluster
- Docker CLI

## How to use
1. Clone the repository
1. Run `yarn install`, `yarn tsc` and `yarn build:all`
1. Build the docker image by `docker build . -f packages/backend/Dockerfile`
1. Replace `[Your GitHub PAT]` with your own GitHub Personal Access Token in `kubernetes/backstage-secret.yaml`
1. Replace `[Your Backstage Image]` with the Backstage image URL in `kubernetes/backstage.yaml`
1. Create namespace by `kubectl create ns backstage`
1. Run `kubectl apply -f kubernetes/.`
1. Run `kubectl port-forward --namespace=backstage svc/backstage 7007:7007`
1. Access your Backstage App through `http://localhost:7007`
