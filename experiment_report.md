# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600487
**Name:** Nguyễn Tiến Thành
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario                          | Agent Response                                                                                                                                        | Accuracy (1-10) | Notes                                                      |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ---------------------------------------------------------- |
| Clean Data (`processed_data.csv`) | Agent tra loi dung: "Best choice is Monitor at $300" va "Laptop at $1200" theo gia tri hien tai. Danh muc duoc chuan hoa dung, gia chinh xac.         | 9               | Du lieu sach, da validate, category dung Title Case        |
| Garbage Data (`garbage_data.csv`) | Agent gap loi: doc gia "ten dollars" khong the chuyen sang so, ID bi trung lap, co ban ghi null category. Agent tra loi sai hoac crash voi exception. | 2               | Duplicate ID, wrong data type, outlier 999999, null values |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi Agent su dung du lieu rac (garbage data), co nhieu van de nghiem trong xay ra. Thu nhat, Duplicate ID khien Agent khong biet nen chon ban ghi nao khi tra cuu theo ID. Thu hai, kieu du lieu sai (gia la chuoi "ten dollars" thay vi so) khien phep tinh so hoc bi loi, Agent khong the so sanh hay tinh toan gia ca. Thu ba, gia tri ngoai le qua lon (Outlier: $999,999) lam lech ket qua: Agent co the de xuat san pham bat thuong thay vi san pham thuc te. Thu tu, gia tri null o category va id khien Agent mat thong tin de phan loai va tra loi cau hoi the loai. Tat ca nhung van de nay cho thay du lieu dau vao ke kem se truc tiep dan den ket qua dau ra kem chat luong, du prompt co tot den dau cung khong khac phuc duoc. Day chinh la ly do tai sao buoc ETL Validation va data quality check rat quan trong trong bat ky he thong AI nao.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y. Du lieu chat luong cao quan trong hon prompt tot. Ngay ca khi prompt duoc viet hoan hao, neu du lieu dau vao chua day du van de (null, wrong type, duplicate, outlier), Agent van se tra loi sai hoac bi loi. ETL pipeline voi validation chat che la nen tang bat buoc de xay dung he thong AI dang tin cay.
