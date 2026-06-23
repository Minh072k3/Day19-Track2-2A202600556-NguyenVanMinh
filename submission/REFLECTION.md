# Reflection — Lab 19

**Tên:** _Nguyễn Văn Minh_
**Cohort:** _A20_
**Path đã chạy:** _lite_

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

_Answer here._
Trên golden set 50 queries:
- **`exact` queries**: Keyword (BM25) chiếm ưu thế nhất do truy vấn chứa các từ khoá chính xác xuất hiện trong văn bản.
- **`paraphrase` queries**: Semantic (Vector) bắt được các văn bản có nét tương đồng về ngữ nghĩa mặc dù không chung từ vựng. Dù điểm tổng thể của cả 2 thuật toán đều thấp (do dùng model `bge-small-en` trên tiếng Việt), nhưng Vector cho thấy tiềm năng tốt hơn.
- **`mixed` queries**: Hybrid thắng hoàn toàn (100%) vì nó dung hoà được khả năng khớp từ khoá (BM25) và hiểu ý nghĩa (Vector) khi câu truy vấn có cả cụm từ cố định lẫn từ diễn giải.

Tuy nhiên, **KHÔNG** nên dùng hybrid khi:
1. Hệ thống có độ trễ cực thấp (yêu cầu tốc độ) hoặc tài nguyên CPU/Memory yếu (Hybrid cần tính cả BM25 + sinh vector + RRF, chi phí cao hơn).
2. Khi hầu hết truy vấn là mã đơn hàng, ID tĩnh, hoặc từ khoá chính xác (lúc này chỉ cần pure BM25 là đủ và tiết kiệm).
3. Hệ thống thuần semantic nơi từ vựng khác biệt hoàn toàn (lúc này pure Vector hợp lý hơn).

---

## Điều ngạc nhiên nhất khi làm lab này

_(Optional, 1–2 câu)_

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
