# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

- **MSSV:** 2A202603455
- **Họ và tên:** Phan Hoàng Phúc
- **SEED:** 5953

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | ☑ |
| [`lab1_report.json`](lab1_report.json) | ☑ |
| `hand_calc.jpg` — ảnh tính tay | ☐ Chưa làm |

## 2. Kết quả chính

| Cách | F1 test | F1 SUB 40 | p95 ms/tin | USD/1k tin |
| --- | --- | --- | --- | --- |
| 1. BoW + LogReg | 0.901 | 0.857 | 0.145 | 0 |
| 2. BoW + MLP | 0.942 | 0.889 | 0.374 | 0 |
| 3a. Encoder + kNN | 0.928 | 0.950 | 123.664 | 0 |
| 3b. Encoder + LogReg | 0.954 | 0.919 | 62.578 | 0 |
| 3c. Encoder + MLP head | 0.949 | 0.919 | 37.452 | 0 |
| 4a. LLM nhỏ zero-shot | 0.950 | 0.950 | 892.105 | 0.021 |
| 4b. LLM lớn zero-shot | 0.974 | 0.974 | 6288.177 | 0.048 |
| 4c. LLM nhỏ few-shot | 1.000 | 1.000 | 892.665 | 0.058 |

Hàng LLM chỉ đo trên 40 tin, nên F1 của chúng không so trực tiếp với F1 test đầy đủ.

## 3. Dự đoán và thực tế

Chưa hoàn thành. Các dự đoán đã ghi nằm trong `lab1_report.json`.

## 4. Phân tích 50 case khó

| Model | F1 test thường (SUB) | F1 50 case khó | Accuracy 50 case khó |
| --- | --- | --- | --- |
| 1. BoW + LogReg | 0.857 | 0.286 | 0.50 |
| 2. BoW + MLP | 0.889 | 0.524 | 0.60 |
| 3a. Emb + kNN | 0.950 | 0.737 | 0.70 |
| 3b. Emb + LogReg | 0.919 | 0.612 | 0.62 |
| 3c. Emb + MLP head | 0.919 | 0.625 | 0.64 |
| 4a. LLM nhỏ zero-shot | 0.950 | 1.000 | 1.00 |
| 4d. LLM nhỏ + prompt phòng thủ | 0.950 | 1.000 | 1.00 |

BoW tụt nhiều nhất, từ 0.857 xuống 0.286. Phân tích theo từng case: chưa hoàn thành.

## 5. Thử thách cá nhân

Đề #2 (vocab 100 và 5000 từ). Chưa làm.

## 6. Phương án cho sản phẩm thật

Với p95 < 50 ms/tin, các cách đạt là BoW + LogReg, BoW + MLP và Encoder + MLP head. Tôi chọn BoW + MLP (F1 0.942, p95 0.374 ms) vì nhanh hơn nhiều so với 3c (F1 0.949, p95 37.452 ms, sát ngưỡng) mà chỉ kém 0.007 F1. Điểm yếu là BoW + MLP chỉ đạt F1 0.524 trên 50 case khó. LLM nhỏ không đạt độ trễ, và tốn khoảng 6.300 USD/tháng cho 10 triệu tin/ngày.

## 7. AI log và điều đã học

| Phần | Hỏi AI gì | AI viết gì | Kiểm chứng gì |
| --- | --- | --- | --- |
| 0-3 | Giải thích khái niệm, xin code TODO | Code 1.1 đến 3.3 và giải thích | Chạy các ô kiểm tra |
| 4 | Viết code LLM, sửa lỗi | Code 4.1 đến 4.4, sửa lỗi message rỗng | Đổi `reasoning_effort` từ `minimal` sang `low` cho Gemini |
| 4-6 | Trả lời ngắn các câu hỏi | Bản nháp câu trả lời | Đối chiếu số của mình |

AI cũng soạn và tải lên báo cáo này từ số liệu trong notebook. Phần điều đã học: chưa hoàn thành.
