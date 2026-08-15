# IRON NEST: Heavy Turret Calculator

A standalone calculator for **IRON NEST: Heavy Turret Simulator**.

It runs directly in a web browser on Windows and does **not** require Python, Node.js, or any extra libraries.

中文说明请往下划

---

# English

## 1. How to run

1. Download `iron_nest_turret_calculator.html`.
2. Double-click the file.
3. It will open in your default browser, such as Microsoft Edge or Google Chrome.
4. No installation or internet connection is required.

## 2. Inputs

### Target name

Optional name used to identify the target in calculation history.

### Distance

Enter the target distance in kilometers.

Supported range:

- Greater than `0 km`
- Maximum `30 km`

### Bearing

Optional target bearing.

Supported range:

- `0.0°` to `359.9°`
- Resolution: `0.1°`

Bearing is only stored for reference. It does not affect elevation or flight-time calculations.

The UI uses:

- `↔` for **Bearing / horizontal direction**
- `↕` for **Elevation / vertical direction**

### Charge

The calculator can automatically choose the minimum charge required to reach the entered distance.

| Charge | Maximum Distance |
|---|---:|
| 1 | 5 km |
| 2 | 10 km |
| 3 | 15 km |
| 4 | 20 km |
| 5 | 25 km |
| 6 | 30 km |

You can also manually select a charge.

The **Lock charge to 6 (MAX)** option forces the calculator to always use Charge 6.

## 3. Elevation Calculation

The elevation formula is:

```text
Elevation = Distance × 12 / Charge
