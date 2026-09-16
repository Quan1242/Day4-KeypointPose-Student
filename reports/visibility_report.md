# Visibility report

- Thư mục nhãn: `dataset\labels\train`
- 20 ảnh, 28 skeleton, trung bình 16.07 khớp có v > 0 mỗi người
- Tổng: v=2 355 | v=1 95 | v=0 26

| # | Khớp | v=2 | v=1 | v=0 | %v=1 |
| ---: | --- | ---: | ---: | ---: | ---: |
| 0 | nose | 23 | 5 | 0 | 18% |
| 1 | left_eye | 22 | 6 | 0 | 21% |
| 2 | right_eye | 22 | 6 | 0 | 21% |
| 3 | left_ear | 13 | 15 | 0 | 54% |
| 4 | right_ear | 16 | 12 | 0 | 43% |
| 5 | left_shoulder | 26 | 2 | 0 | 7% |
| 6 | right_shoulder | 27 | 1 | 0 | 4% |
| 7 | left_elbow | 25 | 3 | 0 | 11% |
| 8 | right_elbow | 25 | 3 | 0 | 11% |
| 9 | left_wrist | 22 | 6 | 0 | 21% |
| 10 | right_wrist | 21 | 6 | 1 | 21% |
| 11 | left_hip | 23 | 5 | 0 | 18% |
| 12 | right_hip | 19 | 8 | 1 | 29% |
| 13 | left_knee | 18 | 6 | 4 | 21% |
| 14 | right_knee | 21 | 3 | 4 | 11% |
| 15 | left_ankle | 16 | 4 | 8 | 14% |
| 16 | right_ankle | 16 | 4 | 8 | 14% |

## Đọc bảng này thế nào

1. Khớp nào có **%v=1 cao**: khớp hay bị che. Cổ tay và hông thường là hai vị trí cần xem lại guideline trước khi kết luận.
2. Khớp nào có **v=0 cao bất thường**: mọi người đang dùng Outside ở chỗ đáng lẽ là Occluded. Đó là lỗi số 3 của slide 46, và nó xoá thẳng khớp đó khỏi bảng điểm OKS.
3. Khi so hai người: **lệch lớn = bất đồng về guideline**, không phải về bức ảnh. Sửa guideline trước, sửa nhãn sau.
