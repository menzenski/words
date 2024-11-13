---
title: "Incident Response is Platform Engineering"
date: "2024-11-13T10:04:07-06:00"
disableShare: true
---

I'm at [KubeCon/CloudNativeCon NA](https://events.linuxfoundation.org/kubecon-cloudnativecon-north-america/) this week,
and attended the co-located
[Platform Engineering Day](https://events.linuxfoundation.org/kubecon-cloudnativecon-north-america/co-located-events/platform-engineering-day/)
event yesterday. One of the talks there was given by my friend Atulpriya Sharma (GitHub:
[@techmaharaj](https://github.com/techmaharaj)), on the topic "Are you really ready to adopt a platform?" (materials
are [here](https://github.com/techmaharaj/platform-readiness-checklist) - thank you Atul for making these available).

In his talk, Atul provided a questionnaire and scorecard that an organization could use to self-assess their "platform
engineering readiness" prior to or during an initial investment in a platform engineering function. One of the questions
in the list was about the incident response process in the organization, and the inclusion of that question (of an
incident response question in a platform engineering checklist) really got me thinking. I pivot here from Atul's talk to
my own opinions (I also [live-skeeted](https://bsky.app/profile/me.nzen.ski/post/3larhlndedx2g) some of these thoughts).

**Incident response is platform engineering**. If that sounds odd to you, it shouldn't. The KubeCon/CloudNativeCon
conference is really organized around a set of tools (around the open-source tools and projects that comprise the
vaunted [CNCF Landscape](https://landscape.cncf.io/)). This is great in some ways — getting to connect with other
practitioners who use these tools, being able to talk to project maintainers is valuable, and so on — but it's less
great in other ways. Specifically, there are a lot of problems, challenges, and opportunities for which "use a tool" is
not the right solution (or at least, not the right first step).

There are a lot of tools in the platform engineering space that enable developers to do things like create new AWS S3
buckets or database infrastructure, or to easily put a local application into production. These are absolutely
platform engineering tasks, but we shouldn't pretend that this kind of work is the _definition_ of platform engineering.
The purpose of platform engineering is not to "shorten the time to production" or "shorten the time to infrastructure
creation". If it's shortening the time to anything it's "shortening the time to value".

Maybe that can even be reframed as "**shortening the time spent on work that doesn't contribute to the delivery of
differentiating business value**".

If I'm an application developer, the business logic that I implement in that application as code is differentiating,
for my organization - it is the work that I was hired to do, that can't be outsourced to a third-party service
provider, to automation, or to a manual process. It's the reason that my role exists. Any work that
takes me away from that should be minimized - the role of platform engineering is to do that minimizing.

There is a significant amount of toil involved in creating new infrastructure that will host and support the
applications that provide the business value. Minimizing the time spent on the creation and operation of that
infrastructure is a key platform engineering function - we have infrastructure-as-code tools, orchestration tools,
third-party vendors, and other options. The platform engineering domain pays a lot of attention to notions like
developer experience, developer productivity, and so on. Platform engineers are engineers and have lots of overlap
with non-platform-engineering developers - they can intuit where there is toil that can be automated, or they can talk
to the developers. All of this is fine.

But there's another kind of toil that's worth platform engineering attention as well - the incident response process.
If "creating new infrastructure" is toil, it's _planned toil_. Incident response is _unplanned toil_ - a developer gets
pulled away from their differentiating-value work to chase down an issue in the logs, roll back a failed deployment,
push a hotfix for a broken depednency, or exec into a pod and test network connectivity. Insert your own organization's
incident actions as appropriate.

But there's other, less visible toil in incident response too, and it can be just as significant. In incident response
scenarios you're not limited to technical, "engineering" actions. You may need to read through a bunch of commits or
changelogs to understand what changed in the service that your service called - did something break on their side or
on yours? (These services are owned by different teams with different deployment processes, of course). Once an incident
is mitigated, you may need to prepare an incident review document, attend (or run) an incident review meeting, write up
a list of after-action items resulting from the incident, and work with other teams or even external vendors to document
what happened, what you've learned from it, and what you'll change going forwards.

That's all toil, and it's toil that's ripe for platform engineering attention. If you invest in your deployment process,
you'll have good change tracking to understand what the state of your environment is at any particular time (very
useful during an incident). You might implement an automated changelog process (so that team A can see at a glance what
recent changes have been made for service B, which they don't own). An investment in application metrics can enable
queries in a UI that will make understanding an incident easier for less technical stakeholders. An investment in
incident process automation can enable an engineer to quickly scaffold incident review documentation that captures all
the necessary information. A standard incident process definition can enable the organization to efficiently locate
information on past incidents. None of this is "infrastructure creation" or "infrastructure automation", but all of
it is platform engineering.

The problem space in platform engineering is far larger than it appears. Don't limit yourselves to a narrow,
infrastructure-focused, tools-focused slice of that domain. There's a lot more potential value that we can add.
