# Self-review checklist - bài solo

Người gán/kiểm: Quan1242  
Ngày: 2026-09-16

| # | Mục kiểm | Kết quả | Ghi chú |
| ---: | --- | --- | --- |
| 1 | Mọi người đủ 17 điểm | Cần sửa | Gold còn báo thiếu 1 người ở `train_13.jpg` |
| 2 | Không có xương cắt chéo | Đã kiểm bằng visualize | Xem `outputs/vis_train/` |
| 3 | Không kéo xương sang người khác | Đã kiểm bằng visualize | Self-review |
| 4 | Khớp bị che dùng `v=1` | Đạt theo guideline | Visibility report có 95 điểm `v=1` |
| 5 | `v=0` chỉ cho outside | Cần rà lại | Có 26 điểm `v=0`, cần đối chiếu ảnh biên |
| 6 | Không dùng Hidden | Đạt định dạng | `check_pose_labels.py` exit code 0 |
| 7 | COCO Keypoints 1.0 | Đã có | `annotations/coco_keypoints/person_keypoints_default.json` |
| 8 | YOLO Pose 56 số, `[17,3]` | Đạt định dạng | `check_pose_labels.py` exit code 0 |
| 9 | Visibility report | Đạt | JSON và Markdown đã có |
| 10 | Ca không rõ trong guideline | Đã ghi | 3 ca trong `GUIDELINE_MINI.md` |
| 11 | Check script 0 lỗi | Đạt | Đã chạy local |

## Peer review

N/A: bài làm solo, không có bài partner để kiểm chéo.