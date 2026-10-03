# Project 3: The SOC Threat Syncer & ATT&CK Matrix Modeler

## Project Goal
To build a Python automation tool using **Pandas DataFrames** that simplifies threat hunting. The utility reads complex endpoint security logs, cleans out missing or corrupted rows, filters for malicious activity, and exports the data into a formatted JSON layer. This layer can be uploaded directly to the [MITRE ATT&CK Navigator](https://mitre.org) web platform for instant visual tracking.

---

## Technical Features
* **DataFrame Ingestion:** Uses `pandas.read_csv()` to load multi-column log datasets directly into memory for fast processing.
* **Automated Data Cleansing:** Runs vectorized `.dropna()` filters to drop incomplete or missing fields before analysis.
* **Threat Filtering:** Isolates specific events by filtering rows where `ThreatLabel == "Malicious"`.
* **Data Re-structuring:** Maps flat technique ID strings into a nested Python dictionary that matches the official MITRE Navigator specification.
* **JSON Export:** Uses the native `json` library to output a cleanly formatted layout (`data/attack_layer.json`) with standard indentation.

---

## The Real-World SOC Problem
* **The Log Deluge:** Modern EDR tools record thousands of commands every minute. Sifting through these rows line-by-line using basic file loops causes massive delays in a real Security Operations Centre (SOC).

* **Missing Context:** Security analysts often find suspicious commands (like hidden PowerShell scripts) but lose critical time manually searching for what specific attack phase they belong to.

* **The Solution:** Automating the jump from raw CSV spreadsheets to a standard visual matrix gives instant context to defenders and speeds up triage time.

---

## Portfolio Growth: Upgrades Over Project 1 & 2
This final project highlights how my Python and software engineering skills have evolved over the last 4 months:

### 1. Data Tables vs. Text Lines
* **Before (Project 1 & 2):** My scripts streamed text log files line-by-line. While this worked well for strings, it required a lot of manual loops to split fields.

* **Now (Project 3):** I stepped up to data science tools. By using **Pandas DataFrames**, the engine cleans and filters thousands of records instantly using simple data filters instead of long nested loops.

### 2. File Logs vs. Dashboard Integration
* **Before (Project 1 & 2):** Script outputs were entirely restricted to local terminal logs and basic text files.

* **Now (Project 3):** I built a tool that connects directly with an industry-standard web dashboard (**MITRE ATT&CK**), bridging the gap between raw backend code and real-world security visuals.

---

## Breakthroughs & Lessons Learned
* **Fixing Redundant Code:** My initial code crashed because I tried to open the CSV file using a manual `with open()` wrapper. I checked the Pandas documentation, realized `pd.read_csv()` handles file opening automatically, and removed the unnecessary wrapper to make my code much cleaner.

* **Dynamic Terminal Metrics:** I replaced my generic print statements with dynamic counter metrics. The script now tracks runtime data and prints out exact row totals and found techniques to mimic an enterprise tool.

* **Web Portal Validation:** During browser testing, the MITRE portal threw errors because of strict layout requirements. I audited my output structure, aligned it with version `4.5` of the schema, configured a proper 6-character hex color code (`#f00000`), and successfully unblocked the engine to render all 11 threat cells automatically.

* ## 🖥️ MITRE ATT&CK Navigator Preview

In addtion, the dashboard visualization created by uploading the generated `attack_layer.json` file directly into the **MITRE ATT&CK Navigator**. The platform successfully processes our automated threat data, highlighting the flagged technique (**System Owner/User Discovery**) in red for immediate visual tracking.

