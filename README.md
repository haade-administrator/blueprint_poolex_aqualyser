# 🏊 Poolex Aqualyser Multi - Home Assistant Blueprint

Blueprint d'automatisation Home Assistant complet pour le **Poolex Aqualyser Multi**, basé sur les préconisations exactes du fabricant.

---

## 🚀 Importer le Blueprint / Import Blueprint

[![my_homeassistant_import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fhaade-administrator%2Fblueprint_poolex_aqualyser%2Fblob%2Fmain%2Fpoolex_aqualyser_blueprint.yaml)

---

## ⚙️ Prérequis — Créer les Helpers / Prerequisites — Create Helpers

Avant d'utiliser le blueprint, deux helpers doivent être créés dans Home Assistant.
Before using the blueprint, two helpers must be created in Home Assistant.

---

### ⏱️ Helper 1 — Timer de Filtration / Filtration Timer

**Obligatoire / Required**

Ce timer gère l'arrêt automatique de la pompe de filtration. Sa durée est calculée et envoyée automatiquement par le blueprint — **pas de durée par défaut à configurer**.

This timer manages the automatic shutdown of the filtration pump. Its duration is calculated and sent automatically by the blueprint — **no default duration to set**.

#### 🇫🇷 Créer le Timer Filtration

1. Aller dans **Paramètres** → **Appareils et services** → **Entrées (Helpers)**
2. Cliquer sur **+ Créer une entrée**
3. Choisir **Minuteur (Timer)**
4. Renseigner :
   - **Nom :** `Timer Filtration`
   - **Durée par défaut :** laisser vide ou `0`
   - **Restaurer au redémarrage :** ✅ activé (recommandé)
5. Cliquer sur **Créer**

#### 🇬🇧 Create the Filtration Timer

1. Go to **Settings** → **Devices & Services** → **Helpers**
2. Click **+ Create Helper**
3. Choose **Timer**
4. Fill in:
   - **Name:** `Filtration Timer`
   - **Duration:** leave empty or `0`
   - **Restore on restart:** ✅ enabled (recommended)
5. Click **Create**

---

### 👥 Helper 2 — Forte Fréquentation / High Attendance *(Optionnel / Optional)*

**Optionnel / Optional**

Permet de basculer entre fréquentation normale et forte fréquentation. Impacte uniquement la tranche 28–30°C (chloration 8h→12h, filtration augmentée) et déclenche le mode Boost à ≥30°C.

Allows switching between normal and high attendance mode. Only affects the 28–30°C range (chlorination 8h→12h, increased filtration) and triggers Boost mode at ≥30°C.

#### 🇫🇷 Créer le Switch Forte Fréquentation

1. Aller dans **Paramètres** → **Appareils et services** → **Entrées (Helpers)**
2. Cliquer sur **+ Créer une entrée**
3. Choisir **Interrupteur (Input boolean)**
4. Renseigner :
   - **Nom :** `Forte Fréquentation Piscine`
5. Cliquer sur **Créer**

#### 🇬🇧 Create the High Attendance Switch

1. Go to **Settings** → **Devices & Services** → **Helpers**
2. Click **+ Create Helper**
3. Choose **Toggle (Input boolean)**
4. Fill in:
   - **Name:** `Pool High Attendance`
5. Click **Create**

---

## ❄️ Sécurité intempérie / Weather Safety

### 🇫🇷 Français
Si la température de l'eau est **inférieure à 10°C**, l'Aqualyser et la pompe de filtration sont **éteints automatiquement**. L'électrolyseur ne peut pas fonctionner en dessous de 10°C (erreur E2).

### 🇬🇧 English
If water temperature drops **below 10°C**, the Aqualyser and filtration pump are **automatically shut down**. The electrolyser cannot operate below 10°C (error E2).

---

## 📊 Tableaux du Fabricant / Manufacturer Tables

### 🌡️ Temps de Traitement (Chloration) / Treatment (Chlorination) Time

| Température / Temperature | Fréquentation normale / Normal | Forte fréquentation / High |
| :--- | :--- | :--- |
| **T° < 10°C** | Aqualyser ARRÊTÉ 🔴 | Aqualyser OFF 🔴 |
| **10°C ≤ T° < 20°C** | 2h | 2h |
| **20°C ≤ T° < 25°C** | 4h | 4h |
| **25°C ≤ T° < 28°C** | 6h | 6h |
| **28°C ≤ T° < 30°C** | 8h | **12h** |
| **T° ≥ 30°C** | 24h | 24h + **BOOST** |

---

### 💧 Temps de Filtration (Granulaire) / Filtration Time (Granular)

| Température / Temperature | Filtration | Forte fréquentation / High (28–30°C) |
| :--- | :--- | :--- |
| **T° < 10°C** | Pompe ARRÊTÉE 🔴 | — |
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
| **T° ≥ 28°C** | 16h | **24h** |
| **T° ≥ 29°C** | 20h | **24h** |
| **T° ≥ 30°C** | 24h | 24h |

---

### 🏊 Volume du Bassin / Pool Volume → Taux de Production / Production Rate

> Pour les tailles intermédiaires, la valeur supérieure est appliquée.
> For intermediate sizes, the upper rate is applied.

| Volume | Taux / Rate |
| :--- | :--- |
| ≤ 15 m³ | 20% |
| ≤ 30 m³ | 40% |
| ≤ 50 m³ | 60% |
| ≤ 60 m³ | 80% |
| > 60 m³ | 100% |

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

## 🛠️ Fichiers / Files

- `poolex_aqualyser_blueprint.yaml` : Blueprint d'automatisation Home Assistant.
