# Phiếu QC 1 — Road v1.0

**Lô được kiểm (học viên):** Vũ Đức Quang  
**Người kiểm (học viên):** Doãn Thị Phương Thảo  
**Ngày:** 21/11/2026  
**Phiên bản guideline:** Road v1.0  
**File được kiểm:** `vuducquang-front.zip`, `vuducquang-fisheye.zip`.   
**Số ảnh kiểm:** 28 ảnh (16 Front + 12 Fisheye; kiểm tra bằng lint)  
**Số nhãn đã kiểm (shape + tag):** 222 shapes + 80 tag entries trong XML.

## Tổng hợp theo mã

| Mã | Loại lỗi | Số mục kiểm | Số lỗi / phát hiện | Mức |
|---|---|---:|---:|---|
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 28 ảnh | 1 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 24 vị trí | 8 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 6 lane fisheye | 3 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 32 lane | 0 cảnh báo lint | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 32 lane | 0 cảnh báo lint | chính |
| QC1-06 style, color, kind | sai thuộc tính | 32 lane | 0 cảnh báo lint | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 44 drivable | 0 cảnh báo lint | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 41 traffic_light | 0 cảnh báo lint | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 47 traffic_sign | 0 cảnh báo lint | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 47 traffic_sign | 4 cảnh báo box thấp | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 68 shapes fisheye | 9 cảnh báo/gợi ý | chính |
| QC1-12 file | lỗi file | 28 ảnh | 8 cảnh báo | nhẹ / nặng |

*Ghi chú: Số mục kiểm là số lượng đối tượng/vị trí suy ra từ XML theo từng nhóm. Số 0 cảnh báo lint không có nghĩa đã kiểm thủ công và xác nhận không lỗi. Các cảnh báo box thấp và edge_zone cần xem lại bằng mắt.*

## Danh sách lỗi (mỗi lỗi một dòng)

| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
|---:|---|---|---|---|---|
| 1 | QC1-01 | B02 | tag:camera | Nặng | Thiếu tag camera |
| 2 | QC1-02 | A03 | lane | Nặng | Thiếu L1 |
| 3 | QC1-02 | A05 | lane | Nặng | Thiếu L1 |
| 4 | QC1-02 | A05 | lane | Nặng | Thiếu R1 |
| 5 | QC1-02 | A06 | lane | Nặng | Thiếu L1 |
| 6 | QC1-02 | A06 | lane | Nặng | Thiếu R1 |
| 7 | QC1-02 | A07 | lane | Nặng | Thiếu L1 |
| 8 | QC1-02 | A09 | lane | Nặng | Thiếu R1 |
| 9 | QC1-02 | A10 | lane | Nặng | Thiếu R1 |
| 10 | QC1-03 | B06 | lane#0 | Nặng | Camera hai bên: position cần là other |
| 11 | QC1-03 | B07 | lane#2 | Nặng | Camera hai bên: position cần là other |
| 12 | QC1-03 | B08 | lane#0 | Nặng | Camera hai bên: position cần là other |
| 13 | QC1-10 | A10 | traffic_sign#3 | Cảnh báo nhẹ | Box thấp hơn 8 px, không bắt buộc |
| 14 | QC1-10 | A10 | traffic_sign#8 | Cảnh báo nhẹ | Box thấp hơn 8 px, không bắt buộc |
| 15 | QC1-10 | A10 | traffic_sign#10 | Cảnh báo nhẹ | Box thấp hơn 8 px, không bắt buộc |
| 16 | QC1-10 | B03 | traffic_sign#16 | Cảnh báo nhẹ | Box thấp hơn 8 px, không bắt buộc |
| 17 | QC1-11 | B02 | road_curb#1 | Chính | Polyline chỉ có 3 điểm, cần đặt điểm theo cung |
| 18 | QC1-11 | B03 | road_curb#4 | Chính | Polyline chỉ có 3 điểm, cần đặt điểm theo cung |
| 19 | QC1-12 | A09 | drivable#3 | Nhẹ | Có 2 điểm lặp liền nhau |
| 20 | QC1-12 | A13 | image | Nhẹ | Ảnh chưa có nhãn |
| 21 | QC1-12 | A14 | image | Nhẹ | Ảnh chưa có nhãn |
| 22 | QC1-12 | A15 | image | Nhẹ | Ảnh chưa có nhãn |
| 23 | QC1-12 | A16 | image | Nhẹ | Ảnh chưa có nhãn |
| 24 | QC1-12 | B10 | image | Nhẹ | Ảnh chưa có nhãn |
| 25 | QC1-12 | B11 | image | Nhẹ | Ảnh chưa có nhãn |
| 26 | QC1-12 | B12 | image | Nhẹ | Ảnh chưa có nhãn |

## Ca mơ hồ

| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
|---|---|---|
| B02, B03, B04 | Các shape được gợi ý edge_zone có thực sự nằm ngoài 80% bán kính fisheye và cần bật thuộc tính này không? | Chưa hỏi |
| A13–A16, B10–B12 | Các ảnh chưa có nhãn có phải ảnh extra không cần gán hay bị bỏ sót? | Chưa xác minh |

## Quyết định

- **Lỗi nặng:** 12 phát hiện lint (1 QC1-01 + 8 QC1-02 + 3 QC1-03).
- **Lỗi chính:** 2 cảnh báo polyline fisheye cần kiểm tra; 7 gợi ý edge_zone chưa xác nhận.
- **Tỷ lệ lỗi chính:** Chưa tính được vì chưa xác định số nhãn đã kiểm thủ công và chưa xác nhận các lỗi chính.
- **Lỗi nhẹ:** 8 cảnh báo QC1-12.
- **Ca chờ lead:** 2 nhóm vấn đề (edge_zone và ảnh chưa có nhãn).

**Quyết định: Rework (theo kết quả lint hiện tại).**

**Lý do:** Có các phát hiện mức nặng gồm thiếu tag camera, thiếu L1/R1 và sai thuộc tính position trên một số lane. Các lỗi này cần được xem xét và xử lý trước khi Release. Các cảnh báo khác cần kiểm tra trực quan; box thấp hơn 8 px và gợi ý edge_zone chưa được tự động xem là lỗi xác nhận.

**Ghi chú:** Phiếu này là bản tự QC dựa trên kết quả lint và XML export, không phải kết quả kiểm thủ công đầy đủ. Các mục không có cảnh báo lint chưa được xác nhận là hoàn toàn đúng.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
