---
description: The React SDK. Works on the client, but also on the server.
---

# React

### Installation

```shell
$ npm install --save @progressively/react
```

### Usage (Browser only)

```javascript
import { ProgressivelyProvider, useFlags } from "@progressively/react";

const FlaggedComponent = () => {
  const { flags } = useFlags();
  /* ... */
};

const progressivelyProps = {
  clientKey: "YOUR_ENVIRONMENT_CLIENT_KEY",
  apiUrl: "your url server",
  websocketUrl: "your url server for websockets",
};

const YourPage = () => {
  return (
    <ProgressivelyProvider {...progressivelyProps}>
      <FlaggedComponent />
    </ProgressivelyProvider>
  );
};

```

### Usage (with SSR)

#### Install the SSR library

```shell
$ npm install --save @progressively/server-side
```

#### Default SSR usage

```javascript
import { ProgressivelyProvider, useFlags } from "@progressively/react";
import { getProgressivelyData } from "@progressively/server-side";

const FlaggedComponent = () => {
  const { flags } = useFlags();
  /* ... */
};

const YourPage = ({ progressivelyProps }) => {
  return (
    <ProgressivelyProvider {...progressivelyProps}>
      <FlaggedComponent />
    </ProgressivelyProvider>
  );
};

export async function getServerSideProps({
  req,
  res,
}: {
  req: Request,
  res: any,
}) {
  const { data, response } = await getProgressivelyData("valid-sdk-key", {
    websocketUrl: "ws://localhost:4000",
    apiUrl: "http://localhost:4000",
    fields: {
      id: userIdFromNextjsCookie,
    },
  });

  return {
    props: {
      progressivelyProps: data,
    },
  };
}
```

#### SSR with sticky user

When using Progressively with a rollout percentage that is not 100%, you want your users to have a consistent experience. In order to do so, Progressively needs a way to stick a variant to a user id.

The handling of creating IDs for anonymous users is done by Progressively under the hood. However, we need an extra step on your side to make it work properly: you have to set a cookie and forward the cookie to the Progressively instance:

```javascript
import { ProgressivelyProvider, useFlags } from "@progressively/react";
import { getProgressivelyData } from "@progressively/server-side";

const FlaggedComponent = () => {
  const { flags } = useFlags();
  /* ... */
};

const YourPage = ({ progressivelyProps }) => {
  return (
    <ProgressivelyProvider {...progressivelyProps}>
      <FlaggedComponent />
    </ProgressivelyProvider>
  );
};

export async function getServerSideProps({
  req,
  res,
}: {
  req: Request;
  res: any;
}) {
  const userIdFromNextjsCookie =
    (req as any).cookies?.["progressively-id"] || null;

  const { data, response } = await getProgressivelyData("valid-sdk-key", {
    websocketUrl: "ws://localhost:4000",
    apiUrl: "http://localhost:4000",
    fields: {
      id: userIdFromNextjsCookie,
    },
  });

  const progressivelyCookie = response?.headers?.get("set-cookie");
  res.setHeader("set-cookie", progressivelyCookie);

  return {
    props: {
      progressivelyProps: data,
    },
  };
}
```
