---
name: data-visualization
description: Create insightful charts and graphs from structured data using a simple, declarative grammar.
license: MIT
---

## Workflow

1.  **Provide Data**: Supply data in a supported format (CSV, JSON, or a direct data string).
2.  **Define Chart**: Specify the chart type, mappings (e.g., x-axis, y-axis), and any customizations.
3.  **Generate Visualization**: The skill processes the data and definition to generate the chart image.
4.  **Save Output**: The generated chart is saved to a specified output file path.

## Usage

Use this skill to quickly generate a variety of charts for data analysis and presentation. It supports common chart types like bar, line, scatter, and pie charts.

## Example

```python
import matplotlib.pyplot as plt
import json

data = json.loads('''[
    {"category": "A", "value": 30},
    {"category": "B", "value": 50},
    {"category": "C", "value": 20}
]''')

categories = [d["category"] for d in data]
values = [d["value"] for d in data]

plt.bar(categories, values)
plt.title("Sample Bar Chart")
plt.savefig("sample_chart.png")
plt.show()
```
