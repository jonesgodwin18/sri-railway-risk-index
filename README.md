# Safety Risk Index (SRI) for Railway Insurance Pricing

A validated Safety Risk Index that converts predictive railway safety analytics into insurer-grade risk scores for risk-adjusted premiums and performance-linked insurance.

**IIT Roorkee E-Summit'26 | Case partner: Kernex Microsystems**
**Team Product Saviours (BIT Mesra):** Aarav Singh, Rudra Baldaniya, Varun Singhal, Jones G

---

## The Problem

Consequential train accidents in India have fallen ~94% over the past decade, yet insurance premiums remain largely static. Safety is **unpriced** because:

- Safety data is fragmented across track, signaling, rolling stock, and operations
- There is no standardized risk signal that insurers can compare across assets and routes
- Data is internally generated and lacks independent validation

Insurers therefore fall back on historical loss data instead of rewarding prevention.

## The Solution: Safety Risk Index (SRI)

A standardized, time-based **0-100 risk score** per asset, route, and zone. It aggregates only safety signals that meet actuarial criteria and is expressed as risk bands, not raw model outputs.

SRI is **not** a real-time safety control system, an AI decision engine, or a replacement for engineering judgment.

## How the Score Works

1. **Signal collection:** fault frequency, near misses, sensor anomalies, maintenance lags
2. **Model weighting:** logistic regression / ensemble ML plus rules
3. **Composite score:** weighted aggregation into a 0-100 index

| SRI Score | Tier | Action | Premium Adjustment |
|-----------|--------|-------------------|--------------------|
| 0-40 | Low | Monitor | -15% discount |
| 41-70 | Medium | Inspect, escalate | No change |
| 71-100 | High | Immediate action | +20% surcharge |

```
Adjusted Premium = Base Premium x (1 + Risk Adjustment Factor)
```

*Figures are illustrative.*

## Architecture

| Layer | Purpose | Tech |
|-------|---------|------|
| Data ingestion | Loco IoT, FOIS, COA, maintenance logs | Kafka, Spark ETL |
| Scoring | Real-time scoring, trend analysis, explainability | Flink, Spark, rules + ML |
| Storage and API | Dashboards and insurer access | Redis, BigQuery, REST |
| UI and reporting | Ops, Insurance, Governance views | Role-based dashboards |

## Validation and Governance

- **Technical:** version-controlled models, checksum-validated data, SHAP explanations for every score
- **Statistical:** target AUC-ROC > 0.87, false positives < 12%, quarterly K-fold calibration
- **Institutional:** immutable score ledger, semi-annual audits, alignment with IRDAI and Ministry of Railways standards

## Deployment Roadmap

| Phase | Timeline | Focus |
|-------|----------|-------|
| 1. Pilot | Months 0-3 | 2 corridors, 1 insurer, 1 loco division |
| 2. Validation | Months 4-8 | Accuracy audit, insurer integration |
| 3. National scale | Months 9-18 | All major zones |
| 4. Insurance pooling | Year 2+ | Performance-linked coverage |

## Limitations

- Inconsistent sensor coverage, especially on rural lines
- Needs ongoing validation as infrastructure evolves
- Requires IRDAI buy-in and standardization

