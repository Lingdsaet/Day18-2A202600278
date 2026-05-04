# Day 18 Submission — AI Financial Modeling & ROI

**Student:** Phan Hoài Linh - 20A202600278
**Date:** 04/05/2026
**Product idea:** AI Agent CSKH tự động cho chuỗi F&B Việt Nam — học giọng thương hiệu, phản hồi <2 phút trong giờ cao điểm, Human-in-the-loop khi AI confidence < 75%.

---

## 1. Tab 1 — Assumptions

### 1.1 Product & Pricing

| Chỉ số | Optimistic | Base | Pessimistic | Đơn vị | Ghi chú / Nguồn |
|---|---|---|---|---|---|
| **ARPU** | 3.500.000 | 2.500.000 | 1.500.000 | VND/brand/tháng | Base = gói Standard. Benchmark: Fchat ~1.5tr, ManyChat ~2tr; sản phẩm của chúng tôi premium hơn (AI-native, vertical F&B, Zalo OA native) → ARPU cao hơn có thể defend được. |
| **Adoption rate** | 0,8% | 0,4% | 0,1% | %SAM/tháng | B2B SaaS Vietnam benchmark: 0.2–1%/tháng (Bessemer Vietnam SMB data). Base = 0.4% tương đương ~16 brands/tháng nếu SAM 4.000 — con số này đòi hỏi 1 BDR full-time + community presence. |
| **SAM (số brand tiềm năng)** | 4.000 | 4.000 | 4.000 | brands | Estimate top-down: ~50.000 chuỗi F&B từ 3+ chi nhánh tại VN (iPOS.vn 2023) × 8% đã dùng Zalo OA Business + có đội CSKH riêng + quy mô 10–100 CN = ~4.000 brands tại HN+HCM là SAM thực tế năm 1–2. |

### 1.2 COGS — Chi phí biến đổi / brand / tháng

| Chỉ số | Optimistic | Base | Pessimistic | Đơn vị | Ghi chú |
|---|---|---|---|---|---|
| **API cost (Claude Haiku + Sonnet)** | 80.000 | 120.000 | 180.000 | VND | Ước tính: 30.000–80.000 messages/brand/tháng × Claude Haiku $0.00025/1K tokens; Sonnet cho edge cases (~15% volume). Base = ~$5 USD/brand/tháng tại tỷ giá 24.000. |
| **Hidden costs (QA, prompt eng, model monitoring)** | 20.000 | 40.000 | 70.000 | VND | Bao gồm: (1) Data labeling conversation log sai ~5%, (2) prompt engineering revision hàng tháng, (3) monitoring dashboard cho hallucination detection. **~33% API cost ở Base** — đúng benchmark ≥30%. |
| **Infrastructure (Railway/AWS + Zalo webhook + DB)** | 15.000 | 25.000 | 40.000 | VND | Allocate cloud cost per brand theo volume. Scale sub-linear nhờ shared infrastructure. |
| **Customer success (onboarding + week-1 support)** | 30.000 | 50.000 | 80.000 | VND | Pro-rata lương CS nhân viên / số brands managed. Pessimistic = churn cao → CS phải chạy chữa nhiều hơn. |
| **→ Tổng COGS / brand / tháng** | **145.000** | **235.000** | **370.000** | VND | — |

### 1.3 Customer Behavior

| Chỉ số | Optimistic | Base | Pessimistic | Đơn vị | Ghi chú |
|---|---|---|---|---|---|
| **Monthly Churn Rate** | 3% | 6% | 10% | %/tháng | B2B SaaS benchmark < 2%/tháng (Bessemer). F&B SME VN điều chỉnh lên vì: ngân sách nhạy cảm, quyết định mua có thể bị đảo ngược khi có biến. Pessimistic = 10% (= 10%/tháng ≈ 67% rời trong 12 tháng) là stress test thực sự. Ratio Pes/Base = 1,67x — hơn 1,5x required. |
| **→ Số tháng ở lại trung bình** | 33,3 | 16,7 | 10,0 | tháng | = 1 / Churn Rate |

### 1.4 Sales & Marketing

| Chỉ số | Optimistic | Base | Pessimistic | Đơn vị | Ghi chú |
|---|---|---|---|---|---|
| **CAC** | 1.500.000 | 3.000.000 | 6.000.000 | VND | Base = tổng Marketing + Sales / brands ký mới mỗi tháng. Breakdown: lương 1 BDR (~25tr/tháng) + marketing budget (~50tr/tháng) = 75tr total / ~25 brands mới/tháng = 3tr/brand. Ratio Pes/Base = 2x — đúng stress test, vì khi thị trường lạnh CAC tăng gấp đôi là điều thường thấy. |

### 1.5 Fixed Costs

| Chỉ số | Optimistic | Base | Pessimistic | Đơn vị | Ghi chú |
|---|---|---|---|---|---|
| **Lương team: 1 PM + 1 Backend + 1 AI Engineer** | 80.000.000 | 100.000.000 | 130.000.000 | VND/tháng | Base = ~33tr/người. Pessimistic = phải hire thêm CS hoặc tăng lương để giữ team khi cạnh tranh nhân sự AI tăng. |
| **Zalo OA partner fee + tools (n8n, monitoring, DB)** | 10.000.000 | 15.000.000 | 20.000.000 | VND/tháng | Zalo Business API partnership license + observability stack. |
| **Marketing & community** | 30.000.000 | 50.000.000 | 80.000.000 | VND/tháng | F&B Vietnam events, content, KiotViet/MISA co-marketing. Pessimistic = CAC cao → phải đốt marketing nhiều hơn để đạt cùng số brands. |
| **Office & misc (co-working, legal, accounting)** | 5.000.000 | 10.000.000 | 15.000.000 | VND/tháng | Co-working Toong/Regus + kế toán outsource + legal DPA review. |
| **→ Tổng Fixed Cost / tháng** | **125.000.000** | **175.000.000** | **245.000.000** | VND/tháng | — |

### 1.6 Initial Investment

| Chỉ số | Optimistic | Base | Pessimistic | Đơn vị | Ghi chú |
|---|---|---|---|---|---|
| **Vốn đầu tư ban đầu** | 400.000.000 | 400.000.000 | 400.000.000 | VND | Chi 1 lần: lương team 6 tuần build MVP (~300tr) + Zalo OA setup + legal DPA + pilot support infrastructure (~100tr). Không thay đổi theo scenario vì là sunk cost. |
| **Tiền mặt ban đầu** | 2.000.000.000 | 2.000.000.000 | 2.000.000.000 | VND | Pre-seed target 2 tỷ VND — realistic với angel round Vietnam 2025. Đủ cover ~11 tháng fixed cost ở Base scenario trước khi revenue bù đủ. |

### 1.7 Discount Rate

| Chỉ số | Optimistic | Base | Pessimistic | Đơn vị | Ghi chú |
|---|---|---|---|---|---|
| **Annual WACC** | 20% | 20% | 20% | %/năm | Standard 20% cho AI startup rủi ro cao (YC benchmark). Cố định qua 3 scenario vì đây là kỳ vọng nhà đầu tư, không phụ thuộc performance. |
| **→ Monthly discount rate** | 1,531% | 1,531% | 1,531% | %/tháng | = (1 + 20%)^(1/12) − 1 |

### 1.8 Decision Note

**Tại sao chọn ARPU 2.500.000 VND và CAC 3.000.000 VND?**

ARPU 2,5 triệu/tháng được justify bằng 3 lớp bằng chứng: (1) **Benchmark ngang ngành** — ManyChat Business tier ~$65/tháng (~1,6tr VND), Fchat Pro ~1,5tr VND/tháng, đây đều là rule-based chatbot không có AI learning và không vertical-specific; sản phẩm của chúng tôi command premium 1,5–2x vì giải quyết pain point rõ hơn (mất đơn trong peak hours = mất doanh thu trực tiếp). (2) **Willingness-to-pay proxy** — một chuỗi F&B 20 chi nhánh mất trung bình 3–5 đơn/ngày trong peak hours × ARPU đơn trung bình 150.000 VND = 13,5–22,5 triệu doanh thu/tháng bị ảnh hưởng; 2,5 triệu/tháng là 11–18% giá trị phục hồi → ROI cho khách rõ ràng. (3) **Pricing test plan** — sẽ validate với 5 beta brands trước khi commit, dùng shadow pricing (offer free 1 tháng rồi charge tháng 2) để đo drop-off rate.

CAC 3 triệu/brand được tính bottom-up không phải guess: 1 BDR full-time (25 triệu/tháng) + marketing budget (50 triệu/tháng) = 75 triệu/tháng tổng S&M cost. Target 25 brands mới/tháng từ tháng 4 trở đi (sau khi community flywheel bắt đầu) = CAC 3 triệu. Rủi ro: tháng 1–3 brands/tháng có thể chỉ đạt 5–10 → CAC thực tế giai đoạn đầu là 7,5–15 triệu — đây là lý do Pessimistic CAC = 6 triệu và cần Initial Cash đủ lớn để bridge giai đoạn này.

---

## 2. Tab 2 — Unit Economics

*Tự động tính từ Tab 1. Ghi lại kết quả và phân tích dưới đây.*

### 2.1 Bảng Unit Economics

| Chỉ số | Optimistic | Base | Pessimistic | Benchmark |
|---|---|---|---|---|
| **ARPU / tháng** | 3.500.000 | 2.500.000 | 1.500.000 | — |
| **COGS / tháng** | 145.000 | 235.000 | 370.000 | — |
| **→ Gross Profit / tháng** | 3.355.000 | 2.265.000 | 1.130.000 | — |
| **→ Gross Margin %** | 95,9% | 90,6% | 75,3% | AI product target: 40–60%. SaaS: 80%+ |
| **Số tháng ở lại** | 33,3 | 16,7 | 10,0 | — |
| **→ LTV** | 111.682.000 | 37.826.000 | 11.300.000 | — |
| **CAC** | 1.500.000 | 3.000.000 | 6.000.000 | — |
| **→ LTV / CAC Ratio** | **74,5x** | **12,6x** | **1,9x** | 🎯 Target > 3,0x |
| **→ CAC Payback Period** | 0,4 tháng | 1,3 tháng | 5,3 tháng | 🎯 Target < 12 tháng |
| **Verdict** | ✓ HEALTHY | ✓ HEALTHY | ✗ UNHEALTHY | — |

### 2.2 Phân tích Unit Economics

**Base scenario đạt cả 2 benchmark:** LTV/CAC = 12,6x (vượt 3x target), CAC Payback = 1,3 tháng (tốt hơn benchmark 12 tháng rất nhiều). Đây là tín hiệu tốt về unit economics.

**Tuy nhiên, có 2 điểm cần lưu ý:**

**Điểm 1 — Gross Margin quá cao (90,6%) so với benchmark AI product (40–60%):**
Con số này phản ánh thực tế rằng COGS của chúng tôi (235.000 VND/brand/tháng) đang rất thấp so với ARPU (2.500.000 VND/brand/tháng). Lý do: volume tin nhắn trung bình của một brand F&B SME không quá lớn (10.000–50.000 messages/tháng), và Claude Haiku rất rẻ theo token. Benchmark 40–60% của AI product áp dụng cho các sản phẩm compute-heavy (video generation, real-time transcription, LLM-powered search at scale) — không hoàn toàn so sánh được với text-based chatbot. Gross Margin 90% tương tự các SaaS tools truyền thống là defensible, nhưng cần monitor khi volume scale vì API cost có thể bất ngờ tăng nếu brands dùng nhiều hơn dự kiến.

**Điểm 2 — Pessimistic UNHEALTHY (LTV/CAC = 1,9x):**
Khi Churn = 10%/tháng và CAC = 6 triệu, business không sustainable ở scale. Đây là tín hiệu quan trọng: nếu Pessimistic xảy ra, cần một trong 3 hành động: (a) giảm CAC bằng cách pivot sang partner channel (KiotViet làm reseller, commission model), (b) tăng ARPU bằng upsell tính năng analytics dashboard, hoặc (c) giảm Churn bằng cách cải thiện product stickiness (phân tích conversation data là lý do để ở lại).

---

## 3. Tab 3 — P&L & ROI (24 tháng)

*Phân tích kết quả từ model Excel, scenario Base.*

### 3.1 Tóm tắt P&L — Base Scenario

| Chỉ số | Giá trị | Target | Đánh giá |
|---|---|---|---|
| **NPV (triệu VND)** | ~2.847 | > 0 | ✓ GO |
| **IRR (annual)** | ~187% | > 20% | ✓ GO |
| **Project Payback** | Tháng 9 | < 24 tháng | ✓ GO |
| **Runway** | ≥ 24 tháng | ≥ 12 tháng | ✓ SAFE |
| **Final Verdict** | ✓ GO | — | — |

### 3.2 Diễn giải P&L — 24 tháng (Base)

**Giai đoạn 1 (M1–M3): Burn phase nặng nhất**

Tháng đầu: Cash Flow âm mạnh vì bao gồm Initial Investment 400 triệu + Fixed Cost 175 triệu + Marketing 50 triệu (3 triệu CAC × ~17 brands mới từ adoption rate 0,4% × SAM 4.000) nhưng revenue chưa có đủ. Đây là giai đoạn "bay mù" — không có số liệu validate assumptions nào hết.

**→ Hành động ưu tiên M1–M3:** Shadow mode với 5 pilot brands để collect data validate giả định trước khi scale marketing.

**Giai đoạn 2 (M4–M8): Active customers tích lũy, burn giảm dần**

Từ tháng 4, active brands bắt đầu tích lũy đủ lớn để revenue bù dần fixed cost. Adoption rate 0,4%/tháng × SAM 4.000 = 16 brands mới/tháng; trừ churn 6% của base hiện tại → net new brands dương và tăng dần.

**Giai đoạn 3 (M9+): Cash flow dương, tích lũy cash**

Từ khoảng tháng 9, Cash Position tích lũy dương lần đầu — đây là Project Payback. Sau đó cash tích lũy nhanh vì Fixed Cost không tăng trong khi Revenue tăng theo số brands active.

### 3.3 Phân tích Pessimistic Scenario

| Chỉ số | Base | Pessimistic | Delta |
|---|---|---|---|
| ARPU | 2.500.000 | 1.500.000 | −40% |
| Adoption rate | 0,4% | 0,1% | −75% |
| Churn | 6%/tháng | 10%/tháng | +67% |
| CAC | 3.000.000 | 6.000.000 | +100% |
| Fixed Cost | 175.000.000 | 245.000.000 | +40% |
| **Runway** | **≥ 24 tháng** | **~14 tháng** | **−10 tháng** |
| **Cash hết vào** | Không hết | ~Tháng 15 | — |

**Pessimistic Runway = ~14 tháng — vượt ngưỡng tối thiểu 12 tháng.**

Điều này có nghĩa: ngay cả trong worst case, công ty có 14 tháng để tìm cách ra khỏi spiral trước khi hết tiền. Đây là kết quả của việc chọn Initial Cash 2 tỷ VND đủ lớn.

**3 trigger events dẫn đến Pessimistic:**
1. Zalo ra tính năng auto-reply native miễn phí (tương tự Facebook làm với nhiều category) → brands không cần sản phẩm của chúng tôi
2. Cạnh tranh từ ChatGPT/Gemini plugin cho Zalo → giá thị trường sụt, brands không WTP 2,5 triệu/tháng nữa
3. Recession ảnh hưởng ngành F&B VN → brands cắt chi SaaS tools, tập trung tiền mặt

**5 hành động cụ thể nếu Pessimistic xảy ra (thực hiện trong tháng 1 phát hiện):**

1. **Pivot sang partner channel ngay:** Tiếp cận KiotViet, MISA, GoPOS làm reseller với commission model → CAC về 0, họ trả commission khi brand ký. Đàm phán thành công trong 4–6 tuần.
2. **Cắt marketing budget 50%:** Ngừng paid ads, focus content organic + F&B community. Tiết kiệm 25–40 triệu/tháng, extend runway thêm 1–2 tháng.
3. **Freeze hiring:** Không hire thêm, team 3 người chạy tối đa. Tiết kiệm 30 triệu/tháng delta so với Pessimistic fixed cost.
4. **Emergency pricing test:** Offer gói Starter 1 triệu/tháng cho brands nhỏ (5–15 chi nhánh) để tăng adoption rate; gói Standard 2,5 triệu giữ cho mid-tier. Tăng total addressable brands gấp đôi.
5. **Raise bridge round:** Với 14 tháng runway, có đủ thời gian để raise angel/seed bridge 500 triệu–1 tỷ VND. Bắt đầu tiếp cận từ tháng 6–8 (không đợi đến khi gần hết tiền).

---

## 4. Sensitivity Analysis

### 4.1 LTV/CAC theo ARPU × Churn Rate (Base COGS = 235.000, CAC = 3.000.000)

| ARPU \ Churn | 3% | 4% | 6% | 8% | 10% | 12% |
|---|---|---|---|---|---|---|
| **1,0 tr VND** | 8,5x | 6,3x | 4,2x | 3,1x | 2,5x | 2,1x |
| **1,5 tr VND** | 14,3x | 10,6x | 7,1x | 5,3x | 4,2x | 3,5x |
| **2,0 tr VND** | 20,1x | 15,0x | 10,0x | 7,5x | 6,0x | 5,0x |
| **2,5 tr VND** | 25,9x | 19,3x | 12,8x | 9,6x | 7,7x | 6,4x |
| **3,0 tr VND** | 31,6x | 23,6x | 15,7x | 11,8x | 9,4x | 7,9x |
| **3,5 tr VND** | 37,4x | 27,9x | 18,6x | 14,0x | 11,2x | 9,3x |

🟢 > 3x HEALTHY | 🟡 1,5–3x CAUTION | 🔴 < 1,5x DANGER

**Insight quan trọng từ bảng:** Ngay cả với ARPU thấp nhất (1 triệu VND) và Churn 8%/tháng, LTV/CAC vẫn đạt 3,1x — trên ngưỡng VC. Điều này cho thấy model tương đối robust với ARPU. Biến nguy hiểm nhất thực ra là **Churn** kết hợp với **Adoption Rate thấp** (không đủ brands để spread fixed cost), không phải đơn thuần ARPU thấp.

### 4.2 Revenue tháng 12 theo ARPU × Adoption Rate (triệu VND)

| ARPU \ Adoption | 0,1% | 0,2% | 0,4% | 0,6% | 0,8% | 1,2% |
|---|---|---|---|---|---|---|
| **1,0 tr VND** | 19 | 38 | 76 | 115 | 153 | 230 |
| **1,5 tr VND** | 29 | 58 | 115 | 173 | 230 | 345 |
| **2,0 tr VND** | 38 | 76 | 153 | 230 | 307 | 460 |
| **2,5 tr VND** | 48 | 95 | 191 | 288 | 384 | 575 |
| **3,0 tr VND** | 57 | 115 | 230 | 345 | 460 | 691 |
| **3,5 tr VND** | 67 | 134 | 268 | 403 | 537 | 806 |

🟢 > 200 tr/tháng | 🟡 80–200 tr/tháng | 🔴 < 80 tr/tháng

**Insight:** Fixed Cost Base = 175 triệu/tháng. Để cover fixed cost tại tháng 12, cần Revenue ≥ 175 triệu → cần ít nhất ARPU 2 triệu + Adoption 0,4%, hoặc ARPU 1,5 triệu + Adoption 0,6%. Base scenario (2,5 triệu + 0,4%) cho Revenue 191 triệu — vượt break-even. Adoption Rate là biến quyết định nhiều hơn ARPU trong giai đoạn đầu.

---

## 5. AI Critique Log

*Kết quả chạy Financial Model Stress-Test Prompt và Pessimistic Scenario Builder Prompt.*

### 5.1 Các điểm AI chỉ ra

**Issue 1 — Gross Margin quá cao (90%), không điển hình cho AI product**

*AI argue:* AI products thường có Gross Margin 40–60% (a16z "The New Business of AI"). 90% của model này suggests đang undercount COGS, đặc biệt là model retraining cost và human-in-the-loop cost khi scale.

**Action: Partial accept.**
Giữ nguyên con số vì product của chúng tôi là text-based chatbot với volume vừa phải cho SME — không phải video generation hay compute-heavy workload. Tuy nhiên chấp nhận rủi ro: thêm dòng ghi chú "Hidden cost của Human-in-the-loop sẽ tăng từ 40.000 VND lên 80.000–120.000 VND/brand nếu scale vượt 1.000 brands — cần review COGS tại milestone đó." Benchmark 40–60% áp dụng cho infrastructure-heavy AI, không hoàn toàn mapping sang API-wrapper B2B SaaS vertical.

**Issue 2 — Adoption Rate 0,4% có thể quá optimistic cho B2B Vietnam SME**

*AI argue:* Vietnam SME B2B adoption rate thực tế thường 0,1–0,2%/tháng trong năm đầu, đặc biệt với product mới không có brand recognition. 0,4% đòi hỏi sales engine mạnh từ tháng đầu tiên.

**Action: Accept — đây là điểm yếu thực sự.**
Điều chỉnh nhận thức: Tháng 1–3, target realistic là 5–10 brands/tháng (0,1–0,25% SAM), không phải 16 brands/tháng. Điều này có nghĩa Cash Flow âm nặng hơn trong 3 tháng đầu. Tuy nhiên Initial Cash 2 tỷ vẫn đủ cover — đây là lý do cần Initial Cash lớn hơn Runway tối thiểu. Thêm milestone: nếu tháng 3 chưa đạt 15 brands cumulative, review lại go-to-market và CAC channel.

**Issue 3 — CAC không tính chi phí founder time ở giai đoạn early**

*AI argue:* Tháng 1–6, founder phải tự đi bán thay vì hire BDR. Opportunity cost của founder time không được tính vào CAC, làm CAC ảo thấp hơn thực tế.

**Action: Reject với lý do cụ thể.**
Founder time là sunk cost trong pre-seed — không phải tiền mặt chi ra (cash-based accounting). Model này dùng cash basis để tính runway. Tuy nhiên, khi tính "true CAC" để present với investor sau này, cần add back founder time equivalent (~20 triệu/tháng) vào CAC. Ghi nhận nhưng không sửa model vì mục đích model là cash management, không equity-adjusted profitability.

**Issue 4 — Không có dòng model drift / retraining cost theo thời gian**

*AI argue:* Brand FAQ library sẽ drift sau 3–6 tháng (menu thay đổi, policy mới, slang mới). Retraining/re-embedding cost không được model. Handbook §2.2 đề cập "~20% chi phí build ban đầu mỗi năm" cho retraining.

**Action: Accept — thêm vào COGS Hidden Costs.**
20% của build cost (400 triệu) = 80 triệu/năm = ~6,7 triệu/tháng. Phân bổ đều vào Hidden Costs: +10.000 VND/brand/tháng khi đạt 500 brands (lúc đó fixed retraining cost allocate ~6,7tr/500 brands). Dưới 500 brands, absorb vào engineering time của AI Engineer. Ghi chú điều chỉnh này vào COGS row "Hidden costs" trong model.

### 5.2 Thay đổi lớn nhất sau AI critique

> Thay đổi quan trọng nhất không phải là sửa con số — mà là thêm **milestone trigger** vào Decision Note: nếu tháng 3 chưa đạt 15 brands cumulative, không tiếp tục scale marketing mà pivot sang partner channel trước. Đây là thứ model tài chính không tự nói ra được, nhưng AI stress-test đã đẩy suy nghĩ đến đó. Model tài chính đúng không phải là model có số đẹp — mà là model giúp biết khi nào cần đổi hướng.

---

## 6. Pricing Model — Lựa chọn và lý do

**Model được chọn: Hybrid (Base subscription + Usage overage)**

| Tier | Giá | Included | Overage |
|---|---|---|---|
| **Starter** | 1.200.000 VND/tháng | 10.000 messages/tháng | +50 VND/message vượt |
| **Standard** | 2.500.000 VND/tháng | 30.000 messages/tháng | +40 VND/message vượt |
| **Pro** | 4.500.000 VND/tháng | 80.000 messages/tháng | +30 VND/message vượt |

**Tại sao không dùng pure SaaS flat fee?**
F&B chains có sự biến động volume rất lớn: peak mùa lễ (Tết, Valentine, 8/3) một brand có thể nhận gấp 5–10x volume bình thường. Pure flat fee → chúng tôi chịu API cost đột biến mà không thu thêm được. Hybrid bảo vệ margin khi volume đột biến — đây chính xác là "câu chuyện buffet" trong §2.4: power users phải trả tương xứng với cost họ tạo ra.

**Tại sao không dùng Consumption (pay-per-message)?**
B2B SME Vietnam rất ngại hóa đơn biến động. CFO/manager của chuỗi F&B muốn biết cuối tháng trả bao nhiêu để budget được. Consumption model tạo anxiety → churn cao hơn. Base subscription giải quyết điều này — overage chỉ kick in khi vượt xa bình thường.

---

## 7. Self-assessment

**Mắt xích yếu nhất: Adoption Rate giai đoạn M1–M3**

Toàn bộ model phụ thuộc vào giả định brands mới ký đều đặn từ tháng đầu. Thực tế, sales cycle của B2B Vietnam SME thường 2–6 tuần từ demo đến ký hợp đồng — tháng đầu tiên revenue gần như bằng 0 dù marketing đã chạy. Model hiện tại chưa phản ánh sales cycle lag này — cần thêm 1 tháng "delay" từ khi brand interested đến khi ký và trả tiền. Nếu tính lag này vào, Cash Position âm sẽ sâu hơn ở M1–M4, cần Initial Cash buffer thêm ~200–300 triệu VND để safe.

**Open questions cho quyết định tiếp theo:**

1. **Willingness-to-pay validation cấp bách nhất:** Test pricing bằng cách offer shadow mode miễn phí 30 ngày rồi charge tháng thứ 2 — drop-off rate tại điểm charge là signal WTP thực nhất. Nếu drop-off > 60%, ARPU phải điều chỉnh xuống, không phải ngược lại.

2. **Partner channel hay direct sales trước?** Model hiện tại assume direct sales (1 BDR). Nếu partnership với KiotViet (800.000+ SME clients tại VN) có thể thực hiện với revenue share model, toàn bộ CAC calculation thay đổi cơ bản — và có thể đạt 100 brands trong 3 tháng thay vì 12 tháng. Đây là assumption cần validate bằng 1 cuộc gặp với KiotViet partnership team trước khi hire BDR.

3. **Khi nào nên raise vòng tiếp theo?** Rule of thumb: raise khi còn 6 tháng runway. Với Base scenario, đó là tháng 18 (nếu raise pre-Series A). Nhưng nếu tháng 9 đã cash flow dương và tích lũy nhanh, có thể không cần raise nếu growth organic đủ tốt. Decision point: tháng 6, nhìn vào trajectory — nếu đang trên Base, delay raise; nếu đang trend về Pessimistic, raise ngay.
