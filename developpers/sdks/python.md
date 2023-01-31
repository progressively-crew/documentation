---
description: The Python SDK to interact with Progressively
---

# Python

### Installation <a href="#installation" id="installation"></a>

```shell
$ pip install sdk-progressively
```

### Usage <a href="#usage" id="usage"></a>

#### Create an SDK instance

```python
from sdk.progressively import Progressively

sdk = Progressively.create("YOUR_ENVIRONMENT_KEY", "http://localhost:4000")
```

The SDK can receive an additional fields option.

**fields** is an option that allows passing data about your users to restrain the audience eligibility. For instance, you can set an email field, and in Progressively's dashboard, you can create a rule that only targets people that matches that field:

```python
fields = {"email": "john.doe@email.com", "id": 1}
sdk = Progressively.create("YOUR_ENVIRONMENT_KEY", "http://localhost:4000", fields)
```

#### evaluate

```python
sdk.evaluate("theFlagKey")
```

#### loadFlags

```
sdk.loadFlags()
```

#### fields <a href="#fields" id="fields"></a>

Fields is an option that allows to pass data about your users to create targeting strategies. For instance, you can set an email field, and in Progressively's dashboard, you can create a rule that only targets people that use an expected domain:

```python
fields = {"email": "john.doe@email.com", "id": 1}
sdk = Progressively.create("YOUR_ENVIRONMENT_KEY", "http://localhost:4000", fields)
```

