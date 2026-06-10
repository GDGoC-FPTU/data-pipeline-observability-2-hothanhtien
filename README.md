[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112864&assignment_repo_type=AssignmentRepo)

# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** hothanhtienqb20092004@gmail.com
**Name:** Hồ Thành Tiến
**Student ID:** AI20K-0001

---

## Mo ta

Bai lab xay dung mot ETL Pipeline tu dong doc du lieu san pham tu file JSON, thuc hien validate (loai bo gia am/bang 0 va category rong), transform (tinh gia giam 10% va chuan hoa category sang Title Case), roi luu ket qua ra CSV. Ngoai ra bai lab con thuc hien Stress Test de quan sat tac dong cua garbage data len ket qua tra loi cua AI Agent.

---

## Cach chay (How to Run)

### Prerequisites

```bash
pip install pandas pytest
```

### Chay ETL Pipeline

```bash
python solution.py
```

### Tao Garbage Data

```bash
python generate_garbage.py
```

### Chay Agent Simulation (Stress Test)

```bash
python agent_simulation.py
```

### Chay tat ca Tests

```bash
pytest tests/
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline (Clean Data)
├── garbage_data.csv         # Du lieu rac dung de stress test
├── raw_data.json            # Du lieu nguon
├── agent_simulation.py      # Agent simulation script
├── generate_garbage.py      # Script tao garbage data
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Tong so records doc vao:** 5
- **Records hop le (passed validation):** 3
- **Records bi loai (dropped):** 2
  - Record id=3: price = -10 (gia am)
  - Record id=4: category rong
- **Output file:** `processed_data.csv` voi cac cot: id, product, price, category, discounted_price, processed_at

### So sanh Clean vs Garbage Data

| Scenario | Ket qua Agent |
|----------|---------------|
| Clean Data | "Laptop at $1200" (chinh xac) |
| Garbage Data | "Nuclear Reactor at $999999" (sai hoan toan) |
