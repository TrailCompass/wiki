---
sidebar_position: 2
---
# Protocol {#protocol}
This part of the commons repository contains the exchange definitions, exchanged objects, request and response packets and utilities, needed for generic exchanges. Exchange definitions are written like interfaces in the following style:
```java
public interface IExchange {
    IAuthExchange auth();
    ISystemExchange system();
    ITestExchange test();
}
```
Every method of this class is a subexchange, containing the actual executable methods. They need to be defined as their interface variant, not any derived class. These are also written like interfaces using the following style:
```java
public interface ITestExchange {
    ServerVersionResponse version(ServerVersionRequest request) throws BackendException;
    OkResponse castCardWithOtherCard(CastCardWithOtherCardRequest req) throws BackendException;
}
```
In the demo provided above, this subexchange, called `ITestExchange`, defines two methods the client can execute. `version()` will provide the current version of the server. [`ServerVersionRequest`](https://github.com/TrailCompass/commons/blob/main/src/main/java/space/itoncek/trailcompass/proto/requests/system/ServerVersionRequest.java) is just an empty class, which can be used to initiate the exchange. **Every method needs an unique request class.** Responses of multiple classes can be duplicated. Next, the server will respond with [`ServerVersionResponse`](https://github.com/TrailCompass/commons/blob/main/src/main/java/space/itoncek/trailcompass/proto/responses/system/ServerVersionResponse.java) record. This object contains the requested information. Finally, every method has to throw BackendException, which is a blanket expression for any error, which pops up while executing the request.

The same can be said about `castCardWithOtherCard()` method. It consumes [`CastCardWithOtherCardRequest`](https://github.com/TrailCompass/commons/blob/main/src/main/java/space/itoncek/trailcompass/proto/requests/deck/CastCardWithOtherCardRequest.java), which is a record, containing the token of a player, `UUID` of the cast card and `UUID` of another card from hider's deck. It returns [`OkResponse`](https://github.com/TrailCompass/commons/blob/main/src/main/java/space/itoncek/trailcompass/proto/responses/generic/OkResponse.java), which is equivalent to `void` return type in Java.

## Creating a subexchange {#creating-subexchanges}
Every subexchange should represent a different module of the TrailCompass protocol. For example, all the packets related to login and authentication should be contained within one subexchange, in this case called [`IAuthExchange`](https://github.com/TrailCompass/commons/blob/main/src/main/java/space/itoncek/trailcompass/proto/exchange/IAuthExchange.java).

When creating a new subexchange, you should first define the exchange's methods and packet definitions (this will be explained [later](#packet-definitions)). This should be written in the following format: 
```java
public interface ITestExchange {
    ServerVersionResponse version(ServerVersionRequest request) throws BackendException;
    OkResponse castCardWithOtherCard(CastCardWithOtherCardRequest req) throws BackendException;
}
```

:::danger

When commiting any changes in the API, it is necessary to update the version number. More information about this procedure can be found in the [relevant chapter](../versioning.md) of this documentation!

:::

As described in the [protocol](#protocol) section, every method has to have exactly one parameter which is a object, referencing an unique packet definition. This is due to the fact, that we are not specifying the method being executed, we are only sending an object and the server has to decipher, which route to take. The returns can be repeated, or completely omitted (similar to using `void` return in java) using OkResponse.

As a limitation of this system, every method needs to throw BackendException for the server to be able to internally throw error messages, which are collected and processed in one place. Also while decoding, it allows the client to throw any exception (for example Connection lost or similar issues).

When this is done, remember

## Creating a method {#creating-method}

### Creating packet definitions {#packet-definitions}