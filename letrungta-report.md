# Báo cáo cá nhân — Ngày 11

**Họ tên:** Lê Trung Tá  
**Mã học viên:** 2A2026003213  
**Phiên bản CVAT (Help → About):** 2.74.1  
**Guideline:** Road v1.0  
**Lần nộp (`revision` trong manifest):** 1  
**Thời điểm export (ngày giờ trên CVAT):** 11:15:54 ngày 21/11/2026  
**Số lần nộp lại sau Rework:** 0 (đây là lần đầu; đã nhận kết luận Rework nhưng chưa ghi nhận lần export/nộp lại)

> **Phạm vi số liệu:** Bảng số lượng và kiểm tra XML trong báo cáo này lấy từ hai file `letrungta-front.zip` và `letrungta-fisheye.zip` của revision 1. Kết quả review QC1 do Nguyễn Thái Dương lập ngày 21/11/2026. Báo cáo này phản ánh trạng thái revision 1 trước khi sửa Rework; sau khi sửa và export lại, cần cập nhật số liệu, manifest, revision và số lần nộp lại.

## 1. Kiểm project

| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Có | `lane` (polyline), `road_curb` (polyline), `crosswalk` (polygon), `drivable` (polygon), `traffic_light` (rectangle), `traffic_sign` (rectangle). |
| Thuộc tính và giá trị | Có | `lane`: `position/style/color/kind`; `drivable`: `area_type`; `traffic_light`: `color/type/facing/edge_zone`; `traffic_sign`: `group/facing/edge_zone`. |
| 4 tag ảnh | Có định nghĩa | `camera`, `timeofday`, `weather`, `source`. Tuy nhiên, revision 1 có lỗi ở tag theo từng ảnh: A10 và B12 thiếu cả 4 tag; B01, B02 và B09 sai giá trị `camera`; A07 có `weather=fog` trong khi reviewer đánh giá là `rain`. |

**Cách kết thúc polyline trên CVAT 2.74.1:** Click lần lượt các điểm trên tâm vạch, bắt đầu từ phía gần xe (đáy ảnh) đi ra xa; nhấn phím `N` để kết thúc polyline.

**Cách đặt tag ảnh trên CVAT 2.74.1:** Dùng công cụ Tag; đặt `camera` trước, sau đó `timeofday`, `weather`, `source`. Mở Details của từng tag trong Objects để kiểm tra và sửa giá trị; không giữ giá trị mặc định nếu không đúng ảnh.

## 2. Số lượng đã gán

Số lượng dưới đây là số shape đếm được trong `annotations.xml` của revision 1.

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 27 | 0 | 4 | 12 | 20 | 8 |
| front-extra (đã làm 4 / 4) | 4 | 10 | 0 | 2 | 4 | 8 | 10 |
| fisheye | 8 | 6 | 0 | 7 | 8 | 3 | 1 |
| fisheye-extra (đã làm 4 / 4) | 4 | 0 | 0 | 2 | 3 | 0 | 0 |
| **Tổng** | **28** | **43** | **0** | **15** | **27** | **31** | **19** |

**Lưu ý:** “Đã làm 4/4” ở hai task Extra nghĩa là đã có đủ 4 ảnh trong file export, không có nghĩa cả 4 ảnh đã đạt tiêu chí điểm thưởng. Trong revision 1, B11 chỉ có drivable; B12 chưa có shape và chưa có tag. Phần Extra cần được sửa/đối chiếu theo manifest và ảnh gốc trước khi coach chấm điểm cộng.

## 3. Bảng ca khó

| Ảnh | Nhãn | Phân vân giữa | Đã chọn / trạng thái revision 1 | Lý do |
| --- | --- | --- | --- | --- |
| A03 | lane | Có cần thêm R1 hay không khi vạch không thấy rõ/bị che | XML có L1 nhưng không có R1; QC1 mẫu không kết luận lỗi này, cần lead xác nhận nếu vạch thực sự không nhìn thấy | Không tự vẽ thêm vạch không nhìn thấy. QC1-02 là lỗi nặng nếu vạch thấy được; ngoại lệ phải được coach xác nhận và ghi mã ảnh. |
| A04 | lane | Vạch vàng đơn hay đôi | `color=yellow`, `kind=double`, `position=L1` | Checkpoint của lab nêu A04 có vạch vàng đôi; `kind=double` biểu diễn vạch đôi. Reviewer còn phát hiện thiếu R2 trắng liền cạnh làn xe đạp. |
| A01 | lane / drivable | Vạch liền hay đứt; direct có bao một hay nhiều làn | Revision 1 có L1/R1 `style=solid`, L2 `kind=double`; polygon direct phủ từ L2 tới R2 | Reviewer xác định L1/R1 thực tế là vạch trắng đứt; L2 là một nét đơn; direct cần giới hạn giữa L1–R1 và hai làn bên là alternative. |
| A07 | tag weather / lane | `fog` hay `rain`; vạch sát dải bê tông có nhìn thấy không | Revision 1 có `weather=fog`; reviewer đề nghị `rain`. QC1-02 ghi chờ lead về L1 | Reviewer thấy mặt đường ướt và giọt nước trên kính; câu hỏi về L1 vẫn cần lead xác nhận. |
| B02 | camera / traffic_light | `fisheye_front` hay `fisheye_rear`; đèn xe hay đèn người đi bộ | Revision 1 có `camera=fisheye_rear`; hai đèn sát mép có `edge_zone=false` | Tên file có hậu tố FV nên camera đúng là `fisheye_front`. Hai box đèn cần lead xác nhận loại đèn/facing; reviewer đánh dấu edge_zone sai. |
| B06–B08 | lane | L1/R1/R2 hay `other` | Revision 1 còn position L1/R1/R2 ở ảnh camera trái/phải | Guideline yêu cầu lane ở `fisheye_left` và `fisheye_right` dùng `position=other`. Reviewer xác nhận lỗi nặng ở B06; lint ngoài mẫu cũng ghi chú B07/B08. |
| B09 | camera / lane / đèn-biển | `fisheye_front` hay `fisheye_rear`; có đủ đối tượng trọng tâm không | Revision 1 có `camera=fisheye_rear`; chưa có lane/traffic_light/traffic_sign trong XML | Tên file FV yêu cầu `fisheye_front`; manifest fisheye mô tả B09 trọng tâm là đèn/biển sát mép và lane. |
| B11 | lane | Vạch dọc hay vạch ô đỗ | Revision 1 chỉ có drivable, chưa có lane | Manifest fisheye yêu cầu lane vạch dọc và bỏ qua vạch ô đỗ; cần đối chiếu ảnh gốc để gán đúng. |
| B12 | drivable / crosswalk / tags | Đã đủ nhãn và tag chưa | Revision 1 chưa có shape và chưa có tag | Manifest fisheye yêu cầu drivable + crosswalk; mọi ảnh cần đủ bốn tag. |

## 4. Phiếu QC 1 nhận được

**Bạn kiểm lô của tôi:** Nguyễn Thái Dương  
**Ngày review:** 21/11/2026  
**Ảnh được kiểm:** A01, A04, A07, B02, B05, B06 (6 ảnh; 0 ảnh Extra)  
**Số nhãn đã kiểm:** 45 (shape + tag)  
**Quyết định nhận được:** **Rework**

| Mã lỗi | Số lỗi theo phiếu QC1 | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| QC1-01 – tag camera | 1 nặng + 1 nhẹ | Đã ghi nhận; đối chiếu tag A07/B02 trước khi sửa | Chưa xác nhận |
| QC1-02 – đủ L1/R1 | 0 trong mẫu; A07 chờ lead | Chờ lead xác nhận trường hợp A07 | Chưa xác nhận |
| QC1-03 – position | 1 nặng | Đã ghi nhận; B06 camera trái phải là `other` | Chưa xác nhận |
| QC1-04 – tâm vạch, chiều, điểm dừng | 1 chính | Đã ghi nhận; A04 thiếu R2 | Chưa xác nhận |
| QC1-05 – vạch đứt, che | 0 | Không có lỗi được ghi nhận trong mẫu | Không áp dụng |
| QC1-06 – style, color, kind | 4 chính | Đã ghi nhận; A01 L1/R1 và A04 R1 cần `dashed`; A01 L2 cần `single` | Chưa xác nhận |
| QC1-07 – vùng lái | 4 chính | Đã ghi nhận; A01/A04 cần sửa direct/alternative; B05 thiếu hai road_curb | Chưa xác nhận |
| QC1-08 – đèn, màu | 0 | Không có lỗi được ghi nhận trong mẫu | Không áp dụng |
| QC1-09 – facing, type, group, biển phụ | 1 chính | Đã ghi nhận; biển xanh A01 cần `group=information`, `facing=front` | Chưa xác nhận |
| QC1-10 – hình in, đủ biển | 1 chính | Đã ghi nhận; A01 thiếu biển xanh nhỏ ở xa, cao khoảng 25 px | Chưa xác nhận |
| QC1-11 – fisheye | 3 chính | Đã ghi nhận; B02 cần edge_zone, B06 polyline cần tách/đi theo cung | Chưa xác nhận |
| QC1-12 – file | 1 nhẹ | Đã ghi nhận; A01 lane L2 có điểm cuối lặp | Chưa xác nhận |

**Tổng hợp theo phiếu người review:** 2 lỗi nặng, 14 lỗi chính, 2 lỗi nhẹ; lỗi chính là `14/45 = 31,1%`; có 2 ca mơ hồ chờ lead (A07 và B02). Theo luật Road v1.0, có lỗi nặng là đủ để Rework; tỷ lệ lỗi chính 31,1% cũng vượt ngưỡng 5%.

**Các lỗi chi tiết người review ghi nhận:**

| # | Mã | Ảnh | Nhãn/đối tượng | Mức | Nội dung |
| ---: | --- | --- | --- | --- | --- |
| 1 | QC1-06 | A01 | lane L1 | Chính | `style=solid`; thực tế vạch trắng đứt, cần `dashed`. |
| 2 | QC1-06 | A01 | lane R1 | Chính | `style=solid`; thực tế vạch trắng đứt, cần `dashed`. |
| 3 | QC1-06 | A01 | lane L2 | Chính | `kind=double`; thực tế vạch trắng một nét, cần `single`. |
| 4 | QC1-07 | A01 | drivable (direct) | Chính | Một polygon direct phủ cả ba làn L2–R2; cần direct giữa L1–R1, hai làn bên là alternative. |
| 5 | QC1-09 | A01 | traffic_sign xanh | Chính | `group=prohibitory` cần đổi thành `information`; `facing=side` cần đổi thành `front`. |
| 6 | QC1-10 | A01 | traffic_sign bị bỏ sót | Chính | Thiếu biển xanh nhỏ ở xa, reviewer đo khoảng x=432–450, y=463–488, cao khoảng 25 px (lớn hơn ngưỡng 8 px). |
| 7 | QC1-12 | A01 | lane L2 | Nhẹ | Điểm cuối (365.5, 499.2) bị lặp hai lần. |
| 8 | QC1-06 | A04 | lane R1 | Chính | `style=solid`; thực tế vạch trắng đứt, cần `dashed`. |
| 9 | QC1-04 | A04 | lane R2 | Chính | Thiếu vạch trắng liền cạnh làn xe đạp (R2). |
| 10 | QC1-07 | A04 | drivable (direct) | Chính | Polygon direct kéo tới mép phải, gộp cả làn phải và làn xe đạp; thiếu alternative giữa R1–R2. |
| 11 | QC1-01 | A07 | tag weather | Nhẹ | `weather=fog`; reviewer nhận định ảnh có đường ướt và giọt nước trên kính, cần `rain`. |
| 12 | QC1-01 | B02 | tag camera | Nặng | `camera=fisheye_rear`; tên file FV yêu cầu `fisheye_front`. |
| 13 | QC1-11 | B02 | traffic_light bên phải (x≈1077–1140) | Chính | Đèn sát mép; tâm box ngoài 80% bán kính nhưng `edge_zone=false`. |
| 14 | QC1-11 | B02 | traffic_light bên trái (x≈110–156) | Chính | Đèn sát mép; tâm box ngoài 80% bán kính nhưng `edge_zone=false`. |
| 15 | QC1-07 | B05 | road_curb | Chính | Thiếu road_curb mép vỉa hè phía xa (x≈430,y≈100 đến x≈890,y≈170). |
| 16 | QC1-07 | B05 | road_curb | Chính | Thiếu road_curb mép đảo giữa bên phải (x≈900,y≈180 đến x≈1110,y≈400). |
| 17 | QC1-03 | B06 | lane (x≈170,y≈258) | Nặng | Camera trái MVL nhưng `position=L1`; cần `other`. |
| 18 | QC1-11 | B06 | lane | Chính | Một polyline nối thẳng (277,253) đến (927,492), gộp hai vạch khác nhau và không đi theo cung. |

**Hai ca mơ hồ chờ lead:**

| Ảnh | Câu hỏi | Trạng thái |
| --- | --- | --- |
| A07 | Vạch sát dải bê tông bên trái có đủ rõ để bắt buộc có L1 không? | Chưa có lời đáp trong phiếu QC1 nhận được. |
| B02 | Hai cụm đèn sát mép là đèn xe (`vehicle`) hay đèn người đi bộ (`pedestrian`), và có quay về xe (`facing=front`) không? | Chưa có lời đáp trong phiếu QC1 nhận được. |

**Ghi chú ngoài mẫu do reviewer báo thêm từ lint:** B01 và B09 cũng sai camera (`fisheye_rear` thay vì `fisheye_front`); A10 thiếu cả 4 tag; B07 và B08 lane camera hai bên chưa là `other`; B12 chưa có nhãn nào. Đây là ghi chú ngoài 6 ảnh được review, không cộng vào số lỗi trong mẫu 45 nhãn ở trên.

**Trạng thái Rework:** Tại thời điểm lập báo cáo này, chưa có xác nhận rằng các lỗi trên đã được sửa và chưa có revision 2. Sau khi sửa trên CVAT, cần export lại, chạy lint, tạo manifest `revision=2`, lưu bản cũ trong `r1/` và cập nhật bảng “Đã sửa?” cùng số lần nộp lại.

## 5. Kiểm file export

Kiểm tra trực tiếp XML của hai ZIP revision 1: mỗi ZIP mở được và chứa `annotations.xml`; không kèm ảnh gốc. Số shape trong hai ảnh đầu của từng nhóm:

| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | ---: | ---: | --- |
| `letrungta-front.zip` | Có | A01: 6 / 6 | A02: 4 / 4 | Có; A01/A02 đều có `camera=front`. |
| `letrungta-fisheye.zip` | Có | B01: 2 / 2 | B02: 4 / 4 | Có nhưng giá trị sai ở cả hai: hậu tố FV yêu cầu `fisheye_front`, XML hiện là `fisheye_rear`. |

**Lưu ý:** “Tag camera có trong XML” không đồng nghĩa giá trị đúng. Ngoài B01/B02, B09 cũng có giá trị camera sai; A10 và B12 thiếu tag camera cùng các tag còn lại. A07 có tag weather nhưng reviewer yêu cầu đổi `fog` thành `rain`.

## 6. Ảnh chụp màn hình

Cần chèn ảnh chụp thật từ CVAT/VS Code vào bốn vị trí dưới đây trước khi nộp:

1. **Tab Labels của project:** `[CHÈN ẢNH CHỤP TAB LABELS — thấy 6 label hình và 4 tag]`
2. **Ảnh camera trước đã gán:** `[CHÈN ẢNH CVAT — thấy lane, drivable và đèn/biển nếu có trong ảnh]`
3. **Ảnh fisheye đã gán:** `[CHÈN ẢNH CVAT — phóng to đoạn polyline cong]`
4. **Đoạn XML:** `[CHÈN ẢNH VS CODE/EDITOR — nhìn thấy một dòng <polyline label="lane"> cùng points và attribute]`

## 7. Tự đánh giá

Trong phiếu QC1 nhận được, hai nhóm có số lỗi chính nhiều nhất là **QC1-06 (style/color/kind) và QC1-07 (vùng lái), mỗi nhóm có 4 lỗi**. Điều này cho thấy em cần kiểm tra thuộc tính từng lane sau khi vẽ và kiểm tra ranh giới giữa `direct` với `alternative`, không chỉ nhìn xem đã có polyline/polygon hay chưa.

Để tránh lặp lại ở Ngày 20, em sẽ dùng checklist sau cho từng ảnh: (1) rà từng lane và đối chiếu `position/style/color/kind` với vạch thật; (2) kiểm tra polygon direct chỉ bao làn xe của mình, các làn bên cạnh dùng alternative khi phù hợp; (3) kiểm tra bốn tag ảnh trước khi chuyển ảnh; (4) xem lại các đối tượng ở vùng mép ảnh để kiểm tra `edge_zone`; (5) chạy lint sau mỗi nhóm ảnh thay vì đợi đến khi export toàn bộ.

**Lỗi ảnh hưởng tới model:** Ví dụ QC1-06 ở A01, lane L1/R1 được gán `style=solid` trong khi vạch thật là `dashed`. Nếu nhãn sai đi vào dữ liệu huấn luyện, mô hình học phân loại thuộc tính vạch không đúng, làm giảm khả năng phân biệt vạch liền và vạch đứt trong cảnh mới. Ví dụ QC1-07 ở A01/A04, polygon `direct` phủ cả làn bên cạnh/làn xe đạp; mô hình học vùng xe có thể đi rộng hơn thực tế, gây sai nhận diện làn xe của mình và ảnh hưởng các bước downstream như ước lượng làn/giữ làn.

**Tình trạng sửa lỗi:** Phiếu QC1 kết luận Rework; tại thời điểm báo cáo chưa có revision 2 được xác nhận. Vì vậy không ghi các lỗi là “đã sửa” cho đến khi sửa trên CVAT và export lại thành công.

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor

Dùng `letrungta-front.zip`, ảnh A01, lane có `position=R1`. Lệnh tương ứng trong repo là:

```powershell
$env:PYTHONPATH = (Resolve-Path .\src).Path
python -m road_lab.rowanchor letrungta-front.zip --image A01 --position R1
```

Kết quả nội suy từ polyline R1 của A01 trong revision 1:

| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi | không có làn | 656.0 | 599.5 | 543.1 | 486.6 |
| x của bạn kia | Chưa có dữ liệu cùng ảnh A01/R1 | Chưa có dữ liệu | Chưa có dữ liệu | Chưa có dữ liệu | Chưa có dữ liệu |

**1. Nếu dừng polyline sớm 40 px, hàng nào đổi thành “không có làn”?**

Polyline R1 hiện đi từ gần xe `(710.30, 718.50)` đến đầu xa `(418.90, 512.00)`. Nếu “dừng sớm 40 px” ở **đầu xa** (đầu kết thúc theo quy tắc gần → xa), đầu xa chuyển từ y=512 lên khoảng y=552. Khi đó hàng y=560 vẫn còn nằm trong đoạn polyline nên vẫn có giá trị; hàng y=520 nằm ngoài đoạn và thành “không có làn”. Trong năm hàng của bảng (720, 680, 640, 600, 560), không có hàng nào mới mất giá trị; y=720 vốn đã nằm ngoài polyline. Nếu ý bài là cắt ngắn **đầu gần** 40 px, đầu gần chuyển từ y=718.5 lên khoảng y=678.5 và hàng y=680 sẽ thành “không có làn”. Cần ghi rõ đầu nào được giả định khi trả lời.

**2. So với bạn được kiểm ở hàng 720 và 560, hai bạn lệch bao nhiêu pixel? Hàng nào ảnh hưởng LKA nhiều hơn?**

Chưa thể tính độ lệch vì file annotation/ZIP của Nguyễn Thái Dương cho **cùng ảnh A01 và cùng lane position=R1** chưa được cung cấp. Phiếu QC1 Nguyễn Thái Dương gửi là đánh giá nhãn của em, không chứa tọa độ row-anchor của bạn ấy. Khi có file của bạn ấy, tính:
- tại y=720: `|x_của_em − x_của_bạn|` (nếu một bên là “không có làn” thì không tính chênh lệch số);
- tại y=560: `|486.6 − x_của_bạn_tại_y560|`.

Về ý nghĩa điều khiển, hàng gần xe thường ảnh hưởng trực tiếp hơn tới ước lượng biên làn tức thời; cần đối chiếu Slide 25 của lớp để dùng đúng diễn giải mà giảng viên yêu cầu. Slide 25 chưa có trong các file hiện được cung cấp nên báo cáo không gán một trích dẫn cụ thể cho slide.

**3. Nếu polyline vẽ từ xa về gần, cách tính có đổi không? Script nào sẽ gặp khó?**

Phép nội suy `x_at_y` không đổi về mặt toán học vì hàm kiểm tra khoảng `min(y1,y2)` đến `max(y1,y2)` của từng đoạn; đảo thứ tự điểm không làm thay đổi x tại cùng một hàng y. Tuy nhiên, quy tắc Road v1.0 vẫn yêu cầu vẽ từ gần xe ra xa. `road_lab.rowanchor` có thể tính nhưng sẽ in cảnh báo nếu phát hiện điểm đầu ở xa hơn điểm cuối; `road_check lint/check` sẽ ghi lỗi QC1-04 “vẽ ngược chiều (phải từ gần xe ra xa)”.

---

## Việc còn phải hoàn thành trước khi nộp bản cuối

- [ ] Sửa các lỗi QC1 theo phiếu Nguyễn Thái Dương: A01, A04, A07, B02, B05, B06.
- [ ] Sửa các ghi chú ngoài mẫu: B01, B09, A10, B07, B08, B12.
- [ ] Xin lead trả lời hai ca mơ hồ A07 và B02; ghi lời đáp vào Phiếu QC1.
- [ ] Export lại đúng hai ZIP, giữ nguyên tên `letrungta-front.zip` và `letrungta-fisheye.zip`.
- [ ] Cất bản cũ và manifest revision 1 vào thư mục `r1/` trước khi tạo manifest mới.
- [ ] Chạy lint, tạo manifest revision 2, kiểm tra `contains_images=false`.
- [ ] Cập nhật số lượng shape và mục 4/5/7 theo ZIP revision 2.
- [ ] Chèn đủ bốn ảnh minh chứng ở mục 6.
- [ ] Nếu làm phần row-anchor so sánh, lấy ZIP/annotations của bạn được kiểm cho cùng ảnh A01/R1 và điền các giá trị x còn thiếu.
