---
slug: grpc
title: ServiceStack gRPC
---

ServiceStack's gRPC support enables a highly productive development environment for developing high-performance gRPC HTTP/2 Services
by making ServiceStack's existing typed Services available via ASP.NET's gRPC endpoints. In addition to offering superior value
in developing gRPC Services on the Server, ServiceStack also offers a 
[simplified development model for gRPC Clients](https://todoworld.servicestack.net) for streamlined end-to-end productivity.

### Getting Started

The easiest way to get started is to start from a new [grpc](https://github.com/NetCoreTemplates/grpc) template, i.e. a copy of the 
empty [web](https://github.com/NetCoreTemplates/web) project template that's pre-configured with gRPC support:

    $ x new grpc MyGrpcProject

### ServiceStack Services are gRPC Services!

Whilst Protocol Buffers imposes additional restrictions on the Types of DTOs that can be returned, in general the only change to
ServiceStack Services following our [recommended API Design](/api-design) need to add are `[DataContract]` and `[DataMember]` attributes 
on each DTO member assigning unique field index to each property, i.e. what's already required to support [ProtoBuf Services](/protobuf-format)
or used to customize XML wire format in XML or [SOAP Services](/soap-support).

For an example here's the complete annotated `GetTodos` Service from [todo-world](https://github.com/NetCoreApps/todo-world) gRPC Service:

```csharp
[DataContract]
public class GetTodos : IReturn<GetTodosResponse> {}

[DataContract]
public class GetTodosResponse
{
    [DataMember(Order = 1)]
    public List<Todo> Results { get; set; }

    [DataMember(Order = 2)]
    public ResponseStatus ResponseStatus { get; set; }
}

[DataContract]
public class Todo
{
    [DataMember(Order = 1)]
    public long Id { get; set; }

    [DataMember(Order = 2)]
    public string Title { get; set; }

    [DataMember(Order = 3)]
    public int Order { get; set; }

    [DataMember(Order = 4)]
    public bool Completed { get; set; }
}

public class TodoServices : Service
{
    public static List<Todo> Todos { get; } = new List<Todo>();
    public object Get(GetTodos request) => new GetTodosResponse { Results = Todos };
}
```

As gRPC mandates a static service contract (i.e. can only return the same Response DTO Type) your Request DTOs are required to 
adhere to ServiceStack best practices and be annotated with either `IReturn<TResponse>` or `IReturnVoid` interfaces. 

In order to receive structured Error Responses your `IReturn<T>` Response DTOs requires `ResponseStatus` property as normal.

> Only services annotated with `IReturn*` interfaces and member indexes (as above) will be registered as gRPC Services.

Trying to call a Service without these annotations will result in an error that the Service you're trying to call doesn't exist.

### Enable gRPC Services in existing .NET Core 3 projects

By default this Service is available in [all of ServiceStack's supported formats](/formats), to also make it available via ASP.NET Core's
gRPC Endpoints you can [mix it](/mix-tool) in [Modular Startup](/modular-startup) projects:

    $ x mix grpc

Or to manually configure it, add a reference to the .NET Core 3 **ServiceStack.Extensions** NuGet package:

    $ dotnet add package ServiceStack.Extensions

Add the necessary dependencies:

```csharp
public void Configure(IServiceCollection services)
{
    services.AddServiceStackGrpc();
}
```

Then register the `GrpcFeature` Plugin in your `AppHost`:

```csharp
Plugins.Add(new GrpcFeature(App));
```

Which registers all applicable ServiceStack Services in ASP.NET Core's gRPC Endpoint and provides an auto-generated 
[Add ServiceStack Reference](/add-servicestack-reference) `proto` metadata endpoint that Google's protoc generated clients can use
to generate typed client proxies in each of the languages supported by Google gRPC.

## Advantages of ServiceStack gRPC

ServiceStack's code-first message-based development approach offers a number of advantages over most gRPC Service frameworks
which rely on manually maintaining a separate plain-text `.proto` IDL file for defining your gRPC Services.

### Maximize reuse of Knowledge and Investments

Likely the biggest advantage in using ServiceStack to develop gRPC Services is being able to (without additional knowledge) 
leverage your existing investments and knowledge of building HTTP Services which in most cases (after annotating them with unique indexes) 
are automatically available as gRPC Services. This maximizes utility of your Services which can be simultaneously made available
via ASP.NET's gRPC Endpoints and ServiceStack's HTTP and MQ Endpoints alleviating the need to fork or duplicate your Services logic
across multiple implementations or worse, taking the leap to develop gRPC-only services and shutting out clients and environments that
can't make use of gRPC HTTP/2 endpoints yet.

ServiceStack enables the best of both worlds, you can take risk-free step of making your Services available via highly efficient and performant
gRPC HTTP/2 Services for clients and environments that can take advantage of it whilst (in the same App) continuing to make them available via the 
ubiquitous JSON HTTP/1.1 APIs or in any of their [preferred formats](/formats).

### Code-First gRPC Services

By allowing the use of idiomatic C# POCOs to define your Services contract, code-first always enables a superior development experience
which avoids having to rely on external build tools to generate foreign implementation-encumbered types which is limited in capability
to what's generated by opaque build tooling whose output emits single-purpose Types limited for usage in gRPC Services that are restrictive
to the lowest common denominator capabilities of `.proto` files.

By contrast with a code-first approach your idiomatic C# POCOs are the master authority for your Services contract in which you retain 
full control over, that can be further enhanced with attributes to enlist declarative behavior and shared interfaces and are in 
general inherently easier to develop genericized behavior around. As [Service Models](/physical-project-structure#servicemodel-project) 
doesn't have any implementation dependencies they can be easily shared and [referenced in any .NET Project](/why-servicestack#target-multiple-platforms) 
and as clean POCOs they can serve as [multi-purpose models enabling maximum reuse](/service-complexity-and-dto-roles#the-simple-poco-life) 
where they can be utilized in all ServiceStack's POCO libraries as well being supported in [all of ServiceStack's supported formats](/formats).

### No additional complexity or artificial machinery

At its most productive level ServiceStack offers the same highly-productive, clean, friction-free development experience that's enjoyed 
in its other [generic .NET Service Clients](/csharp-client) which requires no build tooling, `.proto` files, any code-generation, 
additional configuration or complexity as the same clean POCO DTOs used to define your Services can be reused on the client 
where by preserving any additional metadata attributes and interfaces which can allow for a richer client experience.

An alternative to sharing your **ServiceModel.dll** with .NET clients is for them to use [Add ServiceStack Reference](/add-servicestack-reference)
to generate .NET DTOs locally which they can easily do using the [x dotnet tool](/dotnet-tool), e.g:

    $ x csharp https://todoworld.servicestack.net

This offers the same behavior as sharing **ServiceModel.dll** binary where they can be used in any 
[.NET Generic Service Client](/csharp-client#built-in-clients), but also allows clients to 
[customize DTO generation](/csharp-add-servicestack-reference#dto-customization-options) to suit their own preferences.

Despite the loss of additional complexity, the use of a generic Service Client offers a superior development model then what's 
available in Google's `protoc` generated Service Clients.

### Smart, Substitutable, Generic GrpcServiceClient

The new `GrpcServiceClient` can be used in **.NET Standard 2.1** and **.NET Core 3** .NET Clients by adding a reference to:

    $ dotnet add package ServiceStack.GrpcClient

This is a full-featured generic Service Client that provides a nicer and cleaner API than what's possible with `protoc` generated clients
and contains most of the built-in functionality of other [C#/.NET Typed Generic Clients](/csharp-client):

  - Substitutable `IRestServiceClient`, `IServiceClientAsync` and `IServiceClientSync` interfaces
  - [Rich Detailed and Structured](/validation) Typed Exceptions
  - Built-in Credentials, JWT, API Key and Session Authentication
    - Transparent auto retry on expired JWT Bearer Tokens after retrieving new JWT from configured Refresh Token
  - Auto populates Version/Auth info in `IHasSessionId`, `IHasBearerToken` and `IHasVersion` Request DTOs
  - Batched API support via `SendAll/Async` and `PublishAll/Async` APIs
  - Global and Instance Request/Response Filters to apply generic custom logic on each request
  - C# 8 `await foreach` friendly `async IAsyncEnumerable<TResponse> Stream()` APIs for Server Stream gRPC Services

Importantly `GrpcServiceClient` shares the same interfaces as all other [C#/.NET Typed Generic Clients](/csharp-client) allowing
development of higher-level shared client logic and libraries decoupled from concrete implementations, improved testability,
easy substitution where you could easily switch to `JsonServiceClient` for improved debuggability or if you've hit a limitation of protocol buffers,
parallel client/server development where clients can temporarily bind to a mock client whilst server is being implemented.

The fixed Generic API Surface area of the service client interfaces makes it easier to develop enhanced functionality like
[Cache Aware Service Clients](/cache-aware-clients) in future that existing clients will be able to utilize via a minimally disruptive "drop-in" implementation.

#### Prefer Async

As all .NET gRPC Clients are inherently built on an `async` implementation clients should prefer `*Async` APIs wherever possible as both `protoc` and 
`GrpcServiceClient` both only offer sync APIs over an unoptimal "sync over async" bridge.

#### ServiceStack Interceptor for protoc generated clients

As the `GrpcServiceClient` offers a nicer and clear API, Types and development model its usage over `protoc` clients should generally be preferred, one 
area where you'll want to consider using Google's `protoc` generated clients is in AOT environments like Xamarin.iOS as Google's `protoc` tooling 
emits AOT-friendly Protocol Buffer serialization implementation within its code generated Types.

To better accommodate scenarios where `protoc` clients are used you can use the `ServiceStackClientInterceptor` also in **ServiceStack.GrpcClient**
to replicate most of the rich ServiceStack integration features that's possible to implement using an `Interceptor`. 

The ServiceStack Interceptor can be registered using `GrpcServiceStack.Client()` when creating the protoc `GrpcServicesClient`:

```csharp
// Insecure plain-text example
GrpcClientFactory.AllowUnencryptedHttp2 = true;
var client = new GrpcServices.GrpcServicesClient(
    GrpcServiceStack.Client("http://todoworld.servicestack.net:5054"));

// SSL Example
var client = new GrpcServices.GrpcServicesClient(
    GrpcServiceStack.Client("https://todoworld.servicestack.net:50051", 
        new X509Certificate2("grpc.crt"),
        GrpcUtils.AllowSelfSignedCertificatesFrom("todoworld.servicestack.net")));

// Optional (avoid protobuf-net deserialization)
GrpcServiceStack.ParseResponseStatus = bytes => ResponseStatus.Parser.ParseFrom(bytes);
```

### Preserve rich Semantics and API Design

gRPC Services gives us a highly efficient HTTP/2 concurrent long-lived multiplexed channel with performant Protocol Buffer serialization and a 
vast code-generation framework allowing us to provide Typed clients for most major programming languages and platforms.

An area that could see a regression which all RPC frameworks suffer from is the erosion of the 
[Goals of Service Design](/why-servicestack#goals-of-service-design) and loss of loosely-coupled HTTP API Design that's centered
around resources and applying actions (aka HTTP Verbs) to them which provides both a logical structure for your API Design that is able
to better communicate at a higher-level the commonly understood properties of each HTTP Verb and the subject of each request.

By forcing the usage of **messages** in gRPC Service Requests it partially mitigates against the 
[fragile usage of chatty client-specific method signatures](/why-servicestack#wcf-the-anti-dto-web-services-framework)
plagued by most RPC frameworks like WCF, but still makes it easy for API designs to descend into an logically unstructured "free-for-all" 
surface area adopting uncommonly understood conventions that makes it harder and requires more effort to convey understanding for clients
consuming your API.

By continuing to develop your ServiceStack Services as a good HTTP First citizens using coarse-grained loosely-coupled messages 
oriented around resources, a lot of the rich HTTP semantics is preserved where each Verb remains accessible where its prefixed at the start 
of the rpc Method name:

    rpc [Verb][RequestType](RequestType) returns (ResponseType) {}

The original HTTP Status Code remains accessible from the **httpstatus** gRPC Metadata Response Headers that continues to be populated
in the `WebServiceException.StatusCode` thrown if using `GrpcServiceClient` or `protoc` client configured with the ServiceStack Interceptor.
Any Custom HTTP Headers added by your Services are also returned in gRPC headers including your Services detailed structured Exception
information stored as a serialized `ResponseStatus` message in the **responsestatus-bin** Header that continues to be available in
`WebServiceException.ResponseStatus` property allowing gRPC client Apps to develop [rich form validation bindings](/world-validation#contacts-page)
that's otherwise not possible in gRPC's basic error code and description failed responses.

### Offer best API for every platform

Irrespective of the advantages of gRPC Services we still expect traditional and more ubiquitous HTTP/REST API endpoints to be 
more widely utilized in areas where you don't control both client and server Apps, where interoperability is more important than 
maximum performance, if needing to support Ajax requests in Web Clients where HTTP/JSON is the lingua franca with deep support 
baked into many JS libraries, decoupled scenarios where it's easier to consume clean HTTP APIs then the "complexity tax" required 
for consuming gRPC client proxies or environments where deeper integration of different formats is preferred, e.g. utilizing
[CSV Format](/csv-format) in Excel based workflows or importing datasets into RDBMS Tables which is supported by most RDBMS tooling.

As gRPC is just another endpoint for your ServiceStack Services you don't have to take the risk of committing to one scenario
at the expense of all others and can continue to serve all client consumers with the best API for every platform simultaneously. 

## Limitations

By its nature gRPC and Protocol Buffers have many additional restrictions in the Types it can support:

### Inheritance

In its pursuit of defining a universal service description that can be both implemented and consumed by each major programming language,
Google's gRPC `.proto` and Protocol Buffers suffers from the limitations of needing to abide by the lowest common denominator functionality
available in all languages that's limited to use 
[Protocol Buffers built-in and Well Known Types](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf) 
which is much more restrictive than schema-less formats like JSON where the Type definition is retained in native POCOs used to de/serialize JSON.

The Types of limitations applicable when building gRPC Services in .NET include:

 - No support for Generic Types
 - No proper support for Inheritance
 - All enums need a zero value
 - All enum names to be **globally unique** across all enums used in your Services
 - No built-in Types that can accommodate .NET's `Decimal`, `Guid` Types
 - Built-in `Timestamp` loses precision when when serializing .NET's `DateTime` or `DateTimeOffset` Types

The [protobuf-net](https://github.com/protobuf-net/protobuf-net) library developed by [@mgravell](https://github.com/mgravell) that ServiceStack's
gRPC support uses in its Server implementation (and `GrpcServiceClient`) does its best to transparently work around above limitations, e.g:

 - Creates multiple messages using reified generic type names for each concrete Generic Type used
 - Allows defining layout of base Types to embed ("has a") relation of known sub types
 - Emits `ZERO` enum value for enums without `0` default values
    - Due to unique naming enum scoping rules it's an error to do this for more than 1 Enum
 - Utilizing custom Types defined in an accompanying `bcl.proto` to support .NET's `Decimal`, `Guid` Types
 - Other BCL Types like `DateTimeOffset` can be [supported via surrogates](https://github.com/protobuf-net/protobuf-net/issues/226#issuecomment-319564317)

## Features

In addition to providing a highly-productive code-first development model ServiceStack gRPC adds a lot of additional features that makes 
developing gRPC Services a joy:

### protobuf-net Inheritance

In order to support inheritance [protobuf-net has to retrofit](https://github.com/protobuf-net/protobuf-net/wiki/Getting-Started#inheritance) 
its support by embedding sub classes as different fields in the base class type. This is awkward since all known sub classes needs to be defined 
upfront on the base type using a consistent and non-conflicting numerical field id. 

As it's required by [AutoQuery](/autoquery) it was important to best provide a seamless out-of-the-box solution to alleviate as much friction
as possible so ServiceStack pre-configures this numerical index on all known sub types in your Services Contract with a generated
[Murmur2 hash](https://softwareengineering.stackexchange.com/a/145633/14025) (best overall for speed/randomness) of the **Types Name** that's modded to 
within the `2^29-1` range of [valid field ids in protocol buffers](https://developers.google.com/protocol-buffers/docs/proto#assigning-field-numbers) 
so the possibility of a hash collision is very low (but still possible).

To instead use your own user-defined field id for inherited classes you can use the `[Id]` attribute, for AutoQuery Services it should 
at least start from `10` to avoid id conflicts with base class properties, e.g:

```class
[DataContract, Id(10)]
public class QueryRockstars : QueryDb<Rockstar>
{
    [DataMember(Order = 1)]
    public int? Age { get; set; }
}
```

The `[Id]` needs to be unique for all sub classes and must not conflict with base class field ids, so since AutoQuery Services share the same base-class, any user-defined `[Id(N)]` on AutoQuery Services needs to be unique across all your AutoQuery Services.

Both ServiceStack's transparent or explicit `[Id]` approaches works nicely with the generic `GrpcServiceClient` where it allows calling the base and 
Sub Type properties on DTOs utilizing inheritance, e.g:

```csharp
var response = await client.GetAsync(new QueryRockstars { Age = 27, Include = "Total" });
```

Unfortunately usage of inheritance is [currently not compatible with protoc clients](https://github.com/protobuf-net/protobuf-net.Grpc/issues/50) so 
in order to call AutoQuery Services from protoc generated clients can utilize **Dynamic gRPC Requests** to execute any Service from an loosely-typed
string dictionary.

### Dynamic gRPC Requests

Dynamic Requests lets you to populate Request DTOs of gRPC Services with a `DynamicRequest` DTO in the same way as **QueryString** and **FormData**
is used to populate a Request DTO, in this case `DynamicRequest` is just a Request DTO with a string dictionary:

```csharp
[DataContract]
public class DynamicRequest
{
    [DataMember(Order = 1)]
    public Dictionary<string, string> Params { get; set; }
}
```

Which just like QueryStrings/FormData are also able to [populate deeply nested object graphs from a JSV string](/serialization-deserialization).

By default ServiceStack only generates Dynamic Services for Services annotated with `[Tag("Dynamic")]`, e.g:

```csharp
[Tag(Keywords.Dynamic)]
[DataContract]
public class QueryRockstars : QueryDb<Rockstar>
{
    [DataMember(Order = 1)]
    public int? Age { get; set; }
}
```

This generates an additional Service option for invoking a Service using a `DynamicRequest` DTO instead, in the format:

    rpc [Verb]Dynamic[RequestType](DynamicRequest) returns (ResponseType) {}

For the `QueryRockstars` above, it generates:

    rpc GetDynamicQueryRockstars(DynamicRequest) returns (QueryResponse_Rockstar) {}

Dynamic Requests are useful when you'd prefer to be able to populate Requests from an untyped string Dictionary such as implementing
a [dynamic Query Builder UI](https://github.com/ServiceStack/Admin) which would require significantly less effort and boilerplate 
then trying to map dynamic rules into populating a typed Request.

They're also required for calling Services that doesn't have an explicit Services contract like untyped
[AutoQuery Services utilizing implicit conventions](/autoquery-rdbms#implicit-conventions), e.g:

```csharp
public class QueryRockstars : QueryDb<Rockstar> {}
```

Until [protoc clients are compatible with protobuf-net inheritance](https://github.com/protobuf-net/protobuf-net.Grpc/issues/50) they can
also be used as an alternative for calling inheritance-based Request DTOs like AutoQuery.

The `CreateDynamicService` predicate determines which Services should have dynamic requests generated for it, by default it's limited
to Request DTOs annotated with `[Tag("Dynamic")]`, but can also be made to have dynamic requests for **all AutoQuery Services** with:

```csharp
Plugins.Add(new GrpcFeature(App) {
    CreateDynamicService = GrpcConfig.AutoQueryOrDynamicAttribute
});
```

When configured each AutoQuery Service will have an additional Service available that it can be called with starting with `GetDynamic*` 
where the same `DynamicRequest` can be used to call both a Typed or Untyped AutoQuery Service, e.g:

```csharp
var response = await client.GetDynamicQueryRockstarsAsync(new DynamicRequest {
    Params = {
        { "Age", "27" }, 
        { "OrderBy", "FirstName" },
        { "Include", "Total" },
    }
});
```

In addition to populating the Request DTO each dynamic param will also be available to your services via the `IRequest.QueryString` collection.

### Simulate HTTP Requests

Similar to `DynamicRequest` even normal typed gRPC Service requests can be augmented with gRPC Metadata Request Headers where they can be used
to be able to simulate a HTTP Request where headers starting with:

 - `query.` - added to `IRequest.QueryString`
 - `form.` - added to `IRequest.FormData`
 - `cookie.` - added to `IRequest.Cookies`
 - `header.` - added to `IRequest.Headers` (default)
 - Remaining headers without above prefixes are added to `IRequest.Headers` as-is.

Where this can be used to simulate a valid HTTP Request for Filters, Plugins and HTTP APIs that are very specific on how they analyze HTTP Requests.

So just like `DynamicRequest` you can use dynamic gRPC Metadata Headers to populated typed gRPC Service requests, e.g:

```csharp
var client = new GrpcServiceClient(baseUrl) {
    RequestFilter = ctx => {
        ctx.RequestHeaders.Add("UserAgent", "Googlebot/2.1 (+http://www.google.com/bot.html)"); //impersonate
        ctx.RequestHeaders.Add("query.Age", "27");
        ctx.RequestHeaders.Add("query.OrderBy", "FirstName");
        ctx.RequestHeaders.Add("query.Include", "Total");
    }
};
var response = await client.GetAsync(new QueryRockstars());
```

Where each matching property will populate the Request DTO with the string value using the conversion rules in ServiceStack's 
[built-in Auto Mapping](/auto-mapping).

If you don't wish for Headers to be able to populate Typed gRPC Requests, it can be disabled with:

```csharp
Plugins.Add(new GrpcFeature(App) {
    DisableRequestParamsInHeaders = true
});
```

### Server Stream gRPC Services

All gRPC Services we've seen so far are what gRPC Refers to as **Unary RPC**, i.e. where clients sends a single request to the server and 
gets a single response back. Another very useful communication style supported by gRPC are **Server streaming RPCs**:

> where the client sends a request to the server and gets a stream to read a sequence of messages back. The client reads from the returned stream 
until there are no more messages. gRPC guarantees message ordering within an individual RPC call.

#### StreamServerEvents

There are a couple of scenarios in ServiceStack where this communication channel is primarily useful such as [Server Events](/server-events)
which operates in a similar style with clients connecting to a long-lived HTTP connection that streams back "real-time Events" over the
very light and efficient [SSE](https://www.html5rocks.com/en/tutorials/eventsource/basics/) standard natively supported in browsers.

Although as HTTP Requests are not normally used for maintaining long-lived connections they're susceptible to issues like buffering 
from App Servers, middleware and proxies and require implementing a bespoke health-check and auto-reconnect solution in order to maintain
interrupted service.

As a first class supported communication channel we can instead leverage gRPC's library infrastructure which is perfectly suited for
streaming real-time Server Events that's now also made available via gRPC's efficient HTTP/2 persistent channel with the `StreamServerEvents`
gRPC Service:

    rpc ServerStreamServerEvents(StreamServerEvents) returns (stream StreamServerEventsResponse) {}

Thanks to gRPC all of `protoc` supported languages now have Typed APIs for consuming your [Server Events](/server-events) notifications.

#### GrpcServiceClient Streams

Using the generic `GrpcServiceClient` you're able to take advantage of C#'s 8 new `await foreach` syntax sugar for consuming gRPC Server Streams.

Its usage is analogous to all Server Events clients where your initial connection contains all the channels you want to receive notifications from, e.g:

```csharp
var stream = client.StreamAsync(new StreamServerEvents {
    Channels = new[] {"todos"}
});
```

Then you can use `await foreach` to consume an endless stream of Server Events. Use `Selector` to identify the type of Server Event
whilst the body of each event message can be parsed as JSON, e.g:

```csharp
await foreach (var msg in stream)
{
    if (msg.Selector.StartsWith("todos.")) //custom todos.* events
    {
        var obj = JSON.parse(msg.Json); //body of message in JSON
        if (obj is Dictionary<string, object> map)
        {
            //todos.create + todos.update properties
            var id = map["id"];
            var title = map["title"];
            $"EVENT {msg.Selector} [{msg.Channel}]: #{id} {title}".Print(); 
        }
        else
        {
            //todos.delete id
            $"EVENT {msg.Selector} [{msg.Channel}]: {obj}".Print();
        }
    }
    else
    {
        // general server events, e.g cmd.onConnect, cmd.onJoin, cmd.onLeave
        $"EVENT {msg.Selector} [{msg.Channel}]: #{msg.UserId} {msg.DisplayName}".Print();
    }
}
```

If connected whilst running the [TodoWorld CRUD Example](https://todoworld.servicestack.net/#user-content-c-local-development-grpc-ssl-crud-example)
this stream will output something similar to:

    EVENT cmd.onConnect []: #-1 user1
    EVENT cmd.onJoin [todos]: #-1 user1
    EVENT todos.create [todos]: #1 ServiceStack
    EVENT todos.update [todos]: #1 gRPC
    EVENT todos.delete [todos]: 1

#### protoc Dart Streams

Other `protoc` languages will require using their own language constructs for consuming gRPC Streams,
here's a [example for Dart](https://todoworld.servicestack.net/#dart) that also has a similarly pleasant API for consuming Server Streams:

```dart
var stream = client.serverStreamServerEvents(StreamServerEvents()..channels.add('todos'));
await for (var r in stream) {
    var obj = jsonDecode(r.json);
    if (r.selector.startsWith('todos')) {
        if (obj is Map) {
            print('EVENT ${r.selector} [${r.channel}]: #${obj['id']} ${obj['title']}');
        } else {
            print('EVENT ${r.selector} [${r.channel}]: ${obj}');
        }
    } else {
        print('EVENT ${r.selector} ${r.channels}: #${obj['userId']} ${obj['displayName']}');
    }
}
```

### Implement a Server Stream Service

As they're not your typical unary-style Request/Response service, Server Streams are handled and implemented a little differently
where in addition to inheriting ServiceStack's base `Service` class you'll need to implement the `IStreamService<TRequest,TResponse>`
interface and implement its `Stream()` method for your Service implementation.

Here's the implementation of ServiceStack's built-in `StreamFiles` Service which accepts multiple virtual paths of files 
which returns the File contents and metadata in the same order clients want returned:

```csharp
public class StreamFileService : Service, IStreamService<StreamFiles,FileContent>
{
    public async IAsyncEnumerable<FileContent> Stream(StreamFiles request, CancellationToken cancel = default)
    {
        var i = 0;
        var paths = request.Paths ?? TypeConstants.EmptyStringList;
        while (!cancel.IsCancellationRequested)
        {
            var file = VirtualFileSources.GetFile(paths[i]);
            var bytes = file?.GetBytesContentsAsBytes();
            var to = file != null
                ? new FileContent {
                    Name = file.Name,
                    Type = MimeTypes.GetMimeType(file.Extension),
                    Body = bytes,
                    Length = bytes.Length,
                }
                : new FileContent {
                    Name = paths[i],
                    ResponseStatus = new ResponseStatus {
                        ErrorCode = nameof(HttpStatusCode.NotFound),
                        Message = "File does not exist",
                    }
                };
            
            yield return to;

            if (++i >= paths.Count)
                yield break;
        }
    }
}
```

Although `StreamFiles` is already pre-registered, to register your own gRPC Stream Service add them to the `RegisterServices` collection:

```csharp
Plugins.Add(new GrpcFeature(App) {
    RegisterServices = {
        typeof(StreamFileService)
    }
});
```

> Likewise you can remove the pre-registered `StreamFileService` and `SubscribeServerEventsService` services by removing them from the list

Clients can use `StreamFiles` to efficiently download multiple files over a single gRPC HTTP/2 Server Stream connection in their preferred order:

```csharp
var request = new StreamFiles {
    Paths = new List<string> {
        "/js/ss-utils.js",
        "/js/hot-loader.js",
        "/js/not-exists.js",
        "/js/hot-fileloader.js",
    }
};

var files = new List<FileContent>();
await foreach (var file in client.StreamAsync(request))
{
    files.Add(file);
}
```

With each `FileContent` result containing either the file contents and metadata or an error response for missing files, e.g:

```csharp
// files[0].Name = 'ss-utils.js'
// files[1].Name = 'hot-loader.js'
// files[2].ResponseStatus.ErrorCode = NotFound
// files[3].Name = 'hot-fileloader.js'
```

#### protoc Dart Example

Example of server streaming of files from a protoc generated Dart client:

```dart
var stream = client.serverStreamFiles(StreamFiles()..paths.addAll([
  '/js/ss-utils.js',
  '/js/hot-loader.js',
  '/js/hot-fileloader.js',
]));

await for (var file in stream) {
  var text = utf8.decode(file.body);
  print('FILE ${file.name} (${file.length}): ${text.substring(0, text.length < 50 ? text.length : 50)} ...');
}
```

## SSL Certificate Configuration

Please see the [gRPC SSL docs](/grpc-ssl) for information on how to secure your gRPC connections including scripts for creating custom self-signed
certificates and hosting public gRPC Services behind an nginx proxy.

## gRPC Clients

For most .NET Clients we recommend using our generic `GrpcServiceClient` with deeper ServiceStack integration that can be used with the 
cleaner and richer [Add ServiceStack Reference](/add-servicestack-reference) DTOs that implements clean Service Client interfaces
allowing easy substitution between all of ServiceStack's [.NET Service Clients](/csharp-client), improved testability and implementation 
decoupled gateway logic:

 - [C# / F# / VB.NET Smart GrpcServiceClient](/grpc-generic)

### protoc generated clients

For all non .NET Clients and AOT environments like Xamarin.iOS we recommend using Google's `protoc` generated clients:

 - [C#](/grpc-csharp)
 - [Swift](/grpc-swift)
 - [Java](/grpc-java)
 - [Dart](/grpc-dart)
 - [Go](/grpc-go)
 - [Node.js](/grpc-nodejs)
 - [Python](/grpc-python)
 - [Ruby](/grpc-ruby)
 - [PHP](/grpc-php)
 
## gRPC Web

As it's [impossible to implement the HTTP/2 gRPC spec in the browser](https://grpc.io/blog/state-of-grpc-web/),
in order to be able to consume gRPC services from a browser a [gRPC Web Proxy](https://grpc.io/blog/state-of-grpc-web/#the-tech) is needed.

The current recommendation from the gRPC Web team is to use the 
[Configure the Envoy Proxy](https://grpc.io/docs/tutorials/basic/web/#configure-the-envoy-proxy) to forward
the gRPC browser request to the native gRPC endpoint, however as it adds more moving parts and 
additional complexity, if you're not already using envoyproxy we instead recommended using 
ServiceStack HTTP JSON Services, made possible since ServiceStack's gRPC 
Service implementations are also made available over REST-ful HTTP APIs - i.e. the lingua franca of the web.

If [ASP.NET Core adds native gRPC Web support](https://github.com/grpc/grpc-dotnet/issues/99) then using gRPC
clients may provide a more appealing option although it wont have a clean, versatile and rich API as 
[TypeScript Add ServiceStack Reference](https://docs.servicestack.net/typescript-add-servicestack-reference).

### x dotnet tool gRPC Web support

If wanting to evaluate using a gRPC Web Proxy you can use generate different TypeScript and JavaScript clients
using the commands below:

    $ x proto-ts <url>             # TypeScript + gRPC Web Text
    $ x proto-ts-binary <url>      # TypeScript + gRPC Web Binary
    $ x proto-js-closure <url>     # Google Closure + gRPC Web Text
    $ x proto-js-commonjs <url>    # Common JS + gRPC Web Text

Or if preferred you can use the online UI or HTTP API for generating Protocol Buffers and gRPC client proxies at 
[grpc.servicestack.net](https://grpc.servicestack.net).

## gRPC Configuration


