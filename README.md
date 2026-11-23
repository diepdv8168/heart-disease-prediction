# BÀI TẬP LỚN MÔN HỌC MÁY (MACHINE LEARNING) - HUCE
**Mã học phần:** 608807 | **Khoa:** Công nghệ Thông tin - Trường Đại học Xây dựng Hà Nội  
**Đề tài:** Dự báo Nguy cơ Mắc Bệnh Tim Mạch (*Cardiovascular Disease Risk Prediction*)  

---

## 📁 Cấu Trúc Mã Nguồn (Repository Structure)

```text
03_SourceCode/
├── data/
│   ├── cardio_train.csv           # Dữ liệu gốc (70,000 bản ghi)
│   └── cardio_cleaned.csv         # Dữ liệu sau làm sạch & Kỹ nghệ đặc trưng (68,599 bản ghi)
├── notebooks/
│   ├── 01_EDA_Preprocessing.ipynb  # Bước 1: Khám phá, làm sạch dữ liệu, Feature Engineering & Pipeline
│   └── 02_Modeling_Evaluation.ipynb # Bước 2: Huấn luyện, tuning siêu tham số & so sánh mô hình
├── models/
│   └── best_model.joblib          # Mô hình tối ưu được xuất bản
├── predict.py                     # Script nhận diện / suy luận mẫu dữ liệu mới
├── requirements.txt               # Danh sách thư viện và phiên bản chính xác
└── README.md                      # Hướng dẫn cài đặt và sử dụng mã nguồn
```

---

## ⚙️ Hướng Dẫn Cài Đặt Môi Trường

1. **Yêu cầu môi trường:** Python `>= 3.10`
2. **Cài đặt các thư viện cần thiết:**
   ```bash
   pip install -r requirements.txt
   ```

---

## 📊 Tóm Tắt Tiến Độ: Bước 1 (Milestone 1 - Checkpoint 1)
- **Tập tin:** `notebooks/01_EDA_Preprocessing.ipynb`
- **Nội dung hoàn thành:**
  1. **EDA & Đánh giá chất lượng:** Kiểm định 70,000 dòng dữ liệu, xác nhận 0 giá trị khuyết thiếu (Null), nhãn mục tiêu cân bằng hoàn hảo (50.0% vs 50.0%).
  2. **Làm sạch ngoại lai theo chuẩn Y khoa:** Loại bỏ 1,401 bản ghi dị biệt sinh lý học (huyết áp âm, huyết áp nghịch đảo, chiều cao/cân nặng bất thường), giữ lại 68,599 hồ sơ bệnh án sạch (98.0%).
  3. **Kỹ nghệ đặc trưng (Feature Engineering):** Bổ sung 6 chỉ số lâm sàng quan trọng: `age_years`, `bmi`, `bmi_category`, `pulse_pressure`, `map`, `bp_category` (AHA 2017), `risk_score`.
  4. **Scikit-learn Pipeline:** Thiết lập `ColumnTransformer` tích hợp `StandardScaler` và `OneHotEncoder`, phân chia Train/Test nghiêm ngặt, **chống tuyệt đối lỗi Rò rỉ Dữ liệu (Zero Data Leakage)**.
  5. **Dữ liệu đầu ra:** Đã xuất file `data/cardio_cleaned.csv` sẵn sàng cho giai đoạn huấn luyện mô hình.
