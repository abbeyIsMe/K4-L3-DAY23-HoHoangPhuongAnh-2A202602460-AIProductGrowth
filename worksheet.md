# Worksheet — [Tên sản phẩm]

Họ tên: Hồ Hoàng Phương Anh · MSSV: 2A202602460 · Ngày làm: 9/10/2026

## Trạm 1 — Loại mô hình

**Câu chốt loại:** Chúng tôi là B2B vì sản phẩm AI hỗ trợ tuyển dụng và sàng lọc CV có end user là HR, HRM trong doanh nghiệp vueaf và nhỏ -> Business to Business, doanh nghiệp sẽ là người trả tiền 

**Bảng đèn §3 của loại mình** (ghi đủ mọi đèn trong bảng):

| Đèn | ✅ / 🔧 / ❌ | Số nằm ở đâu / cần gì để đo |
|---|---|---|
| Time-to-first-value (TTFV) | ✅ | Số lượng CV được rút gọn mà HR phải lọc trong 100 CV đưuucj gửi về |
| Pipeline coverage | ❌ | Chưa có pipeline bán, cần show và tìm cơ hội bán |
| % deal chết ở security/procurement | ❌ | Chưa có deal thật — đo khi bắt đầu bán chính thức |
| POC → paid | 🔧 | Đếm thủ công: số công ty pilot chuyển thành trả tiền / tổng pilot |
| Sales cycle (tuần) | ❌ | Chưa có deal — ghi ngày từ lúc tiếp cận → ký |
| Usage depth trong tài khoản | 🔧 | Log: % HR account có hành động thật trong tuần (upload CV, xem điểm, gửi email) |
| Chi phí triển khai ÷ ACV | 🔧 | Ước tính giờ công onboarding × đơn giá + chi phí tích hợp / ACV mục tiêu |
| Tập trung doanh thu | ❌ | Chưa có doanh thu — đo khi có ≥3 khách trả tiền |
| NRR (Net Revenue Retention) | ❌ | Cần ≥1 năm vận hành |
| Gross Margin | 🔧 | (Doanh thu − chi phí API − infra) / Doanh thu — cần pricing model chính thức |
| CAC payback | ❌ | Cần CAC thật và ARPU thật — đo sau khi có ≥3 khách trả tiền |

## Trạm 2 — Thẻ đèn

**North Star:** … — hiện tại … — mục tiêu …

| # | Tầng (L/O/G) | Đèn | Định nghĩa (đếm gì · **không** đếm gì) | Công thức | Nhịp · ai lấy số | Báo trước cho |
|---|---|---|---|---|---|---|
| 1 | L | Time-to-first-value (TTFV) ⭐| | | | |
| 2 | L | Activation Rate | % công ty pilot đã tạo ≥1 Job VÀ upload ≥1 CV VÀ xem kết quả chấm điểm · **Không đếm** tài khoản chỉ đăng nhập/xem demo | Activated_accounts / Total_pilot_accounts × 100 | Hằng tuần · dashboard admin | Usage Depth (#4) |
| 3 | O | Time-to-Screen (TTS)| Giây từ lúc upload CV → hiển thị điểm + nhãn (Phù hợp cao/Tiềm năng/Không phù hợp) · **Không đếm** thời gian HR đọc kết quả sau khi hiển thị | avg(Timestamp_hiển_thị_kết_quả − Timestamp_upload) | Hằng tuần · log tự động | Pilot Retention (#5) |
| 4 | O | Usage Depth trong tài khoản | % HR account trong công ty có ≥1 hành động thật/tuần (upload CV, xem điểm, gửi email nháp) · **Không đếm** đăng nhập không có hành động | (HR_accounts_có_hành_động) / Total_HR_accounts × 100 | Hằng tuần · log | Pilot Retention (#5) |
| 5 | O | Pilot Retention (W2/W1) | % công ty pilot còn active ở tuần 2 so với tuần 1 (có ≥1 HR dùng app) · **Không đếm** công ty chỉ đăng nhập check lại tài khoản | Active_W2 / Active_W1 × 100 | Hằng tuần trong pilot | NRR/MRR (#7) |
| 6 | O | Cost/Job (chi phí AI/CV) | Tổng chi phí token AI (OCR + Embedding + Scoring + Email draft) để xử lý 1 CV · **Không đếm** chi phí infra cố định hay nhân sự | Σ(token_cost_per_cv) = Vision_API + Embedding_API + Chat_API per CV | Hằng tuần · tổng hợp từ API billing log | Gross Margin (#8) |
| 7 | G | MRR / NRR | MRR: tổng doanh thu định kỳ tháng từ gói trả phí · NRR: MRR tháng hiện tại (bao gồm mở rộng) / MRR tháng trước của cùng nhóm khách · Không đếm doanh thu một lần | MRR = Σ(subscription_value); NRR = MRR_t / MRR_(t-1) × 100 | Hằng tháng · kế toán | LTV, Payback (#8) |
| 8 | G | Gross Margin sau chi phí AI | (Doanh thu − chi phí token AI − chi phí infra) / Doanh thu ·Không đếm khấu trừ nhân sự | (Revenue − COGS_AI − COGS_infra) / Revenue × 100 | Hằng quý | Scale decision, Runway |

Đèn chi phí AI là đèn số: 6 Cost/Job = chi phí token AI (OCR + Embedding + Scoring + Email draft) / 1 CV xử lý thành công. Ngưỡng: 🟢 <500 VNĐ/CV · 🟡 500–1.500 VNĐ · 🔴 >1.500 VNĐ

## Trạm 3 — Ngưỡng

| # | Đèn | 🟢 | 🟡 | 🔴 | Nguồn [BM]/[MH]/[TB] | Lý do (1 câu) · ngày kiểm tra nếu [BM] |
|---|---|---|---|---|---|---|
| 1 | TTFV | <30 phút | 30–60 phút | >60 phút | [MH] Suy từ mục tiêu Pilot Retention ≥65%: nếu HR mất >60' mới thấy giá trị lần đầu, xác suất không quay lại tuần 2 rất cao — xem [MH] 1 | TTFV >60' = onboarding bị gãy trước khi HR hiểu sản phẩm làm được gì |
| 2 | Activation Rate | ≥60% | 40–59% | <40% | [BM] Median B2B SaaS activation 45–60% (Product-led Growth Collective, 2024 — kiểm tra lại Q1/2027) | Dưới 40% cho thấy bước đầu tiên (tạo Job → upload CV) bị ma sát quá lớn |
| 3 | Time-to-Screen (TTS) | <10 giây/CV | 10–30 giây | >30 giây | [MH] Suy từ mục tiêu giảm ≥70% so với baseline 3–5 phút/CV (PRD): 70% của 180 giây = 54 giây → mục tiêu <10 giây là vượt kỳ vọng | TTS >30 giây không đủ khác biệt so với manual để HR chọn dùng app thay vì tự đọc |
| 4 | Usage Depth | ≥60% | 30–59% | <30% | [BM] Usage depth B2B SaaS — ICONIQ 2026: đây là ngưỡng tham chiếu thực hành; <30% sau 60 ngày là tín hiệu churn sớm | Nếu <30% HR trong 1 công ty dùng thật, quyết định gia hạn sẽ nghiêng về không gia hạn |
| 5 | Pilot Retention | ≥65% | 50–64% | <50% | [TB] Mục tiêu tự đặt trong PRD — đo trực tiếp trên 10 công ty pilot (tự đo baseline) | Đây là cam kết chỉ số trong PRD; <50% là tín hiệu kill cho sprint tiếp theo |
| 6 | Cost/Job (AI/CV) | <500 VNĐ/CV | 500–1.500 VNĐ | >1.500 VNĐ | [MH] Suy từ ARPU ước tính và gross margin mục tiêu — xem [MH] 2 | Cost/CV >1.500 VNĐ → gross margin <70% → nguy cơ không có margin để scale khi volume tăng |
| 7 | NPS sau onboarding | ≥30 | 0–29 | <0 | [BM] B2B SaaS early-stage NPS benchmark 20–40 (Delighted/Gainsight, 2024 — kiểm tra lại Q1/2027) | NPS âm nghĩa Detractor > Promoter — word-of-mouth sẽ phá acquisition trước khi bắt đầu |
| 8 | Gross Margin | ≥55% | 40–54% | <40% | [BM] AI-native SaaS: 45% (2025) → 53% (2026E) (ICONIQ State of AI 2026) | Dưới 40% thì mô hình không scale được vì chi phí AI + infra ăn hết biên |

### Phụ lục [MH] — phép tính (≥2)

**[MH] 1 — <tên đèn>**

**Đầu vào (từ PRD + ước tính pilot):**
- Mục tiêu Pilot Retention ≥65% (= ≥65% công ty pilot còn active tuần 2)
- Pilot scale: 10 công ty, mỗi công ty 2 HR = 20 user
- Giả định: HR không thấy giá trị trong buổi đầu → 80% không quay lại (quy luật SaaS onboarding)
**Phép tính:**
- Nếu TTFV >60 phút → HR chưa thấy kết quả trong buổi đầu → xác suất active tuần 2 ~20%
- Để Retention ≥65%, cần TTFV đủ ngắn để HR "xong việc" trong 1 phiên ≤30 phút
- Thực nghiệm: tạo tài khoản + tạo Job + upload 1 CV + xem kết quả = chuỗi 4 bước
- Mỗi bước tối đa 7–8 phút → tổng ~30 phút là ngưỡng HR còn kiên nhẫn
- Ngưỡng 🟢 <30 phút đảm bảo HR hoàn thành chuỗi trong 1 phiên, tạo "aha moment"
**Kết quả → 🟢 <30 phút · 🟡 30–60 phút · 🔴 >60 phút**
 

**[MH] 2 — <tên đèn>**

**Đầu vào:**
- ARPU mục tiêu: giả định gói SME 500.000 VNĐ/tháng/công ty *(cần team xác nhận pricing chính thức)*
- Trung bình 1 công ty nhỏ xử lý ~100 CV/tháng (ước tính dựa trên pilot 10 công ty)
- Mục tiêu Gross Margin ≥55% sau chi phí AI + infra (không tính nhân sự)
- Chi phí AI/CV gồm: Vision API (OCR) + Embedding + Chat (GPT-4o-mini hoặc Claude Haiku) + Email draft
**Phép tính:**
- Revenue/CV = 500.000 / 100 = **5.000 VNĐ/CV**
- COGS_AI tối đa để giữ GM ≥55%: 5.000 × (1 − 0.55) = **2.250 VNĐ/CV** (mức trần tuyệt đối)
- Ngưỡng 🟢 <500 VNĐ: margin ≥90% — an toàn scale, budget còn để tối ưu
- Ngưỡng 🟡 500–1.500 VNĐ: margin 70–90% — cần theo dõi khi volume tăng
- Ngưỡng 🔴 >1.500 VNĐ: margin <70% — gần trần 2.250 VNĐ, cần review model ngay
**Kết quả → 🟢 <500 VNĐ/CV · 🟡 500–1.500 VNĐ · 🔴 >1.500 VNĐ**


## Trạm 4 — 5 luật quyết định

Đánh dấu ⏹ cho luật dừng (cần ≥2).

1. NẾU TTFV > 60 phút TRONG 3 công ty pilot đầu VÀ cả 3 chưa xem được kết quả trong buổi đầu THÌ dừng onboard mới, rút gọn flow (thêm JD template, bỏ rubric bắt buộc) KHÔNG THÌ không mở rộng acquisition.
2. ⏹  NẾU accuracy < 90% TRONG bộ test 200 CV VÀ lỗi ≥2 loại định dạng THÌ DỪNG rollout user mới, fix OCR/parsing trước KHÔNG THÌ không launch tính năng mới cho đến khi accuracy >95%.
3. ⏹ NẾU Cost/Job > 1.500 VNĐ/CV TRONG 2 tuần liên tiếp VÀ volume ≥50 CV/ngày THÌ DỪNG nhận pilot mới, chuyển model nhẹ hơn (Haiku/GPT-4o-mini) KHÔNG THÌ không giữ nguyên model và chờ giá API giảm.

4. NẾU Pilot Retention W2/W1 < 50% TRONG 4 tuần pilot đầu VÀ ≥5 công ty active tuần 1 THÌ họp user interview khẩn (≤1 tuần), hoãn feature mới KHÔNG THÌ không chạy outreach để bù churn.

5. NẾU Usage Depth < 30% SAU 60 ngày go-live VÀ công ty có ≥2 HR account THÌ làm adoption trực tiếp (workshop 30 phút, gán 1 job thật) KHÔNG THÌ không bán thêm module cho tài khoản chưa dùng hết.
