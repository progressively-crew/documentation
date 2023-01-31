---
description: Giving you control and flexibility at every level possible.
---

# Hierarchical organisation

Progressively is built on top of 3 entities that are:

* projects
* environments
* feature flags

Each **project** can have **multiple environments** that can have **multiple feature flags**.

This hierarchical structure allows the same instance of Progressively to hold multiple projects, but also to apply different feature flag resolution rules to different environments.

For example, if I have a `New merchant store` project with 3 environments (`Development`, `Staging`, `Production`), I can define different flag resolution rules for each of these environments.

This is practical for testing early in the process, on a not-so-critical environment with more permissive rules, and to keep strong constraints on the `Production` environment.

{% hint style="info" %}
Note that when creating a feature flag on a given environment, it will also be created for the other environments of the given project, **for consistency purposes**. This way, when using a specific flag in your codebase, **it will resolve a value**. Of course, you can define specific rollout configurations for a flag in each environment.
{% endhint %}
