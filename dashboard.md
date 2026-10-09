# OPERATING DASHBOARD — [Tên sản phẩm]

**Loại mô hình:** [B2C / B2B / B2B2C] · **Cập nhật:** 9/10/2026 · Hồ Hoàng Phương Anh – 2A202602460
**NORTH STAR:** Time-to-Screen per CV** — Hỗ trợ team HR giảm thừoi gian trong việc xử lý và lọc CV ứng viên

### Đèn báo sớm (Leading — nhìn hằng ngày/tuần)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn | Báo trước cho |
|---|---|---|---|---|
| Time-to-First-Value (TTFV) ⭐ | Đo (test) | team testing | Log webapp: timestamp đăng ký → lần đầu xem kết quả chấm điểm | Activation Rate |
| Activation Rate | Chưa đo | — | DB: accounts có job_created AND cv_uploaded AND kết_quả_xem ≥1 | Usage Depth |

### Đèn vận hành (Operating — nhìn hằng tuần/tháng)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn | Báo trước cho |
|---|---|---|---|---|
| Time-to-Screen (TTS) | ~180 giây/CV (baseline manual) | 🔴 | Đo thủ công pre-launch | Pilot Retention |
| Usage Depth trong tài khoản | Chưa đo | — | Log hành động/tuần per HR account | Pilot Retention |
|Pilot Retention (W2/W1) | Chưa đo | — | Đếm active company tuần 2 / tuần 1 | MRR/NRR |
| Cost/Job (AI/CV) | Chưa đo (đang build) | — | API billing log: token cost / số CV xử lý | Gross Margin |

### Đèn kết quả (Lagging — nhìn hằng quý)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn |
|---|---|---|---|
| MRR / NRR | 0 (pre-revenue) | — | Stripe / kế toán |
| Gross Margin sau chi phí AI | Chưa tính (cần ARPU thực) | — | (Revenue − COGS_AI − infra) / Revenue |
| NPS sau onboarding | Chưa đo | — | Khảo sát email sau tuần 1 pilot |

### 5 luật quyết định (⏹ = luật dừng)

1. NẾU TTFV > 60 phút TRONG 3 công ty pilot đầu VÀ cả 3 chưa xem được kết quả trong buổi đầu THÌ dừng onboard mới, rút gọn flow (thêm JD template, bỏ rubric bắt buộc) KHÔNG THÌ không mở rộng acquisition.
2. ⏹ NẾU accuracy < 90% TRONG bộ test 200 CV VÀ lỗi ≥2 loại định dạng THÌ DỪNG rollout user mới, fix OCR/parsing trước KHÔNG THÌ không launch tính năng mới cho đến khi accuracy >95%.
3. ⏹ NẾU Cost/Job > 1.500 VNĐ/CV TRONG 2 tuần liên tiếp VÀ volume ≥50 CV/ngày THÌ DỪNG nhận pilot mới, chuyển model nhẹ hơn (Haiku/GPT-4o-mini) KHÔNG THÌ không giữ nguyên model và chờ giá API giảm.
4. NẾU Pilot Retention W2/W1 < 50% TRONG 4 tuần pilot đầu VÀ ≥5 công ty active tuần 1 THÌ họp user interview khẩn (≤1 tuần), hoãn feature mới KHÔNG THÌ không chạy outreach để bù churn.
5. NẾU Usage Depth < 30% SAU 60 ngày go-live VÀ công ty có ≥2 HR account THÌ làm adoption trực tiếp (workshop 30 phút, gán 1 job thật) KHÔNG THÌ không bán thêm module cho tài khoản chưa dùng hết.

### Cổng gác 90 ngày

| Ngày | Metric (1) | Ngưỡng qua cổng | Bằng chứng | Nếu trượt |
|---|---|---|---|---|
| 30 | Activation Rate | ≥60% công ty pilot activated (tạo job + upload CV + xem kết quả) | Screenshot dashboard admin + export log | FIX — rút gọn onboarding flow, thêm JD template mặc định |
| 60 | TTFV + Usage Depth | TTFV < 30 phút trên ≥2 công ty VÀ Usage Depth ≥30% | Log timestamp + hành động per account | PIVOT — phỏng vấn user, cân nhắc đổi flow hoặc segment mục tiêu |
| 90 | Pilot Retention + TTS | Pilot Retention ≥65% VÀ TTS < 10 giây/CV | Export active company data + log xử lý | KILL nếu cả 2 đều trượt sau đã FIX một lần; FIX nếu chỉ 1 chỉ số trượt |
 
**KILL CRITERIA:** Sau 90 ngày, nếu Pilot Retention <40% VÀ TTS >30 giây/CV VÀ đã thực hiện ít nhất 1 vòng FIX — dừng phát triển tính năng mới, đánh giá lại product-market fit và segment mục tiêu
**CHƯA ĐO ĐƯỢC:** TTFV, Activation Rate, Usage Depth, Pilot Retention, Cost/Job, NPS, MRR, Gross Margin (toàn bộ cần đến khi có user thực dùng sản phẩm).
