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


┌──────────────────────────────────────────────────────────────┐
│                       CONTROL PLANE                          │
│                                                              │
│   ┌──────────────────────────────────────────────────────┐   │
│   │                    API Server                        │   │
│   │      Every single command goes through this          │   │
│   └──────────────────────────────────────────────────────┘   │
│          │               │                  │                │
│   ┌──────▼─────┐  ┌──────▼─────┐  ┌─────────▼──────────┐    │
│   │    etcd    │  │ Scheduler  │  │ Controller Manager  │    │
│   │ cluster DB │  │ node picker│  │  reconciles state   │    │
│   └────────────┘  └────────────┘  └────────────────────┘    │
└──────────────────────────────────────────────────────────────┘
                           │
           ┌───────────────▼──────────────────┐
           │           WORKER NODE            │
           │                                  │
           │  ┌────────────────────────────┐  │
           │  │          kubelet           │  │
           │  │  node agent — manages pods │  │
           │  └────────────────────────────┘  │
           │  ┌─────────────┐ ┌────────────┐  │
           │  │ kube-proxy  │ │ Container  │  │
           │  │ networking  │ │  Runtime   │  │
           │  └─────────────┘ └────────────┘  │
           │  ┌──────────┐  ┌──────────┐      │
           │  │  Pod A   │  │  Pod B   │      │
           │  └──────────┘  └──────────┘      │
           └──────────────────────────────────┘
