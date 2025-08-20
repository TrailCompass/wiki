---
slug: 2025-06-02-welcome
title: Welcome to the TrailCompass newsroom
authors: [itoncek]
tags: [status]
---
Hi everyone,
we're now working hard on the trailcompass project so here's a little sneak-peak of what is happening under the hood.
<!-- truncate -->
During the development phase and first publicly accessible beta builds (which will be released when TrailCompass is somewhat ready to be used in the real world), we've opted to use native java serialization for communication between the server and all clients. While this might be unsafe, we are intending to replace it for the full release with somehing more secure. The entire API layer is abstracted to a simplified packet protocol, where clients are driving all the communication.

For the first release of TrailCompass, we're targetting the [home game](https://store.nebula.tv/collections/nebula/products/hideandseek) as our target game rule set. We've experimented with using plugins to drive rule sets, but as of now, we've decided to ditch this functionality, as we're trying to simplify this monumental task to get it finished.