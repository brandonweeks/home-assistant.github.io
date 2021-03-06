---
layout: page
title: "Nest Thermostat"
description: "Instructions how to integrate Nest thermostats within Home Assistant."
date: 2015-03-23 19:59
sidebar: true
comments: false
sharing: true
footer: true
logo: nest_thermostat.png
ha_category: Climate
---


The `nest` climate platform let you control a thermostat from [Nest](https://nest.com).

<p class='note'>
You must have the [Nest component](/components/nest/) configured to use those thermostats.
</p>

To set it up, add the following information to your `configuration.yaml` file:

```yaml
climate:
  platform: nest
```

<p class='img'>
  <img src='{{site_root}}/images/screenshots/nest-thermostat-card.png' />
</p>

