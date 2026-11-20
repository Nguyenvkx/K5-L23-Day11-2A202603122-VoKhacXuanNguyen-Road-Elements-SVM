# Báo cáo cá nhân — Ngày 11 · Road Elements & SVM

Họ tên: Võ Khắc Xuân Nguyên  
Mã học viên: 2A202503122
Ngày lập báo cáo: 20/11/2026  
Phiên bản CVAT (Help → About):  2.81.0  
Guideline: Road v1.0  
Lần tạo manifest bàn giao: revision 2, khớp hai ZIP hiện tại.  
Thời điểm export trên CVAT:   21:43 20/11/2026
Số lần nộp lại sau Rework chính thức: 1


## 1. Kiểm project

| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | XML có đủ 6 label; cần đối chiếu ảnh chụp Labels | lane, road_curb, crosswalk, drivable, traffic_light, traffic_sign |
| Thuộc tính và giá trị | Lint hiện không báo tên label/giá trị không hợp lệ | Độ đúng theo nội dung ảnh cần kiểm trực quan |
| 4 tag ảnh | Đủ trên 20/20 ảnh trong bản export hiện tại | camera, timeofday, weather, source; 80 tag tổng cộng |
| File bàn giao | Hai ZIP đọc được, không kèm ảnh | Chi tiết ở mục 5; manifest revision 2 |

Cách kết thúc polyline trên bản CVAT này: hướng dẫn kèm repo dùng phím N.
Cách đặt tag ảnh: chọn Tag, chọn label, thêm tag và sửa thuộc tính value trong Details. Trạng thái mọi job completed.

## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 34 | 9 | 4 | 18 | 23 | 22 |
| front-extra (0/4 ảnh có trong file nộp) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| fisheye | 8 | 6 | 6 | 8 | 4 | 4 | 6 |
| fisheye-extra (0/4 ảnh có trong file nộp) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Tổng | 20 | 40 | 15 | 12 | 22 | 27 | 28 |

Tổng: 144 shape và 80 tag. Đây là số nhãn trong file, không phải mẫu số của phiếu kiểm chéo cho bạn khác.

## 3. Bảng ca khó

Học viên thông báo các cảnh báo nặng được bỏ qua và các cảnh báo chính đã được xác nhận chấp nhận. Chưa cung cấp tên người xác nhận, lý do riêng cho từng ca hoặc bằng chứng đối chiếu ảnh; cần bổ sung vào các ô dưới đây.

| Ảnh | Nhãn | Phân vân giữa | Đã chọn trong bản hiện tại | Lý do / xác nhận cần ghi |
| --- | --- | --- | --- | --- |
| A05 | lane L1, R1 | Bỏ sót vạch hay thực tế không thấy vạch | Không có L1/R1 | Đã được xác nhận miễn |
| A06 | lane R1 | Bỏ sót hay không thấy vạch | Không có R1 | Đã được xác nhận miễn |
| A09 | lane R1 | Bỏ sót hay không thấy vạch | Không có R1 | Đã được xác nhận miễn |
| A04 | lane | Tách vạch đứt / nhầm position hay trường hợp hợp lệ | Hai polyline R2 và hai polyline L1 | Đã được xác nhận miễn |
| A09 | lane | Hai polyline cùng L2 có hợp lệ không | Giữ hai polyline L2 | Được chấp nhận |
| A11 | lane | Hai polyline cùng L1 có hợp lệ không | Giữ hai polyline L1 | Được chấp nhận |
| B03 | lane | Hai polyline cùng R1 có hợp lệ khôn | Giữ hai polyline R1 | Được chấp nhận |
| B03 | traffic_sign, vị trí khoảng (173,300) | edge_zone bật hay tắt | Giữ bản hiện tại | Đã được xác nhận miễn |
| A03 | traffic_light, vị trí khoảng (593,331) | Đèn nhỏ hơn 8 px có bắt buộc không | Giữ box trong file | Theo guideline, đối tượng thấp hơn 8 px không bắt buộc; cảnh báo không yêu cầu xóa |

## 4. Phiếu QC 1 nhận được

Bạn kiểm lô của tôi: [BỔ SUNG họ tên].  
Tên phiếu / ngày kiểm: [BỔ SUNG].  
Quyết định nhận được (Release / Hold / Rework): [BỔ SUNG theo phiếu thực tế; không suy ra từ lint].

Bảng dưới là lịch sử tự kiểm bằng lint, chưa phải bản sao phiếu QC của người kiểm.

| Mã lỗi | Số cảnh báo trước → hiện tại | Phản hồi | Đã sửa / tình trạng |
| --- | ---: | --- | --- |
| QC1-01 | 40 → 0 | Bản đầu thiếu timeofday và source trên 20 ảnh | Bản hiện tại đã đủ 4 tag/ảnh |
| QC1-02 | 5 → 4 | Còn A05 L1/R1, A06 R1, A09 R1 | A04 không còn cảnh báo thiếu R1; các ca còn lại được học viên thông báo miễn, cần ghi xác nhận ở mục 3 |
| QC1-03 | 2 → 0 | B07/B08 là camera bên, lane phải dùng other | Bản hiện tại không còn cảnh báo position cho camera bên |
| QC1-05 | 6 → 5 | Cảnh báo polyline trùng position | A10 không còn cảnh báo; các ca còn lại được học viên thông báo chấp nhận |
| QC1-11 | 3 → 1 | Cung fisheye và edge_zone | Không còn cảnh báo lane chỉ có 2 điểm; còn gợi ý edge_zone ở B03 được học viên thông báo chấp nhận |
| QC1-08 | 3 → 1 | Box đèn nhỏ hơn 8 px | Còn A03; không bắt buộc gán theo ngưỡng của lab |

Kết quả lint hiện tại: 11 cảnh báo, gồm 4 nặng, 6 chính, 1 nhẹ. Các cảnh báo vẫn được giữ trong manifest; không tự chuyển thành 0 sau khi được chấp nhận. Không tính tỉ lệ lỗi kiểm chéo từ các con số cảnh báo này.

## 5. Kiểm file export

| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| vokhacxuannguyen-front.zip | Có | 10 / 10 | 7 / 7 | 12/12 ảnh |
| vokhacxuannguyen-fisheye.zip | Có | 4 / 4 | 3 / 3 |  8/8 ảnh |

Đã đếm lại hai nội dung XML cung cấp và đối chiếu với XML trong ZIP: số shape khớp ở cả bốn ảnh. Shape không bao gồm tag; mỗi ảnh dưới đây còn có 4 tag riêng.

| Ảnh | Chi tiết shape trong XML | Tổng shape |
| --- | --- | ---: |
| A01 | 4 lane + 2 traffic_sign + 1 road_curb + 3 drivable | 10 |
| A02 | 3 lane + 1 road_curb + 3 drivable | 7 |
| B01 | 2 traffic_light + 1 crosswalk + 1 drivable | 4 |
| B02 | 2 traffic_light + 1 crosswalk | 3 |


## 6. Ảnh chụp màn hình

1. [BỔ SUNG ảnh chụp tab Labels của project].
2. [BỔ SUNG ảnh front đã gán đủ nhóm label được yêu cầu].
3. [BỔ SUNG ảnh fisheye, phóng to đoạn polyline cong].
4. [BỔ SUNG ảnh chụp XML chứa polyline label="lane"].

Đoạn XML thật dưới đây lấy từ A01 trong ZIP front, để hỗ trợ chụp minh chứng; không thay cho ảnh chụp bắt buộc:

```xml
<polyline label="lane" source="manual" occluded="0" points="1279.65,706.27;1187.94,683.58;1078.27,658.30;989.45,636.74;878.76,610.02;789.94,587.33;692.14,564.32;617.86,546.16;535.75,526.77;498.19,518.31;466.32,511.09" z_order="0">
  <attribute name="position">R2</attribute>
  <attribute name="style">solid</attribute>
  <attribute name="color">yellow</attribute>
  <attribute name="kind">single</attribute>
</polyline>
```

## 7. Tự đánh giá

Bản đầu có nhiều cảnh báo nhất ở QC1-01: thiếu timeofday và source trên toàn bộ 20 ảnh. Bản hiện tại đã bổ sung đủ. Để tránh lặp lại, tôi sẽ đặt và kiểm đủ bốn tag trước khi vẽ, sau đó chạy lint trước khi bàn giao.

Một lỗi đã sửa là position của lane ở camera hai bên B07/B08. Với ảnh fisheye_left/fisheye_right, guideline yêu cầu position = other. Nếu giữ nhãn L1/R1 sai, hệ thống học có sử dụng thuộc tính position có thể học nhầm vạch nhìn từ bên hông thành ranh giới làn đang đi.

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor

Chưa thực hiện; mục này không tính điểm theo rubric. Nếu làm thêm, điền kết quả tự tính và đối chiếu với bạn:

| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi | — | — | — | — | — |
| x của bạn kia | — | — | — | — | — |

1. Nếu dừng polyline sớm 40 px, hàng nào đổi thành “không có làn”? [BỔ SUNG nếu thực hiện].
2. Hai bạn lệch bao nhiêu pixel tại y=720 và y=560; hàng nào ảnh hưởng LKA nhiều hơn? [BỔ SUNG nếu thực hiện].
3. Nếu đảo thứ tự điểm polyline, nội suy có đổi không và script nào bị ảnh hưởng? [BỔ SUNG nếu thực hiện].
