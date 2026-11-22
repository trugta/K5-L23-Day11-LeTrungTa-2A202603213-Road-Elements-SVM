# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Lê Trung Tá (letrungta)        Người kiểm (học viên): Nguyễn Thái Dương  
Ngày: 2026-11-21                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): letrungta-front.zip, letrungta-fisheye.zip — revision: __ (chưa nhận manifest)  
Số ảnh kiểm: 6 (A01, A04, A07, B02, B05, B06) (+ 0 ảnh thêm)   Số nhãn đã kiểm (shape + tag): 45  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 1 (+1 tag khác, nhẹ) | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 6 | 0 (A07 chờ lead) | nặng |
| QC1-03 position | sai thuộc tính / thừa | 9 | 1 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 9 | 1 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 9 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 9 | 4 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 9 | 4 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 2 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 3 | 1 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 1 | 1 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 9 | 3 | chính |
| QC1-12 file | lỗi file | 2 | 1 | nhẹ |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-06 | A01 | lane L1 | chính | style = solid, thực tế là vạch trắng đứt → dashed |
| 2 | QC1-06 | A01 | lane R1 | chính | style = solid, thực tế là vạch trắng đứt → dashed |
| 3 | QC1-06 | A01 | lane L2 | chính | kind = double, thực tế vạch trắng liền một nét → single |
| 4 | QC1-07 | A01 | drivable (direct) | chính | Một polygon direct phủ cả 3 làn từ L2 tới R2; phải tách: direct giữa L1–R1, hai làn bên là alternative |
| 5 | QC1-09 | A01 | traffic_sign (x≈550–605) | chính | Biển chỉ dẫn xanh: group = prohibitory → information; facing = side → front |
| 6 | QC1-10 | A01 | traffic_sign (bỏ sót) | chính | Thiếu biển xanh nhỏ ở xa (x≈432–450, y≈463–488, cao ≈ 25 px ≥ 8 px) |
| 7 | QC1-12 | A01 | lane L2 | nhẹ | Điểm cuối lặp hai lần (365.5, 499.2) |
| 8 | QC1-06 | A04 | lane R1 | chính | style = solid, thực tế là vạch trắng đứt → dashed |
| 9 | QC1-04 | A04 | lane R2 (bỏ sót) | chính | Thiếu vạch trắng liền cạnh làn xe đạp (R2) |
| 10 | QC1-07 | A04 | drivable (direct) | chính | Polygon direct kéo tới mép phải ảnh, gộp cả làn bên phải và làn xe đạp; thiếu alternative giữa R1–R2 |
| 11 | QC1-01 | A07 | tag weather | nhẹ | weather = fog, ảnh có đường ướt và giọt nước trên kính → rain |
| 12 | QC1-01 | B02 | tag camera | nặng | camera = fisheye_rear, tên file FV → fisheye_front |
| 13 | QC1-11 | B02 | traffic_light (x≈1077–1140) | chính | Đèn sát mép ảnh, tâm box ngoài 80 % bán kính nhưng edge_zone = false |
| 14 | QC1-11 | B02 | traffic_light (x≈110–156) | chính | Đèn sát mép ảnh, tâm box ngoài 80 % bán kính nhưng edge_zone = false |
| 15 | QC1-07 | B05 | road_curb (bỏ sót) | chính | Thiếu road_curb mép vỉa hè phía xa (x≈430,y≈100 → x≈890,y≈170) |
| 16 | QC1-07 | B05 | road_curb (bỏ sót) | chính | Thiếu road_curb mép đảo giữa bên phải (x≈900,y≈180 → x≈1110,y≈400) |
| 17 | QC1-03 | B06 | lane (x≈170,y≈258) | nặng | Camera trái (MVL): position = L1 → phải là other |
| 18 | QC1-11 | B06 | lane (x≈170,y≈258) | chính | Một polyline nối thẳng từ (277,253) tới (927,492), gộp hai vạch khác nhau và không đi theo cung |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A07 | Vạch sát dải bê tông bên trái có đủ rõ để bắt buộc có L1 không? (lint báo thiếu L1) |  |
| B02 | Hai cụm đèn sát mép là đèn xe (vehicle) hay đèn người đi bộ (pedestrian), và có quay về xe (facing front) không? |  |

## Quyết định
Lỗi nặng: 2   Lỗi chính: 14 / 45 nhãn = 31,1 %   Lỗi nhẹ: 2   Ca chờ lead: 2  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Còn 2 lỗi nặng (B02 sai tag camera, B06 lane camera hai bên không phải `other`), và tỉ lệ lỗi chính 31,1 % vượt ngưỡng 5 %. Có lỗi nặng thì Rework, không cần chờ trả lời hai ca mơ hồ.

Ghi chú ngoài mẫu (lint trên các ảnh không nằm trong mẫu, để bạn tự sửa): B01 và B09 cũng sai camera (fisheye_rear thay vì fisheye_front); A10 thiếu cả 4 tag; B07, B08 lane camera hai bên chưa là `other`; B12 chưa có nhãn nào.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
