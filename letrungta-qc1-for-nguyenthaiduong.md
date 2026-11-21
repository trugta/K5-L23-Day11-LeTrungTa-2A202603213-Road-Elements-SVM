# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Nguyễn Thái Dương       Người kiểm (học viên): Lê Trung Tá 
Ngày: 21/11/2026                         Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest):  nguyenthaiduong-fisheye, manifest_fisheye và nguyenthaiduong-front, manifest_front
Số ảnh kiểm: 6 (+ 14 ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag):  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 20 | 20 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 20 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 20 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 20 | 2 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 20 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 20 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 20 | 3 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 20 | 2 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 20 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 20 | 1 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 8 | 8 | chính |
| QC1-12 file | lỗi file | 20 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-01 | A01_bc5fadac-fa6dd225.jpg |  | nặng |  thiếu tag |
| 2 | QC1-01 | A02_b3c26aff-63a0d7d6.jpg |  | nặng |  thiếu tag |
| 3 | QC1-01 | A03_b1c66a42-6f7d68ca.jpg |  | nặng |  thiếu tag |
| 4 | QC1-02 | A03_b1c66a42-6f7d68ca.jpg | 19 | chính |  sai nhãn |
| 5 | QC1-01 | A04_b7a8e795-0ff55db2.jpg |  | nặng |  thiếu tag |
| 6 | QC1-01 | A05_b2576c8c-2de20b8a.jpg |  | nặng |  thiếu tag |
| 7 | QC1-01 | A06_b8c66e31-37045eec.jpg |  | nặng |  thiếu tag |
| 8 | QC1-08 | A06_b8c66e31-37045eec.jpg | --- | chính | thiếu |
| 9 | QC1-10 | A06_b8c66e31-37045eec.jpg | --- | chính | bỏ sót |
| 10 | QC1-01 | A07_b41ace08-c8468690.jpg | --- | nặng | thiếu tag |
| 11 | QC1-07 | A07_b41ace08-c8468690.jpg | 54 | chính | sai vùng |
| 12 | QC1-01 | A08_c0deebc1-16cfa791.jpg |  | nặng |  thiếu tag |
| 13 | QC1-01 | A09_c7e6d5d1-c8af9fe3.jpg |  | nặng |  thiếu tag |
| 14 | QC1-01 | A10_b6ff1331-f6d3fba8.jpg |  | nặng |  thiếu tag |
| 15 | QC1-01 | A11_c1f35f18-b529c043.jpg |  | nặng |  thiếu tag |
| 16 | QC1-01 | A12_c0f978fa-9b4e623f.jpg |  | nặng |  thiếu tag |
| 17 | QC1-11 | B01_02688_FV.png | --- | chính | thiếu |
| 18 | QC1-11 | B02_03177_FV.png | --- | chính | thiếu |
| 19 | QC1-08 | B02_03177_FV.png | 9 | chính | sai thuộc tính |
| 20 | QC1-08 | B02_03177_FV.png | 12 | chính | sai thuộc tính |
| 21 | QC1-11 | B03_04267_RV.png | --- | chính | thiếu |
| 22 | QC1-11 | B04_05535_RV.png | --- | chính | thiếu |
| 23 | QC1-09 | B04_05535_RV.png | 21 | chính | sai thuộc tính |
| 22 | QC1-11 | B05_05780_MVL.png | --- | chính | thiếu |
| 23 | QC1-11 | B06_04068_MVL.png| --- | chính | thiếu |
| 24 | QC1-04 | B06_04068_MVL.png | 32 | chính | sai |
| 25 | QC1-04 | B06_04068_MVL.png | 30 | chính | sai |
| 26 | QC1-11 | B07_01216_MVR.png | --- | chính | thiếu |
| 26 | QC1-11 | B08_05783_MVR.png | --- | chính | thiếu |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |

## Quyết định
Lỗi nặng: 12   Lỗi chính: 14 / 157 nhãn = 0.08 %   Lỗi nhẹ: __   Ca chờ lead: __  
Quyết định (Release / Hold / Rework):  Rework
Lý do (theo luật của phiếu):  thiếu nhiều tag

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
