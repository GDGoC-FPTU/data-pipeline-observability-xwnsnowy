[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574105&assignment_repo_type=AssignmentRepo)

# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** tienthanhcute2k2@gmail.com
**Name:** Nguyễn Tiến Thành

---

## Mo ta

Bai lab nay xay dung mot ETL Pipeline tu dong de xu ly du lieu san pham tu file JSON. Pipeline thuc hien 4 buoc: Extract (doc du lieu), Validate (loai bo du lieu khong hop le), Transform (chuan hoa va tinh gia giam), Load (luu ra CSV). Ngoai ra, bai lab con chay thi nghiem so sanh hieu qua cua AI Agent khi su dung du lieu sach va du lieu rac, tu do chung minh tam quan trong cua data quality trong he thong AI.

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

### Chay Agent Simulation (Stress Test)

```bash
# Buoc 1: Tao du lieu rac
python generate_garbage.py

# Buoc 2: Chay Agent voi ca 2 loai du lieu
python agent_simulation.py
```

### Chay Tests

```bash
pytest tests/test_autograder.py -v
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── raw_data.json            # Du lieu dau vao
├── processed_data.csv       # Output cua pipeline (sau khi chay solution.py)
├── garbage_data.csv         # Du lieu rac (sau khi chay generate_garbage.py)
├── agent_simulation.py      # Mo phong AI Agent
├── generate_garbage.py      # Tao du lieu rac de thu nghiem
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

Pipeline xu ly 5 records tu `raw_data.json`:

- **3 records hop le** duoc giu lai va luu vao `processed_data.csv`
- **2 records bi loai**: 1 record gia am (-10), 1 record category rong
- Moi record duoc tinh them `discounted_price` (giam 10%) va timestamp `processed_at`
