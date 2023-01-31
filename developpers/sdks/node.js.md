---
description: The Server Side JavaScript SDK to use in your application running in Node.js.
---

# Node.js

### Installation

```shell
$ npm install --save @progressively/sdk-node
```

### Usage

#### Create an SDK instance

```javascript
const { Progressively } = require("@progressively/sdk-node");

const options = {
  apiUrl: "your url server",
};

const sdk = Progressively.init("YOUR_ENVIRONMENT_CLIENT_KEY", options);
```

The `options` object can also receive other (optional) attributes such as **fields**

**fields** is an option that allows passing data about your users to restrain the audience eligibility. For instance, you can set an email field, and in Progressively's dashboard, you can create a rule that only targets people that matches that field:

```javascript
const options = {
  apiUrl: "your url server",
  websocketUrl: "your url server for websockets",
  fields: {
    email: "@progressively.com",
  },
};
```

#### Load the flags

```javascript
sdk.loadFlags();
```
