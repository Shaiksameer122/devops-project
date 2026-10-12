# DevOps Project: Flask App with CI/CD, GitOps and Monitoring

## Flow
Code push -> GitHub Actions (test + build) -> Docker Hub -> Git (k8s manifests) -> Argo CD -> Kubernetes (kind) -> Prometheus + Grafana

## Tools
Python, Flask, Docker, GitHub Actions, Kubernetes (kind), Argo CD, Helm, Prometheus, Grafana

## What I built
- Dockerized Flask app with a /health endpoint
- CI pipeline: tests, then image build and push to Docker Hub tagged with the commit SHA
- Kubernetes Deployment (2 replicas, readiness probe) and Service
- Argo CD with auto-sync and self-heal (Git is the source of truth)
- Prometheus and Grafana installed with Helm

## Screenshots
![Pipeline](screenshots/actions.png)
![Argo CD](screenshots/argocd.png)
![Grafana](screenshots/grafana.png)

## Problems I solved
- InvalidImageName: fixed a wrong image tag
- ImagePullBackOff: restarted pods after slow image downloads
- Argo CD "repository not found": corrected the repo URL