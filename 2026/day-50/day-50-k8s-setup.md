Day 50 – Kubernetes Architecture and Cluster Setup
--------------------------------------------------
#90DaysOfDevOps | DevOps Ka Josh | TrainWithShubham
--------------------------------------------------

My Journey on Day 50
Today I set up my first ever Kubernetes cluster, broke it on purpose, fixed it, and explored what's actually running inside. Here's everything I did, everything I learned, and every mistake I made along the way.

Task 1: The Kubernetes Story (From My Memory)

Before touching the terminal, i wrote down what i remembered.

Why was Kubernetes created? What problem does it solve that Docker alone cannot?
Kubernetes is a container orchestration tool which was created to orchestrate the container. It solved the problem of autoscaling and autoscaling of kubernetes pods if due to any reason pods got crashed.

Who created Kubernetes and what was it inspired by?
Kubernetes was originally developed by engineers at Google and was primarily inspired by Google's internal cluster management system called Borg.


What does the name "Kubernetes" mean?
The name Kubernetes originates from Greek, meaning helmsman or pilot. K8s as an abbreviation results from counting the eight letters between the "K" and the "s". Google open sourced the Kubernetes project in 2014.

Task 2: Kubernetes Architecture
Kubernetes has two sides — the Control Plane (the brain) and the Worker Nodes (the muscle). The Control Plane decides what should happen. The Worker Nodes make it happen.


Control Plane (Master Node):
API Server — the front door to the cluster, every command goes through it
etcd — the database that stores all cluster state
Scheduler — decides which node a new pod should run on
Controller Manager — watches the cluster and makes sure the desired state matches reality

Worker Node:
kubelet — the agent on each node that talks to the API server and manages pods
kube-proxy — handles networking rules so pods can communicate
Container Runtime — the engine that actually runs containers (containerd, CRI-O)
          
