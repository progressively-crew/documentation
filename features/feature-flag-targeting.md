---
description: >-
  Configure your feature flag rollout rules and define the audience that should
  receive a given flag variation.
---

# Feature flag targeting

Progressively comes with two main ways to target the users that are supposed to receive a specific variant of your feature flags: The **quantitative way** and the **qualitative way** (they are not exclusive).

{% hint style="info" %}
Any of the **quantitive** or **qualitative** rules will only apply if the feature toggle is **activated**. If it's not activated, every single user will receive the `false` variation of your flags.
{% endhint %}

### The quantitative way

After a feature flag creation, you can decide which percentage of your audience should receive the `true` variation of your feature flag using the slider in the **"Audience"** pane:ge

<figure><img src="../.gitbook/assets/screely-1675176883577.png" alt="Progressively dashboard with 100% of rollout"><figcaption></figcaption></figure>

### The qualitative way

You can also choose to add additional eligibility constraints.

For example, it's possible to create rules that will allow **50%** of the users that match the following two rules to see the `true` variant of the flag:

* People with an **email containing @progressively.app**
* People with an **email containing @bestfriends.com**

<figure><img src="../.gitbook/assets/screely-1675177124874.png" alt="Progressively dashboard with a configuration allowing 50% of the users matching the given rules to resolve the feature flag."><figcaption></figcaption></figure>
