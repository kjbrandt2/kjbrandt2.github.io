---
layout: post
title: "IoT Botnets, DDoS, and the Device Governance Problem"
---

The recent takedown of four large IoT botnets is a useful reminder of an old truth: a machine does not care whose side it is on. It will obey whoever holds the leash.

Authorities in the United States, Canada, and Germany disrupted infrastructure tied to four botnets called Aisuru, Kimwolf, JackSkid, and Mossad. The official story says those botnets compromised more than three million connected devices and were used to drive DDoS attacks of extraordinary scale.

That sounds like a cyber story. It is not. Not really.

It is a governance story.

No sorcery was required. No death ray from Mars. The machinery was already here, plugged in, trusted, and humming along in offices, homes, field sites, and closets no one has opened in months. Routers. Cameras. Boxes with blinking lights. Cheap, connected, and forgotten. The attackers did not invent an army. They conscripted one.

That is the part worth your attention.

## What matters here

The interesting question is not how many devices were taken over. The interesting question is how many devices in your own environment could be.

### 1. Do you know which devices can become someone else’s infrastructure?

Most organizations think in categories that make them comfortable. Servers matter. Laptops matter. The little appliance in the corner does not matter until it does.

But if a device is connected, reachable, weakly managed, and rarely patched, then it is not a harmless convenience. It is a latent liability. It may sit quietly for months, doing its small assigned duty, until someone else decides it has a more interesting purpose.

A machine with no owner is still owned. Just not by you.

### 2. Are IoT and edge devices governed like real production assets?

There is a common superstition in operations: if something is small, cheap, or boring, it must also be low-risk. That is nonsense.

A camera does not become safe because it is boring. A router does not become harmless because nobody talks about it in steering committee meetings. An Android box does not become trustworthy because Finance never heard of it.

If the device is connected, it needs the same old unglamorous disciplines that keep everything else from becoming a fire: ownership, lifecycle control, patching, visibility, retirement. If those are absent, then you are not running a system. You are running a wish.

Luck is not a control.

### 3. Can you tell when “small devices” start behaving like attack infrastructure?

The official account says these botnets launched hundreds of thousands of attacks and caused real financial harm. That means the signal was there. The question is whether anyone who was responsible could see it in time, and whether they knew what they were looking at when they did.

For most teams, that comes down to a few unromantic questions:

- Can you see internet-exposed devices clearly?
- Do you know what normal outbound behavior looks like?
- Will anyone notice when one of these things starts speaking in a foreign tongue at machine speed?
- Is there a named human being who owns the problem when that happens?

Most failures of this kind are not failures of intelligence. They are failures of housekeeping.

### 4. Is DDoS resilience treated as a business-continuity issue?

Another common mistake is to hand DDoS off to the network team and call it a day, as though a flood of malicious traffic were only a technical inconvenience.

It is not. It is a continuity problem.

When systems are overwhelmed, the real questions are not abstract:

- Which services must remain reachable?
- Which dependencies break first?
- What can be degraded safely?
- Who talks to customers, partners, and internal teams when normal channels are under strain?

At sufficient scale, DDoS stops being a nuisance and starts becoming a test of whether leadership understands its own business.

## The practical takeaway

The recent disruption of these botnets is good news. It is also temporary news.

The underlying condition remains the same: the world is full of insecure, weakly governed connected devices, and adversaries have shown again and again that they are happy to put them to work.

So the useful question is not whether the government disrupted this batch.

The useful question is this:

**Which connected devices in your environment are important enough to inventory, patch, monitor, and retire deliberately, and which ones are still running on neglect and optimism?**

If the answer is vague, then the danger is not hypothetical. It is merely waiting its turn.

## A few useful checks

- Identify every internet-facing and remotely manageable IoT or edge device
- Assign a real owner to each device class
- Confirm patch responsibility and firmware hygiene
- Remove default credentials and weak remote access paths
- Baseline outbound behavior for non-traditional devices
- Alert on unusual traffic, scanning, or command patterns
- Tie DDoS response to business priorities, not just technical procedures
- Hold third-party and field-deployed devices to the same standards as internal ones

The larger point is simple enough for a child, which is one reason adults tend to miss it:

**A device fleet becomes a security problem long before it becomes a headline.**
