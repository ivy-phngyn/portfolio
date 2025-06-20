---
layout: post
title: Prometheus Monitoring Stack
permalink: /proj05
---

In this project, I configured a monitoring stack with Prometheus to send out alerts in case our home servers go down.
With lots of documentation online, it was not hard to set up very quickly. I think the most tedious element was getting the data to export from various systems, 
as Prometheus has a very specific data format it can read.

This monitoring stack is in use for 15 servers within a home environment. It was very needed, since there was no prior monitoring set up in the past.
We would just try to access the server and realize it was down, or a user would notify us of the downtime.
At least now we know if the servers are down, and can act on it promptly!

As a next step, I am in the process of configuring Grafana to visualize the data metrics as well. It's been a very fun process so far, and I'm very glad the monitoring set up 
can help us out with our server environment.
