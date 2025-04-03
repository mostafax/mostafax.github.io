---
title: "Building a Scalable MLOps Foundation in the Cloud – Part 2: Medium Teams Setup"
date: 2025-04-03
layout: post
categories: mlops medium-teams
---

## Intro

In [Part 1](https://mostafax.github.io/mlops-small-teams/), we looked at how small ML teams (usually 1 to 3 people) can set up a lightweight and practical MLOps foundation in the cloud. But as your team grows and more models make it to production, things start to get messy—fast.

When you hit 4 to 10 people, you're no longer a tiny team. You’ve got more experiments running, more models to maintain, and more opinions in every discussion. That simple setup that once worked great? It starts showing cracks.

This post is about scaling that original setup without losing your mind. We’ll go over the new challenges medium teams face, and how to upgrade your MLOps stack just enough to stay fast, collaborative, and in control.

---

## 1. The Growing Pains of Medium-Sized ML Teams

When you’re a team of 2 or 3, it’s easy to sync up. You might even remember which model lives where just from memory (guilty 🙋). But once your team grows, you start noticing things like:

- Experiments being duplicated because no one knew someone else already tried it  
- Pipeline steps failing because someone renamed a column  
- Models going to production without proper checks  
- Metrics being collected in five different ways, none of them consistent  

This is where you need more structure—but without making everything feel like a giant enterprise bureaucracy.

---

## 2. What Changes (and What Doesn’t)

The good news? You don’t have to throw out everything from Part 1. Most of it still applies.

But you **do** need to level things up:

| For small teams                  | Now, as you scale                           |
|----------------------------------|----------------------------------------------|
| JupyterHub or SageMaker Studio  | Add shared environments with user permissions |
| Git + DVC                       | Enforce branching strategies and versioning rules |
| Manual pipeline triggers        | CI/CD integrated with orchestrators          |
| Basic model registry            | Approval workflows + tagging in MLflow       |
| Single notebook                 | Modular, reusable codebase                   |
| Single environment              | Separate dev, staging, prod environments     |

---

## 3. Better Collaboration, Less Chaos

With more people, you need clearer ways to work together. Here’s what that might look like:

### Shared Features  
Use a feature store (like Feast) so people aren’t reinventing the same features again and again.

### Branching & Reviews  
Adopt a Git strategy (e.g. feature branches + PRs) with required reviews. This keeps everyone in the loop and avoids surprises in production.

### Modular Pipelines  
Break up your code so training, preprocessing, evaluation, and deployment each have their own script or function. Bonus: this also helps you reuse components across projects.

---

## 4. Smarter Automation & Deployment

You don’t want someone babysitting model deployments all day. Instead:

- Use CI/CD tools (like GitHub Actions or Jenkins) to trigger training and validation when new code is pushed.
- Add staging environments to test models before full deployment.
- Set up canary deployments to send a small % of traffic to new models, just in case something breaks.

And yeah—monitor everything. Drift, latency, accuracy, resource usage. Tools like Prometheus and Grafana will save your weekend.

## MLOps Architecture (Medium Team Setup)

Let’s visualize what the updated MLOps stack might look like for a medium-sized team.

At this stage, you’ll likely have:

- A shared cloud development environment (e.g., JupyterHub or SageMaker Studio)
- Git + DVC for version control of code and data
- CI/CD pipelines connected to an orchestrator like Kubeflow Pipelines or Argo
- A feature store to centralize and reuse engineered features
- A model registry with approval workflows (e.g., MLflow)
- Staging and production environments for model serving
- Automated deployment triggers (with canary rollout support)
- Monitoring via Prometheus, Grafana, or ELK
- Secrets and permissions managed via Vault or a cloud-native secrets manager

![MLOps medium team architecture](/images/medium-team-mlops.png)

This setup helps you maintain speed while introducing enough structure to support more teammates, more models, and more complexity.

---

## 5. Monitoring, Retraining & Feedback Loops

With more models in production, you’ll want:

- **Dashboards** for model metrics, latency, and drift  
- **Alerts** when performance drops below a threshold  
- **Scheduled or triggered retraining** when the data changes  
- **User feedback loops** if you have human-in-the-loop applications  

You’re not just “deploying and forgetting” anymore—now it’s about maintaining models over time.

---

## 6. Security, Roles & Access

More teammates = more access. It’s time to be thoughtful about security.

- Set up role-based access to notebooks, pipelines, and models  
- Use secret managers (Vault, AWS Secrets Manager) to store API keys and credentials  
- Keep audit logs so you know who changed what, and when  

Even small incidents (like overwriting a model accidentally) can be costly when you’re growing fast.

---

---

## Final Thoughts

Growing a team is exciting—but it also means your MLOps setup has to grow with you.

The key is to **build on top of your existing foundation**. Keep what works, automate what’s slowing you down, and put just enough structure in place to stay productive without overcomplicating things.

In Part 3, we’ll explore how this evolves again for **enterprise teams**—think compliance, cost optimization, and multi-region setups.

---