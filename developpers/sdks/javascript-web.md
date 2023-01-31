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
