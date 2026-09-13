# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Nguyễn Thị Thuý Hiền 
> **Mã Sinh Viên / Mã Học viên:** 2A202602896
> **Chủ đề Lựa chọn:** Trợ lý Học vụ & Tra cứu Lịch thi VinUni

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 5 / 5 | Với yêu cầu đặt lịch theo đúng cố vấn, Agent phải tra cứu hồ sơ, xác định cố vấn từ Observation và mới tạo lịch hẹn. |
| **2. Tool Interaction** | 5 / 5 | Hệ thống cần gọi MCP Server để dùng `academic_query` truy vấn dữ liệu và `schedule_appointment` tạo booking. |
| **3. Dynamic Decision** | 5 / 5 | Tool tiếp theo và tham số `advisor_name` phụ thuộc vào kết quả tra cứu sinh viên ở bước trước. |
| **4. Long Horizon Goal** | 4 / 5 | Agent duy trì mục tiêu hỗ trợ học vụ từ câu hỏi đến xác nhận kết quả qua nhiều bước ReAct trong một phiên. |
| **TỔNG ĐIỂM AGENTIC FIT** | **19 / 20** | *Bài toán rất phù hợp triển khai Agentic System vì tổng điểm lớn hơn 12/20.* |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG

> **Trạng thái nghiệm thu API thật:** Đã chạy thành công với `OpenAIProvider` và API key hợp lệ. Toàn bộ 5/5 test case đã thực thi; trace hiện tại được tạo từ phản hồi LLM thật.

Đoạn trace tiêu biểu của TC04 chứng minh luồng ReAct đa bước Tra cứu → Đặt lịch → Final Answer:

```json
[
  {
    "step": 1,
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV2026001"
    },
    "observation": {
      "status": "SUCCESS",
      "student_id": "SV2026001",
      "data": {
        "full_name": "Nguyễn Văn An",
        "gpa": 3.85,
        "advisor": "PGS.TS Nguyễn Văn A"
      }
    },
    "latency_ms": 1400.52
  },
  {
    "step": 2,
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "student_id": "SV2026001",
      "datetime_str": "09:00 16/09/2026",
      "advisor_name": "PGS.TS Nguyễn Văn A"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026001-99"
    },
    "latency_ms": 1120.58
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã xác nhận Agent chạy trên LLM API thật với OpenAI Provider.
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 5 lượt.
- **Kết quả đẩy Repo nộp bài:** [ ] Chờ commit và push trace nghiệm thu API thật.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
