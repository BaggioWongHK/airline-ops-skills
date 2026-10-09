---
name: airline-disruption-analysis
description: General method for analyzing airline operational disruptions (weather, ATC, typhoons) from flight-level data - classifying cancellations and delays with IATA delay codes, separating primary from reactionary delay, and structuring a disruption timeline. Use when analyzing what happened during an airline disruption.
---

# Airline disruption analysis

A general, airline-agnostic method. Pair it with your airline's own cost model and reporting
template if you have them.

## 1. Build the timeline

- Define the disruption window (for example, the hours a typhoon signal was in force).
- For each flight, use the time it touches the affected airport: departure time for flights out,
  arrival time for flights in.
- Plot scheduled movements per hour against the window to show the shape of the disruption.

## 2. Classify every affected flight

Use IATA delay code groups:

| Codes | Meaning |
|---|---|
| 71 | Weather at departure station |
| 72 | Weather at destination station |
| 73 | Weather en route or at alternate |
| 77 | Ground handling impaired by weather |
| 93 | Reactionary: aircraft rotation, late arrival of the aircraft from a previous flight |

Report cancellations and delays separately. Weather codes (71-77) are **primary** causes; 93 is
**reactionary**, the knock-on effect after the weather has passed.

## 3. Measure the impact

- Cancelled flights and passengers affected, split by direction (out of / into the hub).
- Operated flights delayed by reactionary causes, and total reactionary delay minutes.
- Recovery time: from the end of the disruption window to the first hour with no reactionary delay.

## 4. Questions to answer in the write-up

- How much was cancelled, and when were those decisions made relative to departure?
- How long did recovery take after the window closed?
- What would have changed with earlier decisions?
