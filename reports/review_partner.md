# Self-review - bài làm solo

Người gán: Quan1242  
Người kiểm: Quan1242 (self-review)  
Ngày: 2026-09-16

Bài được thực hiện solo nên không có bài của partner để chạy compare visibility. Các mục
có thể kiểm bằng công cụ local đã được đối chiếu với `outputs/vis_train`,
`reports/visibility_report.md` và kết quả `check_pose_labels.py`.

| Mục | Kết quả | Bằng chứng |
| --- | --- | --- |
| Đủ 17 điểm cho mỗi skeleton | Đạt định dạng | `check_pose_labels.py` chạy exit code 0 |
| Kiểm tra hình dáng | Đã tạo output | `outputs/vis_train/` |
| Visibility report | Đạt | `reports/visibility_report.md` và `outputs/visibility_report.json` |
| COCO Keypoints export | Đã có | `annotations/coco_keypoints/person_keypoints_default.json` |
| YOLO Pose export | Đạt định dạng | 20 file trong `dataset/labels/train/` |
| Peer comparison | N/A | Làm bài solo, không có thư mục bài partner |

## Lỗi tìm được trong self-review

| Ảnh | Người thứ | Khớp | Lỗi gì | Sửa thế nào |
| --- | ---: | --- | --- | --- |
| `train_13.jpg` | 1 | toàn bộ skeleton | Thiếu một người so với gold | Mở lại ảnh trong CVAT, gán đủ 17 keypoint rồi export/convert lại |

## Hai câu kết luận

- Lỗi cần ưu tiên là thiếu một người ở `train_13.jpg`; evaluator ghi nhận 1 `thieu_nguoi`.
- Đây là lỗi bao phủ/thao tác, không thể kết luận là lỗi guideline khi không có peer review.