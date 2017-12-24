# My Highly Opinionated View of Building Systems

Most of this isn't unique, a revelation to anyone, or a new paradigm.  Mostly, I want to write down some of my thoughts that I've tried to articulate at various jobs over my career.

Some overall principles:
* there are two kinds of services
  * services that drive a given user experience
    * UX or experience-based APIs
  * services that provide data, context, etc., and should be _independent_ of a given user experience
    * service APIs
    * these are best as very Restful resource-based APIs
* the client includes both the UI *and* the API driving its user experience
* do *NOT* optimize service APIs for any User Experience
  * You won't know all the user experiences that will use your service, so just don't try.  If you do optimize for one, you'll end up making it a mess for someone else.

Separate, dedicated teams should handle these two types of services.  Ideally, the team that builds the UI is also the team that builds the UX API.  This implies that the UX API is tightly coupled, or perhaps better said, highly cohesive with the UI code.  If there's a native Android client, the team that built that client should also build and manage the UX API associated with it.  Basically do BFF (Backends for frontends) and have the client "team" (doesn't need to be the front-end engineers!) build the BFF.

Services should be build without assuming the user experience.  Without making optimizations for a specific use case, because typically an optimization for one client/experience becomes a problem for another.  In many cases there are "fast", lower latency connections between the BFF and the backend services that minimize the impact of less "optimized" service APIs.
