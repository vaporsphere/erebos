# RPC handlers

A RPC handler is used by the various [APIs](api.md) to make JSON-RPC calls over the provided [transport](transport.md).\
Erebos provides 2 types of RPC handlers: request-based (`RequestRPC`) and stream-based (`StreamRPC`) and 3 factory functions based on the chosen transport: `httpRPC`, `ipcRPC` and `webSocketRPC`.\
The `rpc` factory function will select the appropriate RCP handler and transport based on the provided argument.

### new RequestRPC()

Creates a `RequestRPC` instance using the provided fetch function.

**Arguments**

1. `fetch: (data: Object) => Promise<Object>`

### new StreamRPC()

Creates a `StreamRPC` instance using the provided [RxJS Subject](http://reactivex.io/rxjs/class/es6/Subject.js~Subject.html).

**Arguments**

1. `transport: Subject<Object>`

### httpRPC()

**Arguments**

1. `url: string`

**Returns** a `RequestRPC` instance using the `HTTP` transport.

### ipcRPC()

**Arguments**

1. `path: string`

**Returns** a `StreamRPC` instance using the `IPC` transport.

### webSocketRPC()

**Arguments**

1. `url: string`

**Returns** a `StreamRPC` instance using the `WebSocket` transport.

### rpc()

**Arguments**

1. `endpoint: string`

**Returns** a `RequestRPC` or `StreamRPC` using the relevant transport based on the provided `endpoint` (URL or socket path when using IPC).