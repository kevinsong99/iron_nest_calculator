# IRON NEST: Heavy Turret Calculator

A standalone calculator for **IRON NEST: Heavy Turret Simulator**.

It runs directly in a web browser on Windows and does **not** require Python, Node.js, or any extra libraries.

中文说明请往下划

---

# English

## 1. How to Run

1. Download `iron_nest_turret_calculator.html`.
2. Double-click the file.
3. It will open in your default browser, such as Microsoft Edge or Google Chrome.
4. No installation or internet connection is required.

---

## 2. Inputs

### Target Name

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

Bearing is stored for reference only. It does not affect elevation or flight-time calculations.

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

---

## 3. Elevation Calculation

The elevation formula is:

```text
Elevation = Distance × 12 / Charge
```

Equivalent formulas:

| Charge | Formula |
|---|---|
| 1 | Distance × 12 |
| 2 | Distance × 6 |
| 3 | Distance × 4 |
| 4 | Distance × 3 |
| 5 | Distance × 2.4 |
| 6 | Distance × 2 |

Example:

```text
Distance = 3.5 km
Charge = 1

Elevation = 3.5 × 12
Elevation = 42°
```

---

## 4. Desired Impact Time

Enter the desired impact time using separate fields:

- HR
- MIN
- SEC

The calculator uses a 24-hour clock.

Example:

```text
01:00:00
```

---

## 5. Add Time

You can optionally add a duration to the desired impact time.

Example:

```text
Base Impact Time:
01:00:00

Add Time:
00:05:00

Effective Impact Time:
01:05:00
```

The calculator uses the **Effective Impact Time** when calculating the firing time.

If no additional time is needed, leave all Add Time fields at zero.

---

## 6. Flight Time

Flight time is based on the supplied in-game flight-time chart.

For distances between two listed kilometer values, the calculator uses **linear interpolation**.

Example with Charge 1:

```text
3 km = 14 seconds
4 km = 19 seconds
```

Therefore:

```text
3.5 km = 16.5 seconds
```

The interpolation formula is:

```text
Interpolated Time
= Lower Time
+ Distance Fraction × Time Difference
```

---

## 7. Flight-Time Estimation Outside the Chart

The option:

> Estimate flight time outside the supplied chart by extending the nearest 1 km interval.

is **disabled by default**.

If enabled, the calculator extrapolates flight time using the nearest available interval.

These results should be treated as estimates because they are not directly provided by the original chart.

---

## 8. Fire At Time

The calculator determines the firing timestamp using:

```text
Fire At = Effective Impact Time - Flight Time
```

Example:

```text
Effective Impact Time:
12:00:00

Flight Time:
16.5 seconds

Fire At:
11:59:43.50
```

---

## 9. KPI Results

After pressing **Calculate**, the calculator displays five main result boxes:

- Charge
- Bearing ↔
- Elevation ↕
- Flight Time
- Fire At

Bearing displays `—` if no bearing was entered.

---

## 10. Calculation History

The right side of the screen stores the latest **10 calculations**.

Each history record includes:

- Target name
- Distance
- Bearing ↔
- Charge
- Elevation ↕
- Flight time
- Fire At timestamp

History is stored locally in the browser.

This means the history normally remains available after closing and reopening the HTML file in the same browser.

You can:

- Delete an individual record using the `×` button.
- Delete all records using **Clear history**.

Calculation history is not uploaded anywhere.

---

# 中文说明

## 1. 如何运行

1. 下载 `iron_nest_turret_calculator.html`。
2. 在 Windows 中双击该文件。
3. 文件会直接使用默认浏览器打开，例如 Microsoft Edge 或 Google Chrome。
4. 不需要安装 Python、Node.js 或任何其他第三方库。
5. 不需要联网即可运行。

---

## 2. 输入项

### Target Name / 目标名称

可选。

用于给目标命名，方便在历史记录中区分不同目标。

### Distance / 距离

输入目标距离，单位为公里。

支持范围：

- 大于 `0 km`
- 最大 `30 km`

### Bearing / 方位角

可选。

支持范围：

- `0.0°` 到 `359.9°`
- 精度为 `0.1°`

方位角只用于记录和参考，不参与仰角或飞行时间计算。

界面中：

- `↔` 表示 **Bearing / 水平方向 / 方位角**
- `↕` 表示 **Elevation / 垂直方向 / 仰角**

### Charge / 装药数

计算器可以根据距离自动选择能够覆盖目标的最小装药数。

| 装药数 | 最大射程 |
|---|---:|
| 1 | 5 km |
| 2 | 10 km |
| 3 | 15 km |
| 4 | 20 km |
| 5 | 25 km |
| 6 | 30 km |

也可以手动选择装药数。

勾选 **Lock charge to 6 (MAX)** 后，会强制始终使用 6 号装药。

---

## 3. 仰角计算

仰角公式：

```text
仰角 = 距离 × 12 / 装药数
```

对应关系：

| 装药数 | 公式 |
|---|---|
| 1 | 距离 × 12 |
| 2 | 距离 × 6 |
| 3 | 距离 × 4 |
| 4 | 距离 × 3 |
| 5 | 距离 × 2.4 |
| 6 | 距离 × 2 |

例如：

```text
距离 = 3.5 km
装药数 = 1

仰角 = 3.5 × 12
仰角 = 42°
```

---

## 4. Desired Impact Time / 期望命中时间

命中时间分别输入：

- HR / 小时
- MIN / 分钟
- SEC / 秒

使用 24 小时制。

例如：

```text
01:00:00
```

---

## 5. Add Time / 追加时间

可以额外输入一段时间，并将其加到原始命中时间上。

例如：

```text
原始命中时间：
01:00:00

追加时间：
00:05:00

最终有效命中时间：
01:05:00
```

计算器会使用 **Effective Impact Time / 最终有效命中时间** 来计算开火时间。

如果不需要追加时间，将 Add Time 全部保持为 `0` 即可。

---

## 6. 飞行时间

飞行时间来自提供的游戏内飞行时间表。

如果输入距离位于两个整数公里之间，计算器会使用 **线性插值**。

例如 1 号装药：

```text
3 km = 14 秒
4 km = 19 秒
```

因此：

```text
3.5 km = 16.5 秒
```

计算逻辑：

```text
插值飞行时间
= 下限距离对应时间
+ 距离比例 × 两个时间点的时间差
```

---

## 7. 超出表格范围的飞行时间估算

选项：

> Estimate flight time outside the supplied chart by extending the nearest 1 km interval.

默认 **不勾选**。

如果开启，计算器会根据最接近的一段 1 km 数据进行外推估算。

因为这些数值并未直接出现在原始飞行时间表中，所以只能视为估算值。

---

## 8. Fire At / 开火时间

计算公式：

```text
开火时间 = 最终有效命中时间 - 飞行时间
```

例如：

```text
最终有效命中时间：
12:00:00

飞行时间：
16.5 秒

开火时间：
11:59:43.50
```

---

## 9. KPI 结果区

点击 **Calculate** 后，会显示五个主要结果：

- Charge / 装药数
- Bearing ↔ / 方位角
- Elevation ↕ / 仰角
- Flight Time / 飞行时间
- Fire At / 开火时间

如果没有输入 Bearing，则 Bearing 显示为 `—`。

---

## 10. 历史记录

屏幕右侧会保存最近 **10 条计算记录**。

每条记录包括：

- 目标名称
- 距离
- Bearing ↔ / 方位角
- 装药数
- Elevation ↕ / 仰角
- 飞行时间
- Fire At / 开火时间

历史记录保存在浏览器本地。

因此，在同一浏览器中关闭并重新打开 HTML 文件后，历史记录通常仍然会保留。

可以：

- 点击单条记录右侧的 `×` 删除该记录。
- 点击 **Clear history** 清除全部记录。

历史记录不会上传到任何服务器。

---

## Notes / 注意事项

This calculator is intended only for use with the game **IRON NEST: Heavy Turret Simulator**.

本工具仅用于游戏 **IRON NEST: Heavy Turret Simulator**。
