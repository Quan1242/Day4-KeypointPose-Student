# Báo cáo Ngày 4 - Keypoint & Pose

Họ tên: Quan1242  | Nhóm: solo  | Ngày: 2026-09-16

## 1. Nhãn của tôi

| Chỉ số | Giá trị |
| --- | ---: |
| Số ảnh đã gán | 20 |
| Số skeleton | 28 |
| v=2 / v=1 / v=0 | 355 / 95 / 26 |
| Thời gian trung bình mỗi ảnh | Chưa ghi nhận |

Ba khớp có `%v=1` cao nhất là `left_ear` 54%, `right_ear` 43% và `right_hip` 29%.
Tai thường bị tóc hoặc vật che; hông là vị trí phải ước lượng theo giải phẫu thay vì
bề mặt quần áo. Đây là lý do guideline solo dùng `v=1` khi khớp còn trong ảnh nhưng bị che.

## 2. Chấm với gold

Chưa có lần chạy trước rework riêng. Kết quả lần chạy hiện tại:

| Chỉ số | Trước rework | Sau rework |
| --- | ---: | ---: |
| OKS trung bình | 0.9392 | Chưa chạy |
| OKS@0.50 | 0.9655 | Chưa chạy |
| OKS@0.75 | 0.9655 | Chưa chạy |
| Lỗi `dao_trai_phai` | 0 | Chưa chạy |
| Lỗi `nham_nguoi` | 0 | Chưa chạy |
| Lỗi `xoa_khop_bi_che` | 0 | Chưa chạy |

Evaluator ghi nhận 1 người bị thiếu ở `train_13.jpg`, 7 lỗi lệch nhẹ, 47 cờ khác gold
và 69 trường hợp gold để `v=0`. Hai nhóm cờ cuối không trừ OKS theo README.

**Việc cần rework:** mở `train_13.jpg`, bổ sung người thứ nhất với đủ 17 keypoint,
export/convert lại, rồi chạy lại `evaluate_pose_annotations.py`.

## 3. Kiểm chéo

Bài làm solo nên không có bạn cùng nhóm và không có bảng compare. Self-review được ghi
ở `reports/review_partner.md`; `left_ear` là khớp có `%v=1` cao nhất trong bảng solo.

## 4. Model

Số liệu lấy từ `outputs/eval_model.json`, đo trên cùng tập test 10 ảnh:

| Chỉ số | yolo26n-pose gốc | Sau fine-tune | Chênh |
| --- | ---: | ---: | ---: |
| pose_mAP50 | 0.8450 | 0.8450 | +0.0000 |
| pose_mAP50-95 | 0.6853 | 0.6908 | +0.0055 |
| pose_precision | 0.9734 | 0.9792 | +0.0058 |
| pose_recall | 0.8462 | 0.8462 | +0.0000 |
| box_mAP50-95 | 0.8119 | 0.8041 | -0.0078 |

`pose_mAP50-95` tăng 0.0055 sau fine-tune; precision tăng 0.0058 trong khi recall
không đổi. Box mAP50-95 giảm 0.0078, nên fine-tune trên 20 ảnh giúp độ chính xác pose
ở ngưỡng chặt tăng nhẹ nhưng không cải thiện đồng đều khả năng phát hiện người.

Phần phân tích ảnh model cần được bổ sung sau khi xem output visualize của notebook;
không suy luận loại lỗi chỉ từ các con số aggregate.

## 5. Một rule evidence

Với `train_01.jpg`, `left_ear` được xem là khớp còn trong ảnh nhưng bị che khi vị trí có
thể suy ra từ đầu/mặt dù không nhìn rõ bề mặt tai. Khi đó vẫn đặt chấm tại vị trí ước
lượng và dùng `v=1`. Chỉ dùng `v=0` khi vị trí đã nằm ngoài mép ảnh, vì `v=0` bị loại
khỏi phép tính OKS.