# Project 4: Predictive Analytics Case Study – Google Maps Traffic Prediction

**Course:** DSC 630 – Predictive Analytics (Week 5)

## Overview
A written case study on how Google Maps predicts traffic and estimates travel time (ETA). The hard part isn't measuring current traffic. It's predicting what traffic will be like later in the trip.

## Contents
- **Problem and importance:** congestion costs time, fuel and productivity. Predicting it lets navigation be proactive instead of reactive.
- **Data sources:** anonymized, aggregated GPS location data from phones, historical traffic patterns, user reports (accidents, closures) and government road data.
- **Data preparation:** aggregating data across users, removing anomalies, normalizing speed and time measurements, and grouping by time of day, day of week and season.
- **Modeling:** supervised models trained on historical speeds per road segment, combined with real-time conditions. Graph neural networks (GNNs) represent how traffic on connected roads affects each other.
- **Evaluation:** ETA accuracy (Google reports accurate ETAs for over 97% of trips), plus route efficiency and user satisfaction.
- **Implementation:** predictions are built into the app. Routes are recommended when the trip starts and updated as it goes.

## Files
- `Anish_Samuel_Week5_Assignment5.pdf`: case study (PDF)
- `Anish_Samuel_Week5_Assignment5.docx`: case study (Word)
- `Anish_Samuel_Week5_Assignment5.ipynb.docx`: alternate Word version

## Skills shown
Explaining a production ML system end to end: problem framing, data sourcing, preprocessing, model choice and evaluation metrics.
