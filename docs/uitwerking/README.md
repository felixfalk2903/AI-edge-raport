---
title: Uitwerking
---

# Uitwerking

## Accelerometer code

We schrijven de code van de workshop op de accelerometers door dezelfde stappen te volgen van de [workshop](https://ai-edge-workshop.netlify.app/).

Via MBED compilen we de code en zetten we deze over via het STM bordje naar de accelerometer.

![setup](./assets/setup.png)

Na de code correct over te zetten, kunnen we de X, Y & Z waarden van de accelerometer uitlezen via Putty.

![Putty](./assets/putty.png)

Deze data zenden we naar de [Edge Impulse website](https://www.edgeimpulse.com/) via de [edge-impulse-data-forwarder](https://ai-edge-workshop.netlify.app/02-ab-writing/04-connecting-a-device/), na de device te registreren op Edge Impulse met de data-forwarder kunnen we beginnen met samplen.

![sampling](./assets/sampling.png)

We samplen 2 categorieën: Empty-seat en Seat-fill.
