# Mini guideline - nhóm: solo  |  người gán: Quan1242  |  ngày: 2026-09-16

> Điền file này **trong lúc** gán nhãn, không phải sau khi xong. Mỗi lần bạn dừng lại
> hơn 10 giây để phân vân, đó là một dòng phải ghi vào đây.

## 1. Luật bắt buộc (đã thống nhất cả lớp - không sửa)

- Bộ 17 điểm COCO, đúng tên, đúng thứ tự. Lấy từ file `.SVG` chung.
- Mọi người trong ảnh đều có **đủ 17 điểm**. Điểm không dùng được thì gắn cờ, không xoá.
- Trái/phải tính theo **cơ thể người**, không theo bức ảnh.
- Bị che, còn trong khung -> `v = 1`, **vẫn đặt chấm** ở vị trí ước lượng.
- Ra ngoài mép ảnh -> `v = 0`, **không** đặt chấm.
- Không dùng `Hidden` (`h`) - nó không được lưu vào file.

## 2. Luật của nhóm bạn (phải điền)

| Tình huống | Luật nhóm bạn chọn | Vì sao |
| --- | --- | --- |
| Hông của người mặc quần áo dài | Ước lượng theo trục vai-thân và vị trí hai chân; nếu còn trong ảnh thì đặt chấm và dùng `v=1` khi bị che. | Hông thường không có bề mặt nhìn thấy nhưng vẫn là khớp cần giữ. |
| Tai bị tóc hoặc mũ bảo hiểm che một phần | Nếu còn xác định được vị trí giải phẫu thì đặt chấm, `v=1`; không thấy và nằm ngoài ảnh thì `v=0`. | Phân biệt bị che với ra ngoài khung. |
| Người bị cắt ở mép ảnh (chỉ thấy từ hông trở lên) | Keypoint nào thực sự ngoài ảnh dùng `v=0` và không đặt chấm; các điểm còn trong ảnh vẫn phải gán. | Không dùng `v=0` cho toàn bộ người. |
| Cổ tay nằm sau tay lái / sau thân mình | Ước lượng theo cẳng tay và bàn tay; còn trong khung thì đặt chấm `v=1`. | Vật che không làm khớp ra khỏi ảnh. |
| Hai người chồng lên nhau | Hoàn thành từng người riêng; nối vai-hông-gối để xác nhận điểm thuộc đúng cơ thể. | Tránh nhầm người và kéo xương sang người kế bên. |
| Người nhỏ đến mức nào thì không gán nữa | Không bỏ skeleton; mọi người trong 20 ảnh đều phải đủ 17 điểm, điểm không rõ thì gắn cờ. | Đây là contract của bài, không tự đặt ngưỡng bỏ người. |

Với mỗi luật, chèn **một ảnh mẫu** (screenshot từ CVAT) thay vì chỉ viết một câu.
Slide 12 nói rõ: khớp không có bề mặt nhìn thấy được thì phải có ảnh mẫu, không phải
một câu văn chung chung.

## 3. Ba ca mơ hồ đã gặp (bắt buộc, ghi ít nhất 3)

### Ca 1 - ảnh `train_01.jpg`, người thứ `1`, khớp `left_ear`

- Mơ hồ ở chỗ nào: tai bị che và gold không gán khớp này.
- Bạn quyết thế nào: giữ vị trí ước lượng nếu tai còn trong khung, dùng `v=1`.
- Vì sao: bị che khác với outside; vị trí vẫn có thể suy ra từ đầu và mặt.
- Nếu người khác quyết ngược lại thì model học sai cái gì: model sẽ học rằng tai bị che luôn không tồn tại.

### Ca 2 - ảnh `train_01.jpg`, người thứ `2`, khớp `nose`

- Mơ hồ ở chỗ nào: người quay/đứng gần nhau làm bên trái ảnh dễ bị hiểu nhầm là left.
- Bạn quyết thế nào: xác định trái/phải theo cơ thể người, rồi kiểm tra đường nối vai-hông.
- Vì sao: nhãn trái/phải phải độc lập với hướng nhìn của người trong ảnh.
- Nếu người khác quyết ngược lại thì model học sai cái gì: model học sai cặp keypoint đối xứng khi augmentation lật ảnh.

### Ca 3 - ảnh `train_13.jpg`, người thứ `1`, khớp `right_ankle`

- Mơ hồ ở chỗ nào: phần chân bị cắt gần mép ảnh.
- Bạn quyết thế nào: chỉ dùng `v=0` cho keypoint thật sự ngoài khung; keypoint còn trong ảnh vẫn đặt chấm.
- Vì sao: COCO loại `v=0` khỏi OKS, nên dùng sai sẽ làm mất thông tin huấn luyện.
- Nếu người khác quyết ngược lại thì model học sai cái gì: model học bỏ qua chân ở vùng biên thay vì dự đoán vị trí bị che.

## 4. Sau khi so visibility report với bạn cùng nhóm

- Khớp lệch `%v=1` nhiều nhất: không có bảng peer để đối chiếu; trong bảng solo, `left_ear` cao nhất với 54%.
- Nguyên nhân là **guideline chưa rõ** hay **một trong hai bên gán sai**: chưa thể kết luận giữa hai người vì bài làm solo.
- Luật mới bổ sung vào mục 2 sau khi thống nhất: không có peer review; tự kiểm theo nguyên tắc khớp còn trong ảnh thì vẫn đặt chấm và dùng `v=1` nếu bị che.
