---
title: What Kubernetes is and what it is not
date: '2019-06-05T23:28:12.676Z'
excerpt: ''
thumb_img_path: null
comments_count: 0
positive_reactions_count: 6
tags:
  - kubernetes
  - discuss
  - docker
canonical_url: 'https://dev.to/bzinoun/what-kubernetes-is-and-what-it-is-not-1kkd'
template: post
---
Two questions were very important to me when my interest was on Kubernetes : 

- What is Kubernetes ?
- What Kubernetes is not  ?

By answering to these two questions, i was sure to start from the right point and also know the responsibility of Kubernetes . 

So let's make a pragmatic responses about that . 

### 💡What is Kubernetes ?

Kubernetes is a platform that wrap a huge number of services and capabilities ; these latter is growing day after day . 
From a top level we can say , the core functionalities of Kubernetes  is it's ability to manage containers across linux based infrastructure . 
But Kubernetes brings also a lot of feature such as : 

- Managing Secrets
- Checking applications Health
- Scaling application : Scale app and down
- Auto Scaling
- Instance replication
- Discovering resource
- Naming Resource
- Monitoring resource
- Managing and mounting Storage system
- Providing security component : Authorization , Authentication

In one sentence the responsibility of K8S is 

> Platform for managing containerized workloads and services, that facilitates both declarative configuration and automation.

### ⛔️ What Kubenetes is not ?

The Common mistake is to say  *Kubernetes is a Paas* ! 

**Kubernetes is not a platform as a service** (Paas) , in my opinion  Rancher is a Paas for Kubernetes  , It provide a high level configuration for kubernetes and provide some default configuration for Kubernetes to . 

In fact  Kubernetes doesn't dictate many aspects of our system and leaves them up to us to manage them . 

In facts Kubernetes does  : 

- not require a specific application type or a dependency framework
- not require a specific programming language
- not provide any database
- not provide any message queues
- allow us to choose our logging system
- allow us to choose our monitoring  & alerting system
- ..etc

### That's all Folks

---

In the next post we will discuss the relation between K8S and containers . We will find response for questions such as : 

- What's benefits of containers
- How we need to manage our containers
- ...etc

*[This post is also available on DEV.](https://dev.to/bzinoun/what-kubernetes-is-and-what-it-is-not-1kkd)*


<script>
const parent = document.getElementsByTagName('head')[0];
const script = document.createElement('script');
script.type = 'text/javascript';
script.src = 'https://cdnjs.cloudflare.com/ajax/libs/iframe-resizer/4.1.1/iframeResizer.min.js';
script.charset = 'utf-8';
script.onload = function() {
    window.iFrameResize({}, '.liquidTag');
};
parent.appendChild(script);
</script>    
