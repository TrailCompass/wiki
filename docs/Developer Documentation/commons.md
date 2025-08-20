---
sidebar_position: 2
---
# Commons
This [repository](https://github.com/TrailCompass/commons) is the glue, holding the entire software together. It consists of two main parts. API part is an implementation of the communication protocol, Proto part defines the entire protocol, including all shared objects.

## Protocol
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

# Creating a subexchange
Every subexchange should represent a different module of the TrailCompass protocol. For example, all the packets related to login and authentication should be contained within one subexchange, in this case called [`IAuthExchange`](https://github.com/TrailCompass/commons/blob/main/src/main/java/space/itoncek/trailcompass/proto/exchange/IAuthExchange.java).