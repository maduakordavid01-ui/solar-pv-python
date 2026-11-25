# Solar PV Python: 5 MWp plant design & simulation

Python rebuild of my 5 MWp grid-connected PV plant design for Montpellier, France, from real PVGIS weather data to annual energy yield.

📐 **Electrical design files** (SLD, report, energy analysis): [5MWp_Solar_PV_Electrical_Design_Portfolio](5MWp_Solar_PV_Electrical_Design_Portfolio/)

**Author:** Maduakor Uchechukwu David, MSc Energy for Solar Buildings and Cities (Université Savoie Mont Blanc, 2026)
[LinkedIn](https://linkedin.com/in/david-maduakor)

## Key results
| | |
|---|---|
| Plant | 9,152 × JA Solar 550 Wp · 16 × Sungrow SG250HX · **5.03 MWp DC / 4 MW AC** |
| In-plane irradiation | 2,007 kWh/m²/year (35° south) |
| Annual energy | **8,214 MWh** · 1,632 kWh/kWp · PR ≈ 81 % |
| Clipping | ≈ 0.2 % at DC/AC 1.26 |
| Orientation | 99.7 % of the optimum (40° south) |

## Notebook contents (`01_my_pv_simulation.ipynb`)
1. **Solar resource:** PVGIS TMY download, statistics, monthly irradiation, day × hour heatmap
2. **String sizing:** cold Voc / hot Vmp / MPPT current checks against datasheets
3. **POA & cell temperature:** Perez transposition, SAPM thermal model
4. **Energy simulation:** PVWatts DC, system losses, inverter clipping, comparison with PVGIS
5. **DC/AC ratio study:** clipping and marginal yield from 1.0 to 1.6
6. **Tilt & azimuth study:** 169 orientations, optimum and 98 % zone

## Notebook 2: AI forecasting for battery control (`02_my_ai_forecasting.ipynb`)
Grenoble office building · 400 kWp PV · 300 kWh battery · PVGIS hourly 2019–2020

| | |
|---|---|
| Day-ahead forecasts (gradient boosting) | PV nRMSE 20.5 % · demand 16.4 % · 74 % / 68 % skill vs persistence |
| Explainability | Permutation importance + ablation test |
| Battery control | 5 strategies compared on an unseen year |
| Result | Bill 135 → 45 k€/yr. ML control matches the perfect forecast with −1.1 t CO₂ vs blind charging |

## Track A: 500 kWp rooftop PV, design-office deliverables
Industrial flat roof · 900 × 550 Wp · 5 × 100 kW string inverters · self-consumption
- **AutoCAD:** roof layout (strings, inverters, dimensions) and single-line diagram → [`TrackA_500kWp/`](TrackA_500kWp/)
- **Python calculation note** (`03_calculation_note_500kWp.ipynb`), checks per UTE C 15-712-1 / NF C 15-100:
  - DC: Voc max 821 V ≤ 1,100 V, no string fuses needed
  - DC cables: 4/6/10 mm², every string ≤ 1 % drop, losses 0.70 %
  - AC: Q1–Q5 160 A, QG 800 A, total drop 1.45 %
  - Insight: central inverters would cut DC cable by 44 %

## Tools
Python · pvlib · pandas · NumPy · matplotlib · scikit-learn · Jupyter · VS Code · Git · AutoCAD

## Run it
    pip install -r requirements.txt
then open the notebook and click **Run All**. Weather data is downloaded live from PVGIS (internet needed).