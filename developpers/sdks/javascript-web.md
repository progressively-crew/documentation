---
description: >-
  The Client Side JavaScript SDK to use in your application running in the
  browser.
---

# JavaScript (web)

### Installation

```shell
$ npm install --save @progressively/sdk-js
```

### Usage

#### Create an SDK instance

```javascript
import { Progressively } from "@progressively/sdk-js";

const options = {
  apiUrl: "your url server",
  websocketUrl: "your url server for websockets",
};

const sdk = Progressively.init("YOUR_ENVIRONMENT_CLIENT_KEY", options);
```

The `options` object can also receive other (optional) attributes such as **fields** and **initialFlags**

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

**initialFlags** is an option that is mostly used for server-side rendering. You should not directly use it in your code, except if you are building a server integration that does not yet.

#### Load the flags

```javascript
sdk.loadFlags();
```

#### Listen to WebSockets updates

```javascript
sdk.onFlagUpdate((nextFlags) => {}, optionalUserId);
```

#### Disconnect the WebSockets

```javascript
sdk.disconnect();
```
