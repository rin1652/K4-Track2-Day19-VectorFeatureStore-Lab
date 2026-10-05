# Reflection — Lab 19

**Tên:** Nguyễn Đình Phúc
**Cohort:** A20-K4
**Path đã chạy:** both (đã thử qua cả lite và docker)

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

- **Exact queries**: BM25 thắng vì chứa các từ khóa kỹ thuật khớp chính xác (verbatim) với văn bản.
- **Paraphrase queries**: Vector (Semantic) thắng vì không có từ khóa trùng lặp trực tiếp, thuật toán cần hiểu ngữ nghĩa trừu tượng (với Docker path dùng `bge-m3`, hiệu quả tiếng Việt cực kỳ rõ rệt).
- **Mixed queries**: Hybrid (RRF) thắng tuyệt đối vì tận dụng được thế mạnh của cả việc bắt từ khóa chính xác và suy luận ngữ nghĩa của các từ diễn đạt lại.

**Không dùng hybrid khi**: 
1. Hệ thống có yêu cầu cực kỳ khắt khe về độ trễ (latency < 5ms) hoặc chi phí hạ tầng thấp.
2. Dữ liệu tìm kiếm thiên hoàn toàn về tra cứu mã số, ID, tên riêng chính xác (lúc này pure BM25 hoặc exact match database là đủ).

---

## Điều ngạc nhiên nhất khi làm lab này

Sự chênh lệch hiệu năng rất lớn giữa các Embedding Model khi xử lý tiếng Việt (`bge-small-en` vs `bge-m3`). Việc lựa chọn đúng model quyết định sự thành bại của Vector Search hơn là các thuật toán phức tạp phía sau.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
