---
layout: post
title: "IoT Botnets, DDoS, and the Device Governance Problem"
---

The recent federal disruption of four large IoT botnets is a reminder that DDoS is often a device-governance problem before it becomes a network problem.

The U.S. Justice Department said authorities in the United States, Canada, and Germany disrupted infrastructure used by four botnets named Aisuru, Kimwolf, JackSkid, and Mossad. According to the government, those botnets compromised more than three million IoT devices and were used in a series of major DDoS attacks, including attacks that reached roughly 30 terabits per second.

That headline matters, but the more useful takeaway is operational.

These botnets were not built on exotic infrastructure. They were built on ordinary connected devices such as routers, cameras, and other internet-facing systems that were easy to compromise, easy to scale, and easy to reuse. Krebs also notes that Aisuru emerged in late 2024, Kimwolf expanded rapidly in 2025, and researchers publicly documented Kimwolf’s propagation methods in January 2026. 

## What matters here

A few questions are more useful than the headline count of infected devices.

### 1. Do you know which connected devices can become someone else’s infrastructure?

The botnet story is not just about attackers. It is about unmanaged or poorly governed devices becoming part of an attack platform.

If a device can be reached, poorly maintained, or exposed through weak controls, it can become part of someone else’s DDoS capacity. That is as much an asset-governance issue as it is a security issue. 

### 2. Are IoT and edge devices governed like real production assets?

A router, camera, Android TV box, or field device may not feel as important as a server. In practice, large botnets keep proving the opposite.

If a device is connected, routable, remotely administered, or rarely patched, it needs ownership, lifecycle control, and a clear place in the asset inventory. Otherwise the organization is depending on luck. 

### 3. Can you tell when "small devices" start behaving like attack infrastructure?

The DOJ said the four botnets launched hundreds of thousands of DDoS attacks and that some victims suffered tens of thousands of dollars in losses and remediation costs. That means the operational signal was not subtle. The question is whether affected environments could see the signal in time.

For most teams, this comes down to:
- visibility into internet-exposed devices
- baseline behavior for outbound traffic
- alerting for unusual connections, scanning, or command patterns
- clear ownership when a non-traditional device needs investigation

### 4. Is DDoS resilience treated as a business-continuity issue?

The common mistake is to treat DDoS as a network team problem only.

At scale, DDoS is also a continuity question:
- which services must stay reachable
- what dependencies can fail first
- what fallback paths exist
- what customer, vendor, and internal communications happen during disruption

The larger the botnets get, the less useful it is to think about this as a purely technical nuisance. It becomes a resilience and prioritization problem.

## The practical takeaway

The recent botnet disruption is good news, but it does not solve the underlying issue.

The underlying issue is that insecure and weakly governed connected devices still provide cheap scale for attack operators. Researchers have been pointing to the same pattern for months: insecure IoT and consumer-connected devices are still an abundant supply chain for large DDoS activity.

A simple internal question is this:

**Which connected devices in our environment are treated as operationally important enough to inventory, patch, monitor, and retire deliberately, and which ones are still effectively unmanaged?**

If the answer is unclear, the risk is not theoretical.

## A few useful checks

- Identify all internet-facing and remotely manageable IoT or edge devices
- Confirm ownership and patch responsibility for each device class
- Review where default credentials, weak remote access, or unmanaged firmware still exist
- Baseline outbound behavior for non-traditional devices and alert on unusual activity
- Test whether DDoS response plans are tied to actual business priorities
- Review whether third-party or field-deployed devices are governed to the same standard as core internal systems

The broader point is simple:

**A device fleet becomes a security problem long before it becomes a headline.**
