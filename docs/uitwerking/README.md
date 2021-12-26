---
title: Uitwerking
---

# Uitwerking

## Sensor code

We schrijven de code van de workshop op de accelerometers door dezelfde stappen te volgen van de [workshop](https://ai-edge-workshop.netlify.app/).

Via MBED compilen we de code en zetten we deze over via het STM bordje naar de accelerometer.

![setup](./assets/setup.png)

## Sensor uitlezen

Na de code correct over te zetten, kunnen we de X, Y & Z waarden van de sensor uitlezen via Putty.

![Putty](./assets/putty.png)

## Sampling

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

## Neuraal Netwerk model

We creeëren een model met de Impulse Design:

![model](./assets/model.png)

De Window size en Window increase werden automatisch ingesteld door de EON Tuner.

Na veel testen concludeerden we dat een Spectral Analysis het beste resultaat gaf.

Daarna sturen we deze features door een Keras Neuraal Netwerk, dit Neuraal Network klassificeerd op de 2 klasses: "Empty-seat & "Seat-filled", dit zijn dan ook de 2 mogelijke outputs.

## EON Tuner

![EON](./assets/EON.png)

De EON Tuner zorgt ervoor dat we het meest optimaal neuraal netwerk verkrijgen.

![EON testing](./assets/EONtesting.png)

De EON Tuner test verschillende neurale netwerken met verschillende layer configuraties en zoekt de beste configuratie.

De EON Tuner geeft een aanbevolen configuratie voor het Neuraal Netwerk:

![EONmodel](./assets/EONmodel.png)

## Model testing

Na dit model te laten trainen met de data, testen we het model:

![ModelTest](./assets/ModelTest.png)

Tijdens het testen merkten we dat het model wel vrij accuraat de bezetting van stoel kon detecteren. Er kwamen wat inaccurate resultaten wanneer we ons best deden om zeer stil te zitten dat het model wat moeite had. We testen dan ook maar kleine momenten, mensen kunnen korte momenten stil zitten, maar op een langer termijn zal de persoon eens bewegen en dan zal het model wel de persoon detecteren.
