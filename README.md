# 🏊 Poolex Aqualyser Multi - Home Assistant Blueprint

Blueprint d'automatisation Home Assistant complet pour le **Poolex Aqualyser Multi**, basé sur les préconisations exactes du fabricant.

---

## 🚀 Importer le Blueprint / Import Blueprint

[![my_homeassistant_import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fhaade-administrator%2Fblueprint_poolex_aqualyser%2Fblob%2Fmain%2Fpoolex_aqualyser_blueprint.yaml)

---

## 📊 Préconisations du Fabricant / Manufacturer Recommendations

### 🌡️ Température / Traitement / Filtration

#### 🇫🇷 Français

| Température de l'eau | Temps de traitement | Temps de filtration |
| :--- | :--- | :--- |
| **10°C ≤ T° < 20°C** *(ou piscine couverte)* | 2h | 6h |
| **20°C ≤ T° < 25°C** | 4h | 10h |
| **25°C ≤ T° < 28°C** | 6h | 14h |
| **T° ≥ 28°C** *(Fréquentation normale)* | 8h | 18h |
| **T° ≥ 28°C** *(Forte fréquentation)* | 12h | 24h |
| **T° ≥ 30°C** *(Forte fréquentation)* | 24h *(BOOST)* | 24h |

#### 🇬🇧 English

| Water Temperature | Treatment Duration | Filtration Duration |
| :--- | :--- | :--- |
| **10°C ≤ T° < 20°C** *(or covered pool)* | 2h | 6h |
| **20°C ≤ T° < 25°C** | 4h | 10h |
| **25°C ≤ T° < 28°C** | 6h | 14h |
| **T° ≥ 28°C** *(Normal attendance)* | 8h | 18h |
| **T° ≥ 28°C** *(High attendance)* | 12h | 24h |
| **T° ≥ 30°C** *(High attendance)* | 24h *(BOOST)* | 24h |

---

### 🏊 Volume du Bassin / Pool Volume → Taux de Production / Production Rate

#### 🇫🇷 Français

| Taille du bassin | Taux de production minimal |
| :--- | :--- |
| ≤ 15 m³ | 20% |
| ≤ 30 m³ | 40% |
| ≤ 50 m³ | 60% |
| ≤ 60 m³ | 80% |
| > 60 m³ | 100% |

> Le volume du bassin est paramétrable dans le blueprint (slider 5-200 m³). Le taux de production est automatiquement calculé et appliqué à l'Aqualyser.

#### 🇬🇧 English

| Pool Size | Minimum Production Rate |
| :--- | :--- |
| ≤ 15 m³ | 20% |
| ≤ 30 m³ | 40% |
| ≤ 50 m³ | 60% |
| ≤ 60 m³ | 80% |
| > 60 m³ | 100% |

> Pool volume is configurable in the blueprint (slider 5-200 m³). The production rate is automatically calculated and applied to the Aqualyser.

---

### 💧 Dureté de l'Eau / Water Hardness → Inversion de Polarité / Polarity Reversal

#### 🇫🇷 Français

| Titre Hydrotimétrique (TH) | Temps d'inversion de polarité |
| :--- | :--- |
| TH < 30°f | 8h |
| TH < 40°f | 6h |
| TH < 50°f | 4h |
| TH ≥ 50°f | 2h |

> La dureté de l'eau est paramétrable dans le blueprint (slider 0-100 °f). L'intervalle d'inversion de polarité est automatiquement calculé et appliqué à l'Aqualyser.

#### 🇬🇧 English

| Water Hardness (TH) | Polarity Reversal Interval |
| :--- | :--- |
| TH < 30°f | 8h |
| TH < 40°f | 6h |
| TH < 50°f | 4h |
| TH ≥ 50°f | 2h |

> Water hardness is configurable in the blueprint (slider 0-100 °f). The polarity reversal interval is automatically calculated and applied to the Aqualyser.

---

## ⚙️ Switch Fréquentation (Optionnel) / High Attendance Switch (Optional)

### 🇫🇷 Français
L'option **Switch Fréquentation** est optionnelle :
- **Non renseigné ou `OFF` (Par défaut)** : Fréquentation normale (ex: 8h chloration / 18h filtration à ≥28°C).
- **`ON`** : Forte fréquentation (ex: 12h chloration / 24h filtration à ≥28°C, et Mode BOOST 24h à ≥30°C).

#### Comment créer l'entité dans Home Assistant :
**Paramètres** → **Appareils et services** → **Entrées (Helpers)** → **Créer une entrée** → **Interrupteur (Input boolean)** → nommer `Forte Fréquentation Piscine`.

### 🇬🇧 English
The **High Attendance Switch** is optional:
- **Not set or `OFF` (Default)**: Normal attendance (e.g. 8h chlorination / 18h filtration at ≥28°C).
- **`ON`**: High attendance (e.g. 12h chlorination / 24h filtration at ≥28°C, and 24h BOOST at ≥30°C).

#### How to create the entity in Home Assistant:
**Settings** → **Devices & Services** → **Helpers** → **Create Helper** → **Toggle (Input boolean)** → name it `Pool High Attendance`.

---

## 🔄 Fonctionnement des Déclencheurs / Trigger Logic

### 🇫🇷 Français
Le blueprint combine **deux déclencheurs** :
1. ⏰ **Heure quotidienne** : Lance le cycle de filtration chaque jour à l'heure configurée. Lit la température et calcule les durées.
2. 🌡️ **Franchissement de seuil** : Si la température franchit un seuil (10, 20, 25, 28, 30°C) en cours de journée, le cycle est **recalculé et relancé** avec les nouvelles durées.

### 🇬🇧 English
The blueprint combines **two triggers**:
1. ⏰ **Daily schedule**: Starts the filtration cycle daily at the configured time. Reads temperature and calculates durations.
2. 🌡️ **Threshold crossing**: If temperature crosses a threshold (10, 20, 25, 28, 30°C) during the day, the cycle is **recalculated and restarted** with new durations.

---

## 🛠️ Fichiers inclus / Included Files

- `poolex_aqualyser_blueprint.yaml` : Blueprint d'automatisation Home Assistant.
