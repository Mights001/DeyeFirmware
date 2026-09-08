# Deye Firmware Collection

## Disclaimer

This repository is a private hobby project and is intended solely for informational and archival purposes. It contains a collection of firmware files and related resources for Deye inverters.

### No Warranty

All files and information contained in this repository are provided "as is", without any warranty of any kind, express or implied. No guarantees are made regarding accuracy, completeness, reliability, compatibility, functionality, or suitability for any specific purpose.

### Use at Your Own Risk

By downloading, using, modifying, or installing any file from this repository, you acknowledge and agree that:

* You do so entirely at your own risk.
* You are solely responsible for verifying compatibility with your specific device and system.
* The repository owner assumes no responsibility or liability for any damage, malfunction, data loss, financial loss, reduced performance, downtime, or any other direct or indirect consequences resulting from the use of these files.
* The repository owner provides no technical support and makes no promises regarding the outcome of firmware installations or modifications.

### Warranty and Manufacturer Support

Installing, modifying, or using firmware obtained from this repository may void warranties, guarantees, service agreements, or support entitlements provided by the manufacturer, distributor, installer, or reseller.

No warranty, certification, approval, endorsement, or support is provided by Deye or any other manufacturer regarding the files contained in this repository.

### Unofficial Resource

This repository is not affiliated with, endorsed by, authorized by, or associated with Deye or any of its subsidiaries, partners, distributors, or representatives.

All trademarks, product names, and company names remain the property of their respective owners.

### Purpose of This Repository

The sole purpose of this repository is to archive and preserve firmware versions and related information for research, educational, historical, and hobbyist use.

Nothing contained in this repository should be interpreted as a recommendation to install, modify, or use any specific firmware version.

### LV Firmware — Known infos about Versions, Bugs, Fixes, Issues,...

| Main Firmware (MCU) | HMI Version | Known Issues & Bugs | Fixes & Characteristics | Recommended Action | Status & Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1128** | **C037** | Throttles/limits power in grid-parallel (AC-Couple) and GEN-Port operation. | — | Upgrade to newer firmware | User tested |
| **1132** | — | Caused battery charging issues for some users. | Quiet fan behavior in Bypass/NoBatt mode (up to 114x). | Upgrade to a stable version | Community reported |
| **1135** | **C037** | Zero Export via Modbus is setable to negative but oscillates / unstable. BMS errors reported on some setups. | **Last version supporting negative feed-in / Zero Export.** Overall reported as stable. Quiet fan behavior in Bypass/NoBatt mode. | Recommended baseline (Use if negative feed-in is required) | Community favorite |
| **1140** | **C037 / C043** | Differences between C043 and C044 remain unclear. | Overall stable. Quiet fan behavior in Bypass/NoBatt mode. | Keep if running stable | Factory default on some units |
| **1144** | **C037** | No LoRa support; no negative grid draw support. | **Last version that properly nets/balances phase power under heavy phase imbalance (Zero Export).** Supports up to 6 kW per phase in off-grid mode. **AC-Couple:** No power limiting in grid-parallel mode. **GEN-Port:** Limits to nominal inverter power (e.g. 12 kW) with 2nd inverter. Quiet fan behavior. | Recommended for grid-parallel, unbalanced loads & Felicity setups | User tested / Stable release |
| **1145** *(AT)* | — | **Grid Code Bug:** Cannot save German VDE4105 profile (reverts continuously to Austrian OVE Directive R25). | Contains Austrian grid profiles. | **Do NOT use in Germany.** Austrian users should prefer newer versions. | Highly problematic for DE |
| **1147** | **C037** | Reported as problematic for DE; initial AT release was unrefined. | **AC-Couple:** No power limiting in grid-parallel mode. **GEN-Port:** Limits to nominal inverter power (e.g. 12 kW) with a 2nd inverter. | Avoid / Upgrade to 1150 or newer | User tested / Community warnings |
| **1150** | **C044** | Some reports about disappeared Serial Number (SN). | Significantly improved over 1147 for Austrian users. | Upgrade if you encounter issues | Improved AT build / Outdated elsewhere |
| **1151** | **C04D** | No detailed community experience reports available yet. | **AC-Couple & GEN-Port:** Limits power to **2x nominal inverter rating**. Deployed directly by official Deye DE support. | Monitor community feedback | User tested / Official Deye DE release |
| **1172** | **C050** | **Zero Export Bug** reported on some setups (unexpected grid draw despite available battery/solar). | 1172/C050 combination described positively by some users; released May 2025. | Test Zero Export behavior if installed | Mixed reports / Reportedly recalled initially |
| **1175** | **C070 / C071** | — | **Rock-solid release.** Considered stable benchmark. Required for LoRa Wallbox. Supports AC-couple via Meter2 while keeping GEN port free for a diesel generator (stable operation without power/signal fluctuations). | **Highly Recommended** | Factory installed on newer units / Confirmed stable |
| **1183** | — | **Contradictory / Pulled Back:** F23 errors (every 10 min to 2-3x/day); negative Zero Export setable on LCD but ineffective; config wiped on update; higher idle consumption (+0.3 kWh/day). | Supposedly fixed recurring faults and allowed negative Zero-Export on LCD. | **Avoid** (Reportedly recalled by support due to customer issues) | Unstable / Contradictory reports |
| **1184** | — | **Contradictory:** Reports of persistent F55/F21 errors on SUN-15K; battery won't load via Grid or PV; HMI reboot when opening settings menu (with C05F); config wiped on update. | Support claims F23 bug from 1183 is resolved. | Exercise caution / Await stable feedback | Unstable / Contradictory reports |

### LV/HMI Versions — Known infos
| HMI Version | Known Issues & Bugs | Characteristics & Capabilities | Recommended Action | Status & Notes |
| :--- | :--- | :--- | :--- | :--- |
| **C03E** | Reportedly drops support for Felicity battery storage. Contains no LoRa/Smart Device menu. | Found on newer Deye 12K units. | Exercise caution with Felicity batteries | Unconfirmed community report |
| **≥ C042** | Menus automatically lock after a period of inactivity. | — | Enter `7777` to unlock settings menu | Introduced in C042 |
| **C050** | Factually a downgrade from C05E. Paired with MCU 1150 on new units reported temps >70 °C. | Contains LoRa / Smart Device menu. | Monitor temperatures if paired with MCU 1150 | Confirmed LoRa menu |
| **C051** | Lacks LoRa support. | Good alternative build; works well in combination with MCU 1175. | Good pair for MCU 1175 | Plausible |2
| **C057** | — | Delivered stock / factory default together with 1172. | — | Factory default build |
| **C059** | Base build responsible for stuck/hanging MCU1 updates. | — | Upgrade HMI if MCU updates get stuck | Unstable baseline |
| **C05E** | Lacks LoRa / Smart Device menu. | Stated as current by support when paired with MCU 1175. | Recommended pair for 1175 (without LoRa) | Confirmed |
| **C05F** | **Buggy:** Causes HMI reboot when opening the settings menu (reproducible with MCU 1184). | Introduced by support for fault resolution (paired with MCU 1183). | Avoid / Upgrade to C071 | Unstable HMI release |
| **C070** | Does not allow setting negative values. | Prerequisite for SmartTX / LoRa Wallbox app setup. | Upgrade to C071 if negative values are required | Confirmed |
| **C071** | — | **Rock-solid HMI.** Runs reliably and stable. Prerequisite for SmartTX / LoRa Wallbox. | **Highly Recommended HMI version** (Obtainable via Support) | Confirmed stable |
| **C072** | Associated with configuration loss issues when paired with MCU 118x. | — | Avoid when running MCU 118x | Confirmed |

### HV Firmware — Known infos about Versions, Bugs, Fixes, Issues,...
| Main Firmware (MCU) | Device / Series | Known Issues & Bugs | Fixes & Characteristics | Recommended Action | Status & Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1087 / 1091** | HV Hybrid (AC-Couple / BKW) | — | Frequency shifting at 0 A charge current works properly. **1087** is considered the last stable "mainstream" release. | Do not update intentionally if running well | Community baseline |
| **< 1095** | HV Hybrid | **MPPT Bug:** Severe power drop during hot afternoons (lasting 2–3 hours). | — | Upgrade to ≥ 1095 | Unstable MPPT |
| **≥ 1095** | HV Hybrid | Unplausible portal values reported by some users (downgrades sought, but old files unavailable). | Fixed the MPPT temperature power drop issue. | Keep if MPPT fix is required | Plausible |
| **1110** | HV Hybrid (LoRa Systems) | **No LoRa Support:** Does not work with LoRa modules (requires F094 for LoRa). | — | Avoid if using LoRa | Plausible |
| **1150** | HV Hybrid | **Zero Export Bug:** Continuously imports and exports grid power instead of holding stable at 0 W. High temps (>70 °C) when paired with HMI C050 on new units. | Downgrading MCU does not break LoRa (LoRa depends solely on HMI). | Avoid C050 + 1150 combination; monitor thermal behavior | Not recommended for new units |

### Acceptance

By accessing, downloading, or using any content from this repository, you agree that the repository owner shall not be held liable for any claims, damages, losses, or liabilities arising from the use of the provided materials.


