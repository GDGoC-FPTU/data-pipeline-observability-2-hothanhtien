# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-0001
**Name:** Ho Thanh Tien
**Date:** 2026-06-10

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | "The best choice is Laptop at $1200." | 9 | Ket qua chinh xac, du lieu da qua validate va transform |
| Garbage Data (`garbage_data.csv`) | "The best choice is Nuclear Reactor at $999999." | 1 | Ket qua sai hoan toan do outlier cuc doan (999999$) va duplicate ID |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung garbage data, Agent tra loi sai vi du lieu dau vao chua nhieu van de chat luong nghiem trong.

**Duplicate IDs:** Record co id=1 xuat hien 2 lan voi cac san pham khac nhau (Laptop va Banana), khien Agent khong biet record nao moi la chinh xac, gay ra su nham lan trong ket qua tra ve.

**Wrong Data Types:** San pham "Broken Chair" co gia tri price la "ten dollars" thay vi so nguyen. Khi Agent co gang tinh toan hoac so sanh gia tri nay, no co the gay loi hoac bi bo qua, dan den ket qua khong day du.

**Extreme Outlier:** San pham "Nuclear Reactor" co gia 999999$ la mot gia tri bat thuong va phi thuc te. Vi Agent chon san pham co gia cao nhat, no tra ve "Nuclear Reactor" thay vi mot san pham dien tu thuc su phu hop voi nguoi dung.

**Null Values:** Record "Ghost Item" co id=None va category=None. Cac gia tri null nay co the gay ra loi khi Agent xu ly, hoac tao ra ket qua khong mong muon neu khong co xu ly ngoai le.

Ket luan: Du lieu xau khong chi gay ra ket qua sai ma con co the lam cho AI Agent hoat dong theo nhung cach hoan toan khong du doan duoc. Mot AI Agent chi tot bao nhieu phu thuoc vao chat luong du lieu ma no duoc cung cap - day chinh la nguyen tac "Garbage In, Garbage Out" trong khoa hoc du lieu.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Du co viet prompt tot den dau, neu du lieu dau vao chua nhieu loi nhu duplicate, outlier, null values hay sai kieu du lieu, ket qua cua AI Agent van se sai. Viec dam bao chat luong du lieu thong qua ETL pipeline va cac buoc validate la dieu kien tien quyet de co mot he thong AI dang tin cay. Data quality la nen tang cua moi ung dung AI thuc te.
