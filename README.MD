# Service Mesh Demo

## The 3 pillars of LinkerD
### Reliability 
- Load balancing
- Retries
- Circuit Brakers
- etc.

### Visiibility
- Tap
- Metrics
- Topology

### Security
- mTLS

Taken from:
https://github.com/klingerf/grpc-linkerd-demo

## Linting Proto files


```sh
## Service Mesh Demo

# Setup kubernetes
kind create cluster --name c1
# Add to lens

# Linkerd checks if Kubernetes is OK
linkerd check --pre

# Install Linkerd on kubernetes
linkerd install | kubectl apply -f -

# ======== Reliability + Security (Service Mesh - Part 1) ========

# Apply the app yaml
cd linkerd-demo
k apply -f app.yml

# Check if linkerd is up and running
linkerd check --proxy

# Check stats for deployment
linkerd stat deploy
# gRPC is much more efficient

# Check stats for pods
linkerd stat pods
# Load balancing problem..

# Inject linkerd into the app
kubectl get deploy/gateway -oyaml | linkerd inject - | kubectl apply -f -

# Check pods
kubectl get pods
# New pod is coming up

# Check stats for pods - again (shorter time window)
linkerd stat pods -t 20s

# ======== Tap ========

# Tap into the traffic
linkerd tap deploy/grpc-backend

# ======== Dashboard ========
linkerd dashboard
# click on namespace
# Deploymens -> click (upstream/downstream deployments, live calls)
# Grafana dashboards
# Back, click on grafana next to grpc backend
# In grafana - choose a 15 min time windows, show TLS vs non-TLS


# ======== Other features ========
# Client policy (protobuf function calls)
# Service Profiles
linkerd profile --proto grpc-backend.proto grpc-backend | kubectl apply -f -
# Top
linkerd -n linkerd top deploy/linkerd-web


# ======== Observability (Observability - Part 2) ========
cd ../emojivoto
kubectl apply -f ./app.yml
# Go to: http://localhost:8080/

# Inject Linkerd into the App
kubectl get -n emojivoto deploy -o yaml \
  | linkerd inject - \
  | kubectl apply -f -



```
