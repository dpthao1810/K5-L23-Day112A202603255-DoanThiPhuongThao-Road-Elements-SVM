# Báo cáo cá nhân — Ngày 11

Họ tên: Doãn Thị Phương Thảo  
Mã học viên: 2A202603255  
Phiên bản CVAT (Help → About): 
Guideline: Road v1.0  
Lần nộp (`revision` trong manifest): 1  
Thời điểm export (ngày giờ trên CVAT): 11h40  
Số lần nộp lại sau Rework: 0

## 1. Kiểm project

| Mục | Đúng như guideline Road v1.0? | Ghi chú |
|---|---|---|
| 6 label, đúng kiểu | Có | Đã tạo đủ label theo guideline |
| Thuộc tính và giá trị | Có | Đã thiết lập attribute cho các label |
| 4 tag ảnh | Có | Đã thiết lập bộ tag cho ảnh |

**Cách kết thúc polyline trên bản CVAT này:** Click đúp chuột vào điểm cuối để kết thúc polyline.

**Cách đặt tag ảnh trên bản CVAT này:** Chọn ảnh trong task, đặt các thuộc tính tag ở cấp ảnh (image-level), không gán vào từng shape.

## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
|---|---:|---:|---:|---:|---:|---:|---:|
| front | 12 | 26 | 17 | 10 | 30 | 35 | 36 |
| front-extra (đã làm 0/4) | 4 | 0 | 0 | 0 | 0 | 0 | 0 |
| fisheye | 8 | 6 | 12 | 13 | 12 | 6 | 11 |
| fisheye-extra (đã làm 1/4) | 4 | 0 | 2 | 4 | 2 | 0 | 0 |

## 3. Bảng ca khó

| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
|---|---|---|---|---|
| | lane | L1 / L2 | | Vị trí vạch so với làn xe |
| | drivable | direct / alternative | | Xác định vùng xe có thể di chuyển |
| | traffic_sign | group | | Phân loại theo chức năng biển |
| | road_curb | curb / ranh giới vùng khác | | Quan sát ranh giới đường thực tế |

## 4. Phiếu QC 1 nhận được

**Bạn kiểm lô của tôi:** Road Elements — Front + Fisheye

**Quyết định nhận được:** Chưa sửa sau lần lint; còn các cảnh báo QC cần xem xét.

| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
|---|---:|---|---|
| QC1-01 | 4 | Có | Không |
| QC1-02 | 8 | Cần xem lại | Không |
| QC1-03 | 3 | Cần xem lại | Không |
| QC1-10 | 4 | Có thể chấp nhận | Không |
| QC1-11 | 9 gợi ý | Cần xem lại | Không |
| QC1-12 | 8 | Cần xem lại | Không |

> QC1-11 gồm 2 cảnh báo polyline road_curb chỉ có 3 điểm và 7 gợi ý edge_zone. Đây là số tổng hợp các gợi ý checker, không đồng nghĩa tất cả đều là lỗi đã xác nhận.

## 5. Kiểm file export

| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
|---|---|---|---|---|
| Front ZIP | Có | A01 | A02 | Chưa kiểm tra |
| Fisheye ZIP | Có | B01 | B02 | Chưa kiểm tra |

## 6. Ảnh chụp màn hình

- [ ] Tab Labels của project.
- [ ] Một ảnh camera trước đã gán đủ (làn, vùng lái, đèn/biển).
- [ ] Một ảnh fisheye đã gán, phóng to đoạn polyline cong.
- [ ] Một đoạn XML có `<polyline label="lane">`.

## 7. Tự đánh giá

**Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20:**

Các lỗi tôi cần chú ý nhiều nhất là QC1-02 và QC1-12, liên quan đến thiếu lane ở một số ảnh và các vấn đề về shape như ảnh chưa được gán nhãn hoặc điểm polyline bị lặp. Ngoài ra, tôi cần chú ý hơn đến tag ảnh và thuộc tính của lane trên các camera fisheye.

Ở Ngày 20, tôi sẽ kiểm tra lại từng ảnh sau khi gán nhãn, đối chiếu các thuộc tính với guideline, kiểm tra điểm đầu và điểm cuối của polyline, đồng thời chạy QC trước khi export để hạn chế các lỗi bị bỏ sót.

**Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào:**

Các nhãn annotation được sử dụng làm dữ liệu ground truth để model học trong quá trình training. Model dự đoán dựa trên ảnh đầu vào và được so sánh với nhãn ground truth để điều chỉnh sai số.

Ví dụ, nếu polyline của lane bị đặt sai vị trí hoặc bị thiếu đoạn, model có thể học sai vị trí đường lane, dẫn đến dự đoán sai ranh giới làn đường. Điều này có thể ảnh hưởng đến các ứng dụng như Lane Keeping Assist (LKA), khiến việc xác định vị trí xe và hướng di chuyển không chính xác.

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor

| y | 720 | 680 | 640 | 600 | 560 |
|---|---:|---:|---:|---:|---:|
| x của chúng tôi | | | | | |
| x của bạn kia | | | | | |

### Trả lời 3 câu

**1. Năm số x đó chính là đích mà một model row-anchor học cho vạch này. Nếu bạn dừng polyline sớm 40 px, hàng nào đổi thành "không có làn"?**

Các hàng anchor nằm trong đoạn 40 px bị thiếu ở cuối polyline có thể không còn lấy được tọa độ lane. Khi chuyển polyline sang row-anchor, những hàng không còn giao với đường lane sẽ bị mất giá trị x hoặc được đánh dấu là không có lane. Cụ thể hàng nào bị ảnh hưởng phải dựa vào vị trí điểm kết thúc và các mốc y thực tế.

**2. So với bạn được kiểm (cùng ảnh): ở hàng 720 và hàng 560, hai bạn lệch nhau bao nhiêu pixel? Lệch ở hàng nào ảnh hưởng LKA nhiều hơn (slide 25)?**

Công thức tính độ lệch:

- Hàng 720: `Δx_720 = |x_chúng_tôi - x_bạn_kiểm|`.
- Hàng 560: `Δx_560 = |x_chúng_tôi - x_bạn_kiểm|`.

Chưa thể tính số pixel khi chưa có tọa độ hai bên. Về ảnh hưởng LKA, vị trí lane gần xe thường có ý nghĩa trực tiếp đối với việc xác định ranh giới và hướng điều khiển, nhưng cần đối chiếu đúng slide 25 của lab để trả lời theo tiêu chí giảng viên.

**3. Nếu polyline vẽ từ xa về gần (ngược quy tắc 2), cách tính trên có đổi không? Script nào sẽ gặp khó?**

Phép tính giao giữa polyline và các hàng y không thay đổi về mặt hình học. Tuy nhiên, thứ tự các điểm có thể ảnh hưởng đến script nếu script giả định polyline luôn được vẽ theo một chiều nhất định để xử lý điểm tuần tự. Khi đảo chiều, những script phụ thuộc vào thứ tự điểm có thể đọc sai đoạn, xử lý không đúng thứ tự hoặc gặp khó khi chuyển polyline thành row-anchor.
