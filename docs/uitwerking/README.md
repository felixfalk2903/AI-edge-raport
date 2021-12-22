---
title: Uitwerking
---

# Uitwerking

## Accelerometer code

We schrijven de code van de workshop op de accelerometers door dezelfde stappen te volgen van de [workshop](https://ai-edge-workshop.netlify.app/).

Via MBED compilen we de code en zetten we deze over via het STM bordje naar de accelerometer.

![setup](./assets/setup.png)

Na de code correct over te zetten, kunnen we de X, Y & Z waarden van de sensor uitlezen via Putty.

![Putty](./assets/putty.png)

Deze data zenden we naar de [Edge Impulse website](https://www.edgeimpulse.com/) via de [edge-impulse-data-forwarder](https://ai-edge-workshop.netlify.app/02-ab-writing/04-connecting-a-device/), na de sensor te registreren op Edge Impulse met de data-forwarder kunnen we beginnen met samplen.

![sampling](./assets/sampling.png)

We hangen de sensor aan een stoelpoot en meten data op.

![seat](./assets/seat.jpg)

We samplen 2 categorieën: Empty-seat en Seat-fill.

Bij "Empty-seat" laten de stoel leeg. De metingen zullen dus ook lage waarden hebben.

![empty](./assets/empty.png)

Bij "Seat-filled" zitten we in de stoel waarbij we soms wat bewegen en soms stil zitten. De meting zullen dus hoge pieken hebben, deze pieken zijn plotse bewegingen.

![filled](./assets/filled.png)

We verzamelen meer dan een uur aan data.

![data](./assets/data.png)

We creeëren een model met de Impulse Design:

![model](./assets/model.png)

De Window size en Window increase werden automatisch ingesteld door de EON Tuner.

Na veel testen concludeerden we dat een Spectral Analysis het beste resultaat gaf. Daarna sturen we deze features door een Keras Neuraal Netwerk, dit Neuraal Network klassificeerd op de 2 klasses: "Empty-seat & "Seat-filled", dit zijn dan ook de 2 mogelijke outputs.