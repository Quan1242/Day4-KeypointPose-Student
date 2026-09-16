# Reviewer report

Người gán: Nghiêm Việt Quân  
Người kiểm: Phù Ngô Việt Anh  
Ngày: 2026-09-16

## Phạm vi kiểm tra

Không có thư mục nhãn của partner trong workspace để chạy kiểm chéo. Vì vậy báo cáo
này ghi rõ các kiểm tra đã thực hiện trên artifact hiện có, không đại diện cho một peer
review đầy đủ của bài khác.

## Kết quả kiểm tra artifact

| Mục | Kết quả | Bằng chứng |
| --- | --- | --- |
| Đủ 20 file nhãn train | Đạt | `dataset/labels/train/train_01.txt` đến `train_20.txt` |
| Đủ 17 keypoint và đúng định dạng YOLO Pose | Đạt định dạng | `check_pose_labels.py` chạy exit code 0 |
| COCO Keypoints export | Có | `annotations/coco_keypoints/person_keypoints_default.json` |
| Visibility report | Có | `outputs/visibility_report.json`, `reports/visibility_report.md` |
| Hình visualize | Có | `outputs/vis_train/` |
| So sánh với gold | Có | `outputs/eval_vs_gold.json` |

## Lỗi/cảnh báo phát hiện

Các mục dưới đây được phát hiện khi tự kiểm bài hiện tại; không phải kết quả so sánh
với nhãn của partner:

| Ảnh | Người thứ | Khớp | Lỗi gì | Sửa thế nào |
| --- | ---: | --- | --- | --- |
| `train_13.jpg` | 1 | toàn bộ skeleton | Gold báo thiếu một người | Mở lại CVAT, gán đủ 17 keypoint, export và convert lại |
| `train_04.jpg` | 1 | 4 keypoint `v=0` | Người còn nằm trong ảnh nhưng có điểm bị đánh Outside | Xem lại từng điểm, dùng `v=1` và đặt chấm nếu bị che |
| `train_10.jpg` | 1 | 4 keypoint `v=0` | Người còn nằm trong ảnh nhưng có điểm bị đánh Outside | Xem lại từng điểm, dùng `v=1` và đặt chấm nếu bị che |
| `train_16.jpg` | 2 | vai/hông trái-phải | Có dấu hiệu đảo trái/phải | Kiểm tra theo cơ thể người rồi sửa trong CVAT |

## Kết luận

- Peer review partner: **chưa thực hiện được vì chưa có artifact của partner**.
- Lỗi lặp lại chính trong self-check là visibility ở người còn trong khung và nguy cơ
  đảo trái/phải; cần sửa trong CVAT trước khi export lại.
- Không dùng báo cáo này để khẳng định đã hoàn thành peer review của người khác.