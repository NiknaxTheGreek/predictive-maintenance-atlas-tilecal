# Predictive Maintenance for the ATLAS Tile Calorimeter

Technical report based on the MSc dissertation **“Alert Signal Classification and Prediction Using Natural Language Processing for the Tile Calorimeter of ATLAS.”**

The report investigates whether archived ATLAS Tile Calorimeter (TileCal) Detector Control System (DCS) alarm logs can provide a predictive-maintenance layer in addition to their existing monitoring and protection role. Semi-structured alarm text is converted into detector-aware spatial and temporal datasets using targeted NLP and rule-based extraction, followed by LSTM-based alarm-count forecasting and dominant alarm-type classification.

## Report

**[Predictive_Maintenance_ATLAS_TileCal_Report_FINAL_v2.pdf](./Predictive_Maintenance_ATLAS_TileCal_Report_FINAL_v2.pdf)**

The current report is a concise 10-page technical version of the MSc work, with the methodology, hyperparameter optimisation, principal figures and quantitative results retained.

## Workflow

The analysis follows three linked stages:

1. **Alarm preprocessing and information extraction** — select Error-level DCS alarms, normalise alarm text, extract TileCal partition/hardware/module information and consolidate alarms into five classes: ALERT, EMR, NO CONNECTION, NO TOGGLE and TRIPPED.
2. **Temporal dataset construction** — convert the structured alarms into module-level alarm-count time series for forecasting and partition-level sequences for dominant alarm-type classification.
3. **Model-ready preprocessing and LSTM modelling** — preserve chronological order, scale from the training portion, generate sliding-window sequences, tune the LSTM models and evaluate forecasting and multiclass classification performance.

## Main results

- TileCal alarm activity was strongly spatially non-uniform across partitions and modules.
- LSTM alarm-count forecasting produced MAPE values of approximately **12.8–22.9%** across the four selected forecasting cases.
- The raw dominant-alarm classifier achieved **88% accuracy**, but performance was strongly affected by class imbalance.
- After chattering-alarm reduction, accuracy was **75%** while macro-F1 improved from **0.27 to 0.57**, giving a more informative view of minority alarm classes.
- The LBA forecasting result is treated cautiously because overlapping sequences near the chronological split reduced independence between training and evaluation samples.

## Scope and interpretation

This is a **proof-of-concept predictive-maintenance study**, not a deployed ATLAS operational system. The results demonstrate that historical detector-control alarm archives contain exploitable spatial and temporal structure, while limited sample sizes, class imbalance, validation design and the absence of live DCS testing constrain operational conclusions.

## Data availability

The underlying ATLAS/TileCal DCS alarm data are not released in this repository. The report presents derived statistics, methodology and study results without publishing the operational alarm dataset.

## Author

**Nicholas Perikli**  
University of the Witwatersrand, Johannesburg, South Africa

## Research context

The work combines high-energy-physics detector operations with NLP, time-series modelling and predictive maintenance. It builds on earlier machine-learning research by the author in COVID-19 vaccine-hesitancy and Mpox stance detection before transferring those methods to semi-structured detector-control alarm logs.

## Citation

If you use or discuss this work, please cite the technical report and/or the associated MSc dissertation. A formal arXiv citation can be added here if the report is deposited on arXiv.
