---

# Microservice on K8s

tiny microservices playground running on Kubernetes ☸️

built while learning k8s, breaking shiii, fixing it.

### architecture (or whatever)

```
                    ┌──────────────┐
                    │  Voting App  │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │    Redis     │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │    Worker    │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │  PostgreSQL  │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │  Result App  │
                    └──────────────┘
```

### the k8s bits i’m currently pretending to understand

- **Pods** — where the containers actually live
- **Deployments** — the thing that keeps the pods from dying on me
- **Services** — networking magic so they can yell at each other
- **Redis** — temporary vote/message dump
- **Worker** — the guy that actually processes the votes
- **PostgreSQL** — where the votes go to sleep forever

### quick start

```bash
kubectl apply -f .
```

check if anything is alive:

```bash
kubectl get pods
kubectl get deployments
kubectl get services
```

restart everything because why not:

```bash
kubectl rollout restart deployment
```

scale postgres down (for science):

```bash
kubectl scale deployment db-postgres --replicas=0
```

bring it back from the dead:

```bash
kubectl scale deployment db-postgres --replicas=1
```

### the point

not trying to build the next Netflix.  
just learning how a bunch of services:

```
talk → fail → restart → recover → talk again
```

inside kubernetes.

**stack:** Docker · Kubernetes · Redis · PostgreSQL  

🎧 lab soundtrack: Manu Chao
