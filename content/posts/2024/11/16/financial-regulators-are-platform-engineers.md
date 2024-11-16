---
title: "Financial Regulators are Platform Engineers"
date: "2024-11-16T07:38:07-06:00"
disableShare: true
---

Yesterday I attended a KubeCon panel that ended up being one of my favorite KubeCon sessions of the week: "Platform
Engineering In Financial Institutions: The Practicioner Panel". Moderated by
[Paula Kennedy](https://bsky.app/profile/paulalkennedy.bsky.social) (Syntasso), with panelists
Chris Plank (NatWest Bank), [Suhail Patel](https://bsky.app/profile/suhailpatel.bsky.social) (Monzo),
[Jinhong Brejnholt](https://bsky.app/profile/jbrejnholt.bsky.social) (Saxo Bank), and
[Rachael Wonnacott](https://twitter.com/rachwonn) (Fidelity International), the discussion went deep into establishing
and sustaining a platform engineering practice in a highly-regulated industry.

I enjoyed the panel very much. I wish it had been longer, even - there was so much good discussion happening that it
went over its alloted time. The whole panel was interesting, but at the end it got extra-interesting for me, because
the conversation started to pivot to the impact of all those regulations and whether they could be a good thing.

I'm a fan of the idea of ["enabling constraints"](https://cutlefish.substack.com/p/making-things-better-with-enabling),
and have leveraged the external regulations in my own work environment as a way to drive adoption of specific changes
or processes. (I don't work in banking, but I am at a company that processes payments - we are PCI-DSS Level 1
certified, and have a number of other certifications/are compliant with a number of other regulations as well). For
example, when proposing the migration of a manual "ClickOps" process to a more automated "GitOps" process, I might point
out that the latter process produces an audit trail of pull request approvals, showing not only who made the change but
who approved it, and that those approvals will help us demonstrate process compliance during the audit process.

Towards the end of the panel discussion Rachael and Suhail made some comments about working with external auditors -
to the effect of "they're just people trying to do their jobs, there's no need to be antagonistic" (I agree). I think
it was Suhail specifically who made a comment during this exchange about regulators trying to establish guardrails, and
a lightbulb appeared over my head in that moment.

Regulators are themselves platform engineers!

Think about it: they are operating in a very large and complex distributed system, trying to build processes that
allow their customers (banks, companies) to deploy changes safely (uptime is really important). They're doing the same
things that I as a platform engineer do with developers and teams within my organization, they're just working at a
higher level of abstraction and with companies instead.

It's fun to think about this. We've become comfortable in the platform engineering field thinking about multiple
platforms and multiple levels of platforms coexisting within an organization (for example, in my own organization we've
started to distinguish the application platform from the data platform), but as is so often the case, everything is
fractal. We can zoom out and see a higher order platform landscape in which our organization is one actor out of many.

This is something I'm going to continue to think about. As platform engineers we spend a lot of energy thinking about
our "downstream" users and customers - whether we are supporting, steering, guiding, enabling, blocking, or accelerating,
in my experience we generally tend to think of that relationship as having two actors - platform engineering users and
developer/customer users. As a result of this KubeCon panel, I've now got a new mental model, one with three actors:
upstream regulators, platform engineering, and downstream developers. What will change if we start thinking about
ourselves more as being "in the middle" of a larger set of platform layers? I don't know yet, but this is why I love
KubeCon - I always come away with new ideas.
