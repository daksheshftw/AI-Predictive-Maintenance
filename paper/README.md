<div align="center">

# Research Manuscript

## Machine Learning-Based Vibration Fault Detection in Rolling Element Bearings

**A Leakage-Aware Comparison with Conventional RMS Thresholding Under Variable Operating Conditions**

**Dakshesh Das**  
Mechanical Engineering + Artificial Intelligence  
29 September 2026

</div>

---

## Abstract

Unexpected rolling-element bearing failures can cause downtime, secondary damage, and unnecessary maintenance cost. This study compares conventional root-mean-square (RMS) vibration thresholding with classical machine-learning methods in two complementary phases.

Phase I uses a 16-recording Case Western Reserve University (CWRU) subset containing normal, ball, inner-race, and outer-race conditions across 0-3 hp. Normal drive-end recordings were standardized from 48 kHz to 12 kHz, fault recordings were analyzed at 12 kHz, and all signals were segmented into non-overlapping one-second windows, producing 155 feature vectors. Under leave-one-load-out evaluation, the conventional RMS threshold achieved a mean-fold balanced accuracy of 0.8750 and produced five false alarms when 0 hp was held out. Logistic regression and random forest each achieved 1.0000 mean-fold balanced accuracy for binary detection, while XGBoost achieved 0.9958. For four-class diagnosis, random forest achieved 1.0000 mean balanced accuracy, compared with 0.9750 for XGBoost and 0.9313 for logistic regression.

Phase II uses NASA IMS run-to-failure data to test chronological early-anomaly warning. With a fixed analysis protocol using a 24-hour healthy baseline, six time-domain features, RobustScaler, an RBF One-Class SVM, a 99th-percentile baseline anomaly threshold, and three-consecutive-exceedance persistence, IMS Test 2 Bearing 1 produced an anomaly alarm at 84.67 monitored hours versus an RMS alarm at 89.00 hours, a 4.33-hour lead. Across 12 Test 2 sensitivity configurations, the One-Class SVM warned earlier than RMS in nine and at the same time in three; Isolation Forest warned later in all 12.

Applying the fixed protocol without retuning to four IMS Test 1 sensor trajectories produced apparent anomaly leads of 91.53-210.58 monitored hours. Alarm-credibility diagnostics showed variable persistence, so these large leads are interpreted as early anomaly indications rather than remaining-useful-life predictions.

The combined results show that multivariate machine learning improved robustness over a fixed RMS threshold on the selected CWRU benchmark and can produce earlier anomaly alarms on IMS, while also demonstrating that early warning is highly sensitive to calibration choices and must be interpreted separately from fault classification and from true failure-time prediction.

**Keywords:** predictive maintenance · rolling element bearing · vibration analysis · machine learning · fault diagnosis · RMS threshold · random forest · XGBoost · One-Class SVM · early anomaly warning · data leakage

---

## Research Questions

**RQ1.** Can machine-learning-based vibration analysis distinguish healthy and faulty drive-end bearings more reliably than a conventional RMS vibration threshold across the selected CWRU operating conditions?

**RQ2.** How do motor load and rotational speed affect the robustness of the conventional threshold and the machine-learning models?

**RQ3.** Which vibration features contribute most strongly to model decisions and are those features mechanically interpretable?

**RQ4.** On a true run-to-failure dataset, can an ML-based health indicator produce an earlier persistent warning than a conventional RMS threshold, and how stable is that warning under alternative calibration choices?

---

## Manuscript Scope

The completed manuscript covers:

- condition-based and predictive-maintenance background
- rolling-element bearing fault mechanics
- CWRU dataset selection and sampling-rate quality control
- one-second vibration windowing and interpretable feature engineering
- conventional RMS thresholding
- Logistic Regression, Random Forest, and XGBoost fault detection/diagnosis
- leakage-aware leave-one-load-out evaluation
- feature ablation and interpretability
- NASA IMS chronological run-to-failure analysis
- One-Class SVM early-anomaly warning
- sensitivity analysis and alarm-credibility checks
- limitations and engineering interpretation

The manuscript deliberately separates **fault diagnosis**, **early anomaly detection**, and **remaining-useful-life prediction** rather than treating them as interchangeable claims.

---

## Headline Findings

| Experiment | Result |
|---|---|
| CWRU RMS threshold | 0.8750 mean-fold balanced accuracy |
| CWRU binary Logistic Regression | 1.0000 mean-fold balanced accuracy |
| CWRU binary Random Forest | 1.0000 mean-fold balanced accuracy |
| CWRU binary XGBoost | 0.9958 mean-fold balanced accuracy |
| CWRU multiclass Random Forest | 1.0000 mean balanced accuracy |
| IMS Test 2 One-Class SVM | +4.33 h apparent anomaly lead vs RMS |
| IMS Test 2 sensitivity | SVM earlier in 9/12 settings; same in 3/12 |
| IMS Test 1 trajectories | +91.53 to +210.58 h apparent anomaly lead vs RMS |

> Large IMS Test 1 leads are reported as **apparent early-anomaly signals**, not verified failure predictions or RUL estimates.

---

## Repository Evidence

The numerical claims in the manuscript can be traced to the repository's saved experimental outputs:

- [Master results](../results/FINAL_master_results.csv)
- [Key findings](../results/FINAL_key_findings.csv)
- [Frozen Phase II protocol](../results/FINAL_phase2_frozen_protocol.csv)
- [Phase I feature dataset](../results/phase1_feature_dataset.csv)
- [IMS Test 1 validation](../results/phase2_test1_validation.csv)
- [IMS Test 2 sensitivity analysis](../results/phase2_test2_sensitivity_full.csv)
- [Research figures](../figures/)
- [CWRU analysis notebook](../notebooks/01_cwru_fault_detection.ipynb)
- [IMS workflow notebook](../notebooks/02_ims_early_warning.ipynb)

---

## Citation

If referencing this work, please cite:

> Das, Dakshesh. *Machine Learning-Based Vibration Fault Detection in Rolling Element Bearings: A Leakage-Aware Comparison with Conventional RMS Thresholding Under Variable Operating Conditions.* Comprehensive Research Manuscript, 29 September 2026.

See the repository's [CITATION.cff](../CITATION.cff) for machine-readable citation metadata.
