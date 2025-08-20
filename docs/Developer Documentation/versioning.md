---
sidebar_position: 2
---
# Versioning
For this project, we have kind of a unique versioning scheme. While similar to semantic versioning, there are some important differences. The naming I chose goes as follows: `v(MAJOR).(MINOR).(PATCH).(API-VERSION)`

`MAJOR` version (`vX.*.*.*`) indicates major releases (generally with a big announcement, video from IToncek, etc.). You should probably not change this version. Bumping this version is done only after long discussions and major debugging sessions. 

`MINOR` version (`v*.X.*.*`) is bumped on stable releases. This is the channel, which is distributed as "stable". Again, bumping this version is only for the maintainers. Should be set to zero for major releases.

`PATCH` (`v*.*.X.*`) is the "preview" version. This channel is probably stable, but needs testing. After consulting with maintainers, at the end of your pull request, you get the privilige of bumping this version. Should be set to zero for major and minor releases.

`API-VERSION` (`v*.*.*.X`) is marking changes in the API, which makes it uncompatible with older versions of the API project. You should bump this version every time you commit any change in the commons.proto package. This version is only internal and is used only in the commons project, where this variable marks compatible and incompatible API versions. Should be set to zero for major, minor and patch releases.

# Examples

1) *First "production ready" version of the app* - **v1.0.0.0**, bumped by IToncek, major event with a post on reddit and a YouTube video
2) *After production release, we add a new gamemode* - **v2.0.0.0**, same as first production release, major event
3) *Adding possibility of creating custom cards, already tested in beta* - **v2.1.0.0**, sending out updates for "stable" branch of the app
4) *Experimetnal tool for adding custom icons* - **v2.1.1.0**, sending out updates for "preview" branch of the app
5) *Updating protocol to support removing custom cards when this feature is still in pull-request hell* - **v2.1.1.1**, nobody actually cares, just ensuring compatibility
