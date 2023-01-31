---
description: What else to say? :)
---

# PHP

### Installation

In your `composer.json` file, add the following package:

```json
{
  "require": {
    "progressively/sdk-php": "dev-fix-packagist"
  }
}

```

And finally, run the following inside your terminal:

```shell
$ composer install
```

### Usage

#### Create an SDK instance

```php
$option = array(
    "apiUrl" => "your url server"
);

$sdk = Progressively::create("YOUR_ENVIRONMENT_KEY", $option);

```

#### Check the variant of a flag

```php
$sdk->isActivated('theFlagKey');
```

{% hint style="info" %}
In the future, this function will change its name to better reflect the way Progressively deals with feature flags.
{% endhint %}
