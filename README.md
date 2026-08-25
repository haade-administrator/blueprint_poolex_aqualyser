# 🏊 Poolex Aqualyser Multi - Home Assistant Integration & Blueprint

Ce dépôt contient le **Blueprint d'automatisation Home Assistant** pour le contrôleur d'électrolyse et de traitement d'eau **Poolex Aqualyser Multi**, basé sur les préconisations exactes du fabricant.

---

## 🚀 Importer le Blueprint dans Home Assistant / Import Blueprint to Home Assistant

Cliquez sur le bouton ci-dessous pour importer directement le blueprint d'automatisation dans votre instance Home Assistant :

[![my_homeassistant_import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fhaade-administrator%2Fblueprint_poolex_aqualyser%2Fblob%2Fmain%2Fpoolex_aqualyser_blueprint.yaml)

---

## ⚙️ Fonctionnement du Switch Fréquentation (Optionnel) / High Attendance Switch (Optional)

L'option **Switch Fréquentation / High Attendance Switch** est optionnelle :
- **Non renseigné ou positionné sur `OFF` (Par défaut)** : L'automatisation applique la fréquentation normale (ex: 8h chloration / 18h filtration à ≥28°C).
- **Positionné sur `ON`** : L'automatisation bascule en mode forte fréquentation (ex: 12h chloration / 24h filtration à ≥28°C, et Mode BOOST 24h à ≥30°C).

---

## 📊 Préconisations du Fabricant / Manufacturer Recommendations

### 🇫🇷 Français
Tableau d'ajustement du temps de filtration et de la durée de traitement (chloration) selon la température de l'eau :

| Température de l'eau | Temps de traitement | Temps de filtration |
| :--- | :--- | :--- |
| **10°C ≤ T° < 20°C** *(ou piscine couverte)* | 2h | 6h |
| **20°C ≤ T° < 25°C** | 4h | 10h |
| **25°C ≤ T° < 28°C** | 6h | 14h |
| **T° ≥ 28°C** *(Fréquentation normale / par défaut)* | 8h | 18h |
| **T° ≥ 28°C** *(Forte fréquentation)* | 12h | 24h |
| **T° ≥ 30°C** *(Forte fréquentation)* | 24h *(BOOST)* | 24h |

---

### 🇬🇧 English
Adjustment table for filtration duration and chlorination (treatment) time based on water temperature:

| Water Temperature | Treatment Duration | Filtration Duration |
| :--- | :--- | :--- |
| **10°C ≤ T° < 20°C** *(or covered pool)* | 2h | 6h |
| **20°C ≤ T° < 25°C** | 4h | 10h |
| **25°C ≤ T° < 28°C** | 6h | 14h |
| **T° ≥ 28°C** *(Normal attendance / default)* | 8h | 18h |
| **T° ≥ 28°C** *(High attendance)* | 12h | 24h |
| **T° ≥ 30°C** *(High attendance)* | 24h *(BOOST)* | 24h |

---

## 🛠️ Fichiers inclus / Included Files

- `poolex_aqualyser_blueprint.yaml` : Blueprint d'automatisation Home Assistant.
