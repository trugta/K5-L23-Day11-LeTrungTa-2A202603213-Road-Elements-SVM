# Báo cáo cá nhân — Ngày 11
Họ tên: Lê Trung Tá           Mã học viên: 2A2026003213 
Phiên bản CVAT (Help → About):  2.74.1
Guideline: Road v1.0    Lần nộp (`revision` trong manifest):  1
Thời điểm export (ngày giờ trên CVAT): 11:15:54 ngày 21/11/2026   Số lần nộp lại sau Rework: 0  

## 1. Kiểm project
| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | có | lane (polyline), road_curb (polyline), crosswalk (polygon), drivable (polygon), traffic_light (rectangle), traffic_sign (rectangle). |
| Thuộc tính và giá trị | và giá trị	Có — định nghĩa trong XML khớp Road v1.0 | lane: position/style/color/kind; drivable: area_type; traffic_light: color/type/facing/edge_zone; traffic_sign: group/facing/edge_zone. |
| 4 tag ảnh | có | camera, timeofday, weather, source; tuy nhiên dữ liệu tag từng ảnh hiện chưa hoàn chỉnh: A10 thiếu cả 4 tag, B12 thiếu cả 4 tag; B01, B02, B09 có camera tag nhưng giá trị camera chưa đúng.  |
Cách kết thúc polyline trên bản CVAT này:  Click lần lượt các điểm trên tâm vạch, bắt đầu từ phía gần xe (đáy ảnh) đi ra xa; nhấn phím N để kết thúc polyline.
Cách đặt tag ảnh trên bản CVAT này:  Dùng công cụ Tag; đặt camera trước, sau đó timeofday, weather, source. Mở Details của từng tag trong Objects để kiểm tra/sửa giá trị, không giữ mặc định nếu không đúng ảnh.

## 2. Số lượng đã gán
| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 27 | 0 | 4 | 12 | 20 | 8 |
| front-extra (đã làm 4 / 4) | 4 | 10 | 0 | 2 | 4 | 8 | 10 |
| fisheye | 8 | 6 | 0 | 7 | 8 | 3 | 1 |
| fisheye-extra (đã làm 4 / 4) | 4 | 0 | 0 | 2 | 3 | 0 | 0 |

## 3. Bảng ca khó
| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| A03 | lane | 	Có cần thêm R1 hay không khi vạch không thấy rõ/bị che | XML hiện có L1, chưa có R1; cần đối chiếu ảnh gốc và xin coach xác nhận nếu thực sự không thấy vạch | Không tự vẽ thêm vạch không nhìn thấy; ngoại lệ QC1-02 phải được coach xác nhận và ghi trong phiếu QC1. |
| A04 | lane | 	Vạch vàng đơn hay đôi | color=yellow, kind=double, position=L1 | Checkpoint của lab nêu A04 có vạch vàng đôi; kind=double dùng để biểu diễn vạch đôi. |
| B06–B08 | lane | 	L1/R1/R2 hay other | XML hiện còn L1/R1/R2; cần sửa thành position=other cho camera fisheye trái/phải | Guideline quy định lane ở fisheye_left và fisheye_right luôn dùng position=other. |
| B09 | camera / lane / đèn-biển | fisheye_front hay fisheye_rear; có đủ đối tượng trọng tâm không | XML hiện là fisheye_rear; cần sửa thành fisheye_front theo hậu tố FV. XML hiện chưa có lane/traffic_light/traffic_sign | Bảng kế hoạch fisheye ghi B09 là FV, trọng tâm gồm đèn/biển sát mép và lane. |
| B11 | lane | 	Vạch dọc hay vạch ô đỗ | XML hiện chưa có lane; chỉ có drivable. Cần đối chiếu ảnh gốc và bổ sung lane nếu nhìn thấy vạch dọc theo kế hoạch | Bảng kế hoạch B11 yêu cầu lane vạch dọc và bỏ qua vạch ô đỗ. |
| B12 | drivable / crosswalk và tags | Đã đủ nhãn và tag chưa | XML hiện chưa có shape và chưa có tag; cần hoàn thiện theo ảnh gốc | Bảng kế hoạch B12 yêu cầu drivable và crosswalk; mọi ảnh phải có đủ bốn tag. |

## 4. Phiếu QC 1 nhận được
Bạn kiểm lô của tôi:  Quyết định nhận được:  
| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |

## 5. Kiểm file export
| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |

## 6. Ảnh chụp màn hình
1. Tab Labels của project.
2. Một ảnh camera trước đã gán đủ (làn, vùng lái, đèn/biển).
3. Một ảnh fisheye đã gán, phóng to đoạn polyline cong.
4. Một đoạn XML có <polyline label="lane">.

## 7. Tự đánh giá
Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20:  
Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào:  

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor
| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi |  |  |  |  |  |
| x của bạn kia |  |  |  |  |  |

Trả lời 3 câu:

1. Năm số x đó chính là đích mà một model row-anchor học cho vạch này. Nếu bạn dừng polyline sớm 40 px, hàng nào đổi thành "không có làn"?
2. So với bạn được kiểm (cùng ảnh): ở hàng 720 và hàng 560, hai bạn lệch nhau bao nhiêu pixel? Lệch ở hàng nào ảnh hưởng LKA nhiều hơn (slide 25)?
3. Nếu polyline vẽ từ xa về gần (ngược quy tắc 2), cách tính trên có đổi không? Script nào sẽ gặp khó?
