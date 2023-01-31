---
description: The Go SDK to interact with Progressively
---

# Go

### Installation <a href="#installation" id="installation"></a>

```
$ go get github.com/progressively-crew/sdk-go@latest
```

### Usage <a href="#usage" id="usage"></a>

#### Create an SDK (Build method)

```go
sdk := progressively.SdkBuilder("valid-sdk-key", "BACKEND_URL").Build()
```

**AddField**

Fields is an option that allows passing data about your users to create targeting strategies. For instance, you can set an email field, and in Progressively's dashboard, you can create a rule that only targets people that use an expected domain:

```go
sdk := progressively.SdkBuilder("valid-sdk-key", "BACKEND_URL").AddField("email", "marvin.frachet@something.com").Build()
```

**Evaluate**

```go
varValue := sdk.Evaluate("theFlagKey")
```

**LoadFlags**

```go
sdk.LoadFlags()
```
