# Production Planning Optimization (Linear Programming with PuLP)

A data science project that uses **linear programming** to solve a real business problem: deciding how much of each product a furniture manufacturer should make each month to **maximize profit**, given limited resources.

## Business Problem

*OakCraft Furniture* makes four products: **chairs, tables, desks and shelves**. Each product earns a different profit and uses wood, labor hours and machine hours. Resources are limited, demand is capped, and some minimum quantities are promised to contract customers.

**Question:** how many units of each product should be produced to earn the highest possible profit?

## What the Notebook Covers

1. Setup and data
2. Mathematical formulation (decision variables, objective, constraints)
3. Building the model in PuLP
4. Optimal production plan and chart
5. Resource utilization, shadow prices, reduced costs
6. What-if analysis (capacity sweeps)
7. LP vs. integer (whole-unit) solution
8. Insights and recommendations

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3.9+ | Language |
| PuLP | Modeling the optimization problem |
| CBC (bundled with PuLP) | Solver |
| pandas | Data handling and result tables |
| matplotlib | Charts |
| Jupyter Notebook | Interactive deliverable |

## Project Structure

```
optimization-model/
├── optimization_model.ipynb   # main notebook
├── requirements.txt           # dependencies
└── README.md
```

## Setup and Run

### 1. Check Python
```bash
python --version
```
You need Python 3.9 or newer. On some systems the command is `python3`.

### 2. Open the project folder
```bash
cd path/to/optimization-model
```

### 3. Create a virtual environment
```bash
python -m venv venv
```

### 4. Activate it
- **Windows (Command Prompt):** `venv\Scripts\activate`
- **Windows (PowerShell):** `venv\Scripts\Activate.ps1`
- **macOS / Linux:** `source venv/bin/activate`

### 5. Install dependencies
```bash
pip install -r requirements.txt
```

### 6. Launch Jupyter
```bash
jupyter notebook optimization_model.ipynb
```

### 7. Run all cells
In the notebook menu choose **Kernel → Restart & Run All**.

## Expected Results

With the included data, the model should recommend about **80 chairs, 40 tables, 30 desks and 10 shelves** for a maximum profit of about **$13,500**. Labor and machine hours are the binding bottlenecks, while wood has spare capacity.

## Customizing

Edit the `products` table and the `capacity` dictionary near the top of the notebook with your own profits, resource usage and limits, then re-run all cells. The model, charts and insights update automatically.

## Possible Extensions

- Multi-period planning with inventory
- Fixed setup costs using binary variables
- Uncertain demand with scenario or robust optimization
- Streamlit app for interactive what-if analysis

## Troubleshooting

- **`pip` or `python` not found:** use `python3` / `pip3`, or reinstall Python and tick "Add Python to PATH".
- **PowerShell blocks activation:** run `Set-ExecutionPolicy -Scope Process RemoteSigned`, then activate again.
- **`jupyter` not found:** make sure the virtual environment is activated, then re-run `pip install -r requirements.txt`.
- **Solver not found error:** run `pip install --upgrade "pulp<3"`.
- **`LpVariable` TypeError (lowBound / positional arguments):** you have PuLP 3.x. Run `pip install "pulp<3"`, then restart the Jupyter kernel.
