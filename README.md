# 🏊 Poolex Aqualyser Multi - Home Assistant Blueprint

Blueprint d'automatisation Home Assistant complet pour le **Poolex Aqualyser Multi**, basé sur les préconisations exactes du fabricant.

---

## 🚀 Importer le Blueprint / Import Blueprint

[![my_homeassistant_import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fhaade-administrator%2Fblueprint_poolex_aqualyser%2Fblob%2Fmain%2Fpoolex_aqualyser_blueprint.yaml)

---

## ❄️ Sécurité intempérie / Weather Safety

### 🇫🇷 Français
Si la température de l'eau est **inférieure à 10°C**, l'Aqualyser et la pompe de filtration sont **éteints automatiquement**. L'électrolyseur ne peut pas fonctionner en dessous de 10°C (erreur E2).

### 🇬🇧 English
If water temperature drops **below 10°C**, the Aqualyser and filtration pump are **automatically shut down**. The electrolyser cannot operate below 10°C (error E2).

---

## 📊 Tableaux du Fabricant / Manufacturer Tables

### 🌡️ Temps de Traitement (Chloration) / Treatment (Chlorination) Time

#### 🇫🇷 Français

| Température de l'eau | Fréquentation normale | Forte fréquentation |
| :--- | :--- | :--- |
| **T° < 10°C** | Aqualyser ARRÊTÉ 🔴 | Aqualyser ARRÊTÉ 🔴 |
| **10°C ≤ T° < 20°C** *(ou piscine couverte)* | 2h | 2h |
| **20°C ≤ T° < 25°C** | 4h | 4h |
| **25°C ≤ T° < 28°C** | 6h | 6h |
| **28°C ≤ T° < 30°C** | 8h | 12h |
| **T° ≥ 30°C** | 24h | 24h *(BOOST 100%)* |

#### 🇬🇧 English

| Water Temperature | Normal Attendance | High Attendance |
| :--- | :--- | :--- |
| **T° < 10°C** | Aqualyser OFF 🔴 | Aqualyser OFF 🔴 |
| **10°C ≤ T° < 20°C** *(or covered pool)* | 2h | 2h |
| **20°C ≤ T° < 25°C** | 4h | 4h |
| **25°C ≤ T° < 28°C** | 6h | 6h |
| **28°C ≤ T° < 30°C** | 8h | 12h |
| **T° ≥ 30°C** | 24h | 24h *(BOOST 100%)* |

---

### 💧 Temps de Filtration (Granulaire) / Filtration Time (Granular)

#### 🇫🇷 Français

| Température de l'eau | Temps de filtration | Forte fréquentation (28–30°C) |
| :--- | :--- | :--- |
| **T° < 10°C** | Pompe ARRÊTÉE 🔴 | Pompe ARRÊTÉE 🔴 |
| **T° ≥ 10°C** | 5h | — |
| **T° ≥ 12°C** | 6h | — |
| **T° ≥ 14°C** | 7h | — |
| **T° ≥ 16°C** | 8h | — |
| **T° ≥ 18°C** | 9h | — |
| **T° ≥ 20°C** | 10h | — |
| **T° ≥ 22°C** | 11h | — |
| **T° ≥ 23°C** | 12h | — |
| **T° ≥ 25°C** | 12h | — |
| **T° ≥ 26°C** | 14h | — |
| **T° ≥ 27°C** | 15h | — |
| **T° ≥ 28°C** | 16h | 24h |
| **T° ≥ 29°C** | 20h | 24h |
| **T° ≥ 30°C** | 24h | 24h |

#### 🇬🇧 English

| Water Temperature | Filtration Time | High Attendance (28–30°C) |
| :--- | :--- | :--- |
| **T° < 10°C** | Pump OFF 🔴 | Pump OFF 🔴 |
| **T° ≥ 10°C** | 5h | — |
| **T° ≥ 12°C** | 6h | — |
| **T° ≥ 14°C** | 7h | — |
| **T° ≥ 16°C** | 8h | — |
| **T° ≥ 18°C** | 9h | — |
| **T° ≥ 20°C** | 10h | — |
| **T° ≥ 22°C** | 11h | — |
| **T° ≥ 23°C** | 12h | — |
| **T° ≥ 25°C** | 12h | — |
| **T° ≥ 26°C** | 14h | — |
| **T° ≥ 27°C** | 15h | — |
| **T° ≥ 28°C** | 16h | 24h |
| **T° ≥ 29°C** | 20h | 24h |
| **T° ≥ 30°C** | 24h | 24h |

---

### 🏊 Volume du Bassin / Pool Volume → Taux de Production / Production Rate

> Pour les tailles intermédiaires, la valeur supérieure est appliquée.
> For intermediate sizes, the upper rate is applied.

| Taille du bassin / Pool Size | Taux de production / Production rate |
| :--- | :--- |
| ≤ 15 m³ | 20% |
| ≤ 30 m³ | 40% |
| ≤ 50 m³ | 60% |
| ≤ 60 m³ | 80% |
| ≤ 80 m³ | 100% |

---

### 💧 Dureté de l'Eau / Water Hardness → Inversion de Polarité / Polarity Reversal

> Pour les valeurs intermédiaires, le taux d'inversion supérieur (intervalle plus court) est appliqué.
> For intermediate values, the upper reversal rate (shorter interval) is applied.

| Dureté / Hardness (TH) | Intervalle / Interval |
| :--- | :--- |
| TH < 30°f | 8h |
| TH < 40°f | 6h |
| TH < 50°f | 4h |
| TH ≥ 50°f | 2h |

---

## ⚙️ Switch Fréquentation (Optionnel) / High Attendance Switch (Optional)

### 🇫🇷 Français
L'option **Switch Fréquentation** est optionnelle :
- **Non renseigné ou `OFF` (Par défaut)** : Fréquentation normale.
- **`ON`** : Forte fréquentation (durées de traitement et filtration supérieures, BOOST à ≥30°C).

#### Comment créer l'entité dans Home Assistant :
**Paramètres** → **Appareils et services** → **Entrées (Helpers)** → **Créer une entrée** → **Interrupteur (Input boolean)** → nommer `Forte Fréquentation Piscine`.

### 🇬🇧 English
The **High Attendance Switch** is optional:
- **Not set or `OFF` (Default)**: Normal attendance.
- **`ON`**: High attendance (higher treatment & filtration durations, BOOST at ≥30°C).

#### How to create the entity in Home Assistant:
**Settings** → **Devices & Services** → **Helpers** → **Create Helper** → **Toggle (Input boolean)** → name it `Pool High Attendance`.

---

## 🔄 Logique de Déclenchement / Trigger Logic

### 🇫🇷 Français
Le blueprint utilise **deux types de déclencheurs** :
1. ⏰ **Heure quotidienne** : Lance le cycle de filtration chaque jour à l'heure configurée.
2. 🌡️ **Franchissement de seuil** : Si la température franchit un seuil (10, 12, 14, 16, 18, 20, 22, 23, 25, 26, 27, 28, 29, 30°C) en cours de journée, le cycle est **recalculé et relancé** automatiquement.

### 🇬🇧 English
The blueprint uses **two trigger types**:
1. ⏰ **Daily schedule**: Starts the filtration cycle daily at the configured time.
2. 🌡️ **Threshold crossing**: If temperature crosses a threshold (10, 12, 14, 16, 18, 20, 22, 23, 25, 26, 27, 28, 29, 30°C) during the day, the cycle **automatically recalculates and restarts**.

---

## 🛠️ Fichiers / Files

- `poolex_aqualyser_blueprint.yaml` : Blueprint d'automatisation Home Assistant.
