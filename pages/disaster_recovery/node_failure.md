---
title: [elephant]
tags: 
keywords: tbd
last_updated: tbd
summary: "blerg"
sidebar: mydoc_sidebar
---
# Node failure

ThoughtSpot uses replication of stored data. When a disk goes bad, ThoughtSpot continues to operate.

To support high availability, your ThoughtSpot instance must have at least three nodes. In a three or more node system, if one node fails, its services will be distributed to the other nodes. The failover is automatic. However, when a node fails, you should contact ThoughtSpot Support about replacing the node when possible.

A node is considered to have failed when one or more of these conditions occur:

-   Two or more disks have failed.
-   SSD has failed.
-   Memory failure.
-   Another hardware component has failed \(networking, motherboard, power supplies\).

## Symptoms

You should suspect node failure if you observe these symptoms:

-   Performance degrades significantly.
-   You receive alert emails beginning with WARNING or CRITICAL, that describe problems with one of the nodes not running.
-   A node does not come up upon booting or rebooting the system.

If you notice these symptoms, contact ThoughtSpot Support.

## Node replacement

Node replacement is done on site by ThoughtSpot Support. You will need to schedule a maintenance window, since some downtime is required. For more information, please contact ThoughtSpot Support.

**Parent topic:** [About disaster recovery](../../disaster_recovery/disaster_recovery/about_disaster_recovery.html)
