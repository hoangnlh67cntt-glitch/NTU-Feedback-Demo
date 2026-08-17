# NTU Feedback Analytics — Public Demo

Demo công khai của hệ thống phân tích phản hồi sinh viên bằng NLP + Ontology/OWL + SPARQL + Streamlit.

## Public-demo safety

- Dữ liệu giảng viên đã được **ẩn danh** thành `GV_001`, `GV_002`, ...
- Các tên riêng phát hiện trong nội dung phản hồi đã được che bằng `[ẨN_DANH]`.
- Không đưa dữ liệu thô, Gold Set, IAA annotations hoặc dữ liệu augmentation lên bản public demo.
- Chức năng **sửa/xóa dữ liệu gốc bị khóa**.
- Dữ liệu người dùng nhập ở trang phân tích chỉ tồn tại trong phiên Streamlit và không được ghi vào file nguồn.

## Chạy cục bộ

```bash
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

## Cấu trúc deploy

```text
NTU-Feedback-Demo/
├── app.py
├── requirements.txt
├── .gitignore
├── .streamlit/
│   ├── config.toml
│   └── secrets.toml.example
├── data/processed/
│   └── Du_Lieu_NTU_Official.xlsx
├── ontology/
│   ├── Ontology_NTU_FeedbackSystem_V8.owl
│   ├── SPARQL_Queries.txt
│   └── SPARQL_Queries_V8.txt
├── src/
│   ├── owl_sparql_engine.py
│   └── ... research scripts ...
├── config.py
├── run_all.py
└── docs/
    ├── DEPLOY_GITHUB_STREAMLIT.md
    └── GOOGLE_FORM_TEMPLATE.md
```

## Google Form đánh giá

Dashboard đọc URL từ `st.secrets["SURVEY_URL"]`. Khi deploy trên Streamlit Community Cloud, mở **App settings → Secrets** và dán:

```toml
SURVEY_URL = "https://forms.gle/....."
```

Xem hướng dẫn chi tiết trong `docs/DEPLOY_GITHUB_STREAMLIT.md`.
