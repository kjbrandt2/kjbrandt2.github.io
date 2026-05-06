---
layout: post
title: "Canonical, Snap, and the Infrastructure We Forgot to Question"
date: 2026-05-06
categories: [essays]
tags: [ubuntu, canonical, snap, linux, cybersecurity, infrastructure, open-source, resilience, governance]
excerpt: "A DDoS against Canonical did not just interrupt services. It exposed an uncomfortable question about Ubuntu’s direction: how much of an open-source operating system should depend on centralized infrastructure?"
---

There are few things more clarifying than watching the operating system you trust become difficult to reach because somebody, somewhere, has decided to turn infrastructure into a geopolitical piñata.

Canonical, the company behind Ubuntu, recently acknowledged that its web infrastructure was under what it called a “sustained, cross-border attack.” Reports described the event as a Distributed Denial of Service attack affecting Ubuntu and Canonical services, with a group known as 313 Team, also called the Islamic Cyber Resistance in Iraq, claiming responsibility. As with most things involving attribution, Telegram channels, packet floods, and people with dramatic names, that claim should be handled with care. Claiming responsibility is not the same thing as proving responsibility.

Still, the incident matters.

It matters because Ubuntu is not some obscure hobby project hiding in the back room of computing history. Ubuntu is a major Linux distribution used by developers, enterprises, cloud providers, hobbyists, schools, labs, and people like me who want their machines to work without first negotiating with the spirits of seventeen forgotten dependencies.

I have used Ubuntu for years. I understand the appeal. It is practical, well-documented, widely supported, and familiar enough that most problems have already been suffered by someone else in public, which is one of the quiet blessings of civilization.

But this incident made something visible.

Not because it proved Ubuntu is bad. It did not. Not because it proved Snap caused the outage. It did not. Not because it proved Canonical is malicious. It did not.

It made visible the assumptions underneath the system.

The Marine Corps has a saying about assumptions that is not fit for a corporate slide deck, which is one reason it is useful. The polite version is this: assumptions are where plans go to die.

That is what this incident exposed for me. What had I assumed about Ubuntu’s resilience? What had I assumed about centralized stores? What had I assumed about open source infrastructure simply because the source code was open?

The answer, uncomfortably, is that I had assumed more than I had inspected.

## “Cross-Border Attack” and the Language of Seriousness

Canonical’s initial public language described the event as a “sustained, cross-border attack.” Later reporting quoted Canonical confirming a sustained, cross-border DDoS attack.

That phrase is not necessarily false. A DDoS is often cross-border in the practical sense. Compromised machines, botnets, proxies, rented infrastructure, and hostile traffic do not pause politely at customs checkpoints. Packets are famously indifferent to passports.

But “cross-border attack” is one of those phrases that sounds more clarifying than it is. It gestures toward seriousness without giving users much operational clarity.

What users needed was not a geopolitical adjective. They needed plain information:
What services are affected?
Are package repositories affected?
Are ISO images safe?
Are security advisories reachable?
Are Snap services degraded?
Are APT mirrors functioning?
What should administrators do if normal update paths fail?

To Canonical’s credit, it later stated that mitigations had been implemented and services affected by the DDoS attack had been restored, though some services might remain partially degraded. That is useful. But the earlier phrase still matters because crisis communication is part of infrastructure trust.

In an incident, clarity is not decoration. It is a control.

A good incident statement does not need to satisfy everyone’s curiosity. It does need to tell users what is known, what is not known, what is affected, what is not affected, and what they should do next. Otherwise, people fill the gaps themselves. The internet, being a generous institution, will fill them with panic, speculation, memes, and four men in a forum explaining why this would not have happened on Gentoo.

## Availability Is Security

It is tempting to think of DDoS attacks as crude. In many ways, they are. A DDoS is not a subtle jewel thief descending through a skylight. It is more like a mob blocking every road into town while shouting.

But crude does not mean harmless.

Availability is part of security. That is especially true when the affected infrastructure supports operating system downloads, authentication, developer services, package access, security guidance, or update workflows.

If users cannot reliably reach the services they need during a security event, the system is weaker than its design documents suggest. If administrators cannot easily find guidance, confirm integrity, or route around failure, then the outage becomes more than inconvenience. It becomes friction at precisely the moment friction is most expensive.

That is why this was more than a bad day for a website.

It was a stress test.

And systems reveal themselves under stress.

## The Copy Fail Timing Problem

There is another wrinkle in the story, and it is precisely the sort of wrinkle that makes infrastructure people age in dog years.

Around the same time Canonical was dealing with the DDoS, the Linux ecosystem was also responding to Copy Fail, CVE-2026-31431, a high-severity local privilege escalation vulnerability in the Linux kernel. Canonical described it as affecting Ubuntu releases before 26.04, with mitigations released through `kmod` and kernel fixes following through normal update channels.

Some people speculated that the DDoS could be related to Copy Fail. Tom’s Hardware noted that speculation, while also calling the premise “a little shaky.” That caution is warranted.

This does not prove Copy Fail caused the DDoS.
It does not prove the attackers were trying to prevent patching.
It does not prove Ubuntu packages were compromised.
It does not prove that anyone should run screaming into the woods holding a Debian netinst ISO like a sacred object.

Those would be dramatic claims, and dramatic claims are best handled with tongs.

But the timing matters anyway.

Copy Fail is not remotely exploitable by itself. An attacker needs some sort of local foothold first: an account, a workload, a CI job, a container context, or another way to execute code on the system. Once that foothold exists, however, the vulnerability becomes a path to root. In plain English, it can turn a bad day into a much worse one.

That makes availability part of the security story.

During a vulnerability response, users need clear advisories, reachable update infrastructure, working mirrors, automation that does not fail mysteriously, and communication that tells them what is affected and what is not. If the front door is being pelted with packets while the building is also trying to distribute fire extinguishers, the fire extinguishers may still exist. That is good. But one is entitled to ask why everyone was expected to find them through a doorway currently occupied by vandals.

The DDoS did not need to be about Copy Fail for Copy Fail to matter.

## The Mirrors Held

This is where the APT mirror network deserves credit.

The detail that keeps tugging at me is not only what failed. It is what did not.

During the packet storm, the older APT mirror model appears to have done what distributed infrastructure is supposed to do. Not perfectly, not romantically, and certainly not with the sort of glossy product language that makes executives feel they have purchased the future in convenient quarterly installments. But it held well enough to remind us why distributed systems exist.

APT mirrors are not magic. They are ordinary infrastructure, maintained by people, universities, providers, institutions, and mirror operators who accept the unglamorous responsibility of keeping packages available. Ubuntu’s own documentation describes archive mirrors, release mirrors, country mirrors, Launchpad registration, sync requirements, and regular update expectations. Archive mirrors are expected to update every six hours. Release mirrors update every four hours or use push mirroring.

This is not glamorous architecture.

It is better than glamorous.

It is legible. It is boring. It is distributed. It is the sort of thing that survives trouble precisely because no single door has to remain open for the whole town to eat.

There is a quiet genius in boring infrastructure. Mirrors, sync jobs, package indexes, signatures, fallback hosts, and the ability to change sources are not the stuff of keynote demos. They are not sleek. They are not especially charismatic. But when the weather turns hostile, charisma is a poor substitute for redundancy.

The old mirrors behaved like infrastructure.

That matters.

## The Store Becomes the Chokepoint

This is where Snap comes back into the conversation.

The criticism of Snap has often been treated as ordinary Linux tribalism, and to be fair, Linux tribalism is one of the world’s most renewable energy sources. But beneath the shouting there has always been a serious architecture question.

A software distribution model is not only a packaging choice. It is a trust model. It is an availability model. It is a governance model.

Who controls the store?
Who reviews submissions?
Who decides what is verified?
Who operates the infrastructure?
What happens when that infrastructure is unavailable?
What alternatives exist for users, enterprises, or distributions that do not want their operating model tied so tightly to one company’s services?

Snapcraft’s own documentation describes the official Snap Store as hosted and curated by Canonical. That may be perfectly sensible for many use cases. Centralization can bring benefits: consistency, review processes, publisher identity, simplified distribution, automatic updates, and a more controlled user experience.

But convenience has a habit of putting on a nicer jacket and returning as dependency.

That is the uncomfortable comparison with APT mirrors.

APT’s older model assumes alternate paths. Snap’s public-store model assumes a central service. Those are different philosophies, not just different technologies.

The DDoS did not create that difference. It merely removed some of the polite fog around it.

## Open Source Is Not Automatically Resilient

One of the lazier arguments in technology is that open source is automatically resilient because the code is open.

I like open source. I prefer it whenever practical. I think it is one of the great achievements of modern technical culture. It gives users, developers, researchers, and institutions an ability to inspect, modify, preserve, and improve software in ways closed ecosystems often resist.

But openness of source code is not the same thing as resilience of the operating model.

A system can be open and still centralized.
It can be transparent in one layer and opaque in another.
It can publish code while concentrating distribution through a small number of chokepoints.
It can call itself community-oriented while quietly making the community dependent on infrastructure it does not control.

The question is not only, “Can I read the code?”

The question is also:
Can I get the software?
Can I verify it?
Can I update it?
Can I route around failure?
Can I mirror what matters?
Can the system degrade gracefully when the world becomes impolite?

Because the world will become impolite. It has a schedule.

## Open Source in a Political World

There is another piece here, and it is easy to miss if one thinks of Linux distributions as mere technical artifacts.

Open source does not live in a monastery.

It lives in the world. And the world contains botnets, proxies, criminal markets, state-aligned actors, hacktivists, bored teenagers, grievance politics, sanctions, wars, extortion attempts, and people who believe civilization is best improved by sending junk traffic at package infrastructure.

Ubuntu, Debian, Fedora, Arch, Alpine, Red Hat, SUSE, and the rest are not just operating systems in the abstract. They are parts of the modern technical commons. They support cloud workloads, developer machines, CI/CD systems, laboratories, classrooms, factories, home servers, small businesses, and governments. They are infrastructure in the broad civic sense.

That means they are now part of the geopolitical weather.

A DDoS against Canonical is not just a nuisance. It is a reminder that open-source infrastructure is also strategic infrastructure, and strategic infrastructure attracts strategic stupidity.

Sometimes the stupidity wears a uniform. Sometimes it wears an ideology. Sometimes it wears a Discord handle and sells DDoS-as-a-service to people whose moral development peaked somewhere between “found a booter panel” and “learned to spell operational security incorrectly.”

But the effect is the same. Systems we rely on are placed under pressure, and their hidden assumptions become visible.

## Why This Pushes Me Toward Fedora or Debian

This incident pushes me, at least emotionally, a little farther from Ubuntu and a little closer to Fedora or Debian.

Not because Fedora or Debian are magic kingdoms where packets arrive on horseback bearing constitutional rights. They have their own tradeoffs, politics, rough edges, governance disputes, maintenance burdens, and software choices capable of ruining a Saturday.

But they feel different in the areas that now matter more to me.

Debian appeals to the part of me that wants infrastructure to be boring in the way a good bridge is boring. It is conservative, widely mirrored, deeply rooted in the free software tradition, and less inclined to make the user feel gradually enrolled into a corporate product strategy.

Fedora appeals to the part of me that wants modern Linux, strong engineering, upstream alignment, and a desktop experience that does not revolve around Canonical’s preferred packaging future. Fedora is not neutral ground. It has Red Hat’s shadow over it, and anyone pretending otherwise is selling something. But the tradeoffs feel different.

Ubuntu still has strengths. It remains useful. It remains familiar. It remains one of the easiest distributions to recommend to many people. I am not throwing it into the sea.

But trust is not only built by being useful.

Trust is built by making the user comfortable with the tradeoffs.

And this incident made me less comfortable.

## The Infrastructure We Forgot to Question

The lesson here is not that Ubuntu is doomed, or that Snap is evil, or that everyone should reinstall their laptops before dinner.

The lesson is simpler and more durable: open-source resilience is not guaranteed by open code alone. It depends on the design of the whole system around the code.

It depends on distribution.
It depends on governance.
It depends on mirrors.
It depends on update paths.
It depends on incident communication.
It depends on whether users and administrators have alternate routes when the main road is blocked by a political parade of garbage packets.

A system can be open and still centralized. It can be convenient and still brittle. It can be widely trusted and still depend on infrastructure whose failure reveals assumptions nobody wanted to inspect too closely.

That is the part worth taking seriously.

Canonical’s DDoS did not prove that Ubuntu is broken. It did not prove that Snap is the end of civilization, though I recognize that some corners of the Linux internet will continue their liturgical dance on that subject with or without evidence.

What it did prove is more useful.

It proved that architecture has a memory. The older APT mirror model remembered a world where distribution needed redundancy. The newer centralized services remembered a world where convenience, identity, review, and control could be concentrated in a store.

Both worlds have lessons.

But when the weather turned political, the old mirrors looked wiser than they had the day before.

And that is enough to make a man reconsider his assumptions.

## Sources

[^canonical-ddos]: Canonical, “Update concerning DDOS attack on Canonical and Ubuntu,” Ubuntu Community Hub, May 2026. https://discourse.ubuntu.com/t/update-concerning-ddos-attack-on-canonical-and-ubuntu/81482

[^tomshardware-ddos]: Bruno Ferreira, “Canonical under sustained DDoS attack as Ubuntu 26 releases — Iranian group 313 Team claims responsibility,” Tom’s Hardware, May 1, 2026. https://www.tomshardware.com/tech-industry/cyber-security/canonical-under-sustained-ddos-attack-as-ubuntu-26-releases-iranian-group-313-team-claims-responsibility

[^register-ddos]: Connor Jones, “Pro-Iran crew turns DDoS into shakedown as Ubuntu.com stays down,” The Register, May 1, 2026. https://www.theregister.com/security/2026/05/01/pro-iran-group-turns-ubuntu-ddos-into-shakedown/5224575

[^ubuntu-mirrors]: Ubuntu Project Documentation, “Mirrors.” https://documentation.ubuntu.com/project/release-team/mirrors/

[^copy-fail-ubuntu]: Luci Stanescu, “Fixes available for CVE-2026-31431 (Copy Fail) Linux Kernel Local Privilege Escalation Vulnerability,” Canonical Ubuntu Blog, April 30, 2026. https://ubuntu.com/blog/copy-fail-vulnerability-fixes-available

[^snap-store]: Snapcraft documentation, “Snap publishing process.” https://documentation.ubuntu.com/snapcraft/latest/explanation/snap-publishing-process/
