# DAY 03 – IMAGE SEGMENTATION REPORT

## 1. Thông tin học viên

- **Họ và tên:** Mai Van Phong
- **MSSV:** 2A202603256
- **Bài thực hành:** K5 – Level 2 – Day 03 – Image Segmentation
- **Công cụ gán nhãn:** Roboflow
- **Công cụ kiểm tra và xuất dữ liệu:** CVAT

## 2. Các task đã thực hiện

| Task | Loại segmentation | Số ảnh | Trạng thái |
|---|---|---:|---|
| easy_semantic | Semantic | 3 | Đã gán nhãn |
| medium_instance | Instance | 3 | Đã gán nhãn |
| hard_panoptic | Panoptic | 2 | Đã gán nhãn |
| cp1_holes | Checkpoint | 1 | Đã gán nhãn |
| cp2_slice | Checkpoint | 1 | Đã gán nhãn |
| cp3_thin | Checkpoint | 1 | Đã gán nhãn |
| cp4_curb | Checkpoint | 1 | Đã gán nhãn |
| cp5_occlusion | Checkpoint | 1 | Đã gán nhãn |
| cp6_coverage | Checkpoint | 1 | Đã gán nhãn |

**Tổng cộng:** 9 task, 14 ảnh.

## 3. Quyết định gán nhãn Medium Instance đầu tiên

- **Task:** medium_instance
- **Ảnh:** [Điền tên ảnh]
- **Object đầu tiên:** [Điền tên đối tượng]
- **Class:** [Điền class tương ứng]
- **Quy tắc chọn biên:** Gán mask theo đường biên của phần đối tượng thực sự nhìn thấy, không bao gồm phần nền xung quanh. Với các đối tượng bị che khuất, chỉ gán phần quan sát được và giữ đúng định danh instance theo quy tắc bài thực hành.

**Giải thích:** Việc sử dụng mask giúp xác định chính xác hình dạng đối tượng thay vì chỉ sử dụng bounding box. Mỗi đối tượng riêng biệt cần được giữ thành một instance độc lập.

## 4. Lỗi phát hiện và cách xử lý

- **Task:** [Điền task thực tế]
- **Ảnh:** [Điền tên ảnh]
- **Vị trí lỗi:** [Điền vị trí]
- **Loại lỗi:** [Thiếu vùng / sai class / mask tràn nền / gộp instance / sai ranh giới]
- **Dấu hiệu quan sát:** [Mô tả lỗi thực tế đã phát hiện]

**Hành động xử lý:** Kiểm tra lại vùng annotation, điều chỉnh mask theo ranh giới thực tế của đối tượng và kiểm tra lại class tương ứng.

**Trạng thái:** [Đã sửa và Save / Chưa sửa / Chưa kiểm tra].

## 5. Ba trường hợp khó quyết định

### Trường hợp 1 – Ranh giới Road và Sidewalk

- **Hai cách hiểu:** Vùng chuyển tiếp có thể thuộc road hoặc sidewalk.
- **Căn cứ:** Chức năng sử dụng của vùng và ranh giới bó vỉa.
- **Quyết định:** Ưu tiên xác định theo chức năng của khu vực, không chỉ dựa vào sự khác biệt màu sắc.

### Trường hợp 2 – Hai phương tiện nằm sát nhau

- **Hai cách hiểu:** Có thể xem hai phương tiện là một vùng mask hoặc hai instance riêng biệt.
- **Căn cứ:** Mỗi phương tiện là một đối tượng độc lập.
- **Quyết định:** Tách thành hai instance riêng, không gộp mask của hai phương tiện.

### Trường hợp 3 – Đối tượng bị che khuất (Occlusion)

- **Hai cách hiểu:** Tách phần nhìn thấy thành nhiều object hoặc giữ cùng một instance.
- **Căn cứ:** Quy tắc instance trong đề bài yêu cầu duy trì định danh của một vật thể bị che khuất.
- **Quyết định:** Giữ một instance cho cùng một đối tượng và chỉ gán phần thực sự nhìn thấy, không tự suy đoán vùng bị che.

## 6. Kết luận

Thông qua bài thực hành Day 03, tôi đã thực hiện gán nhãn dữ liệu segmentation trên 9 task với tổng cộng 14 ảnh bằng Roboflow.

Bài thực hành giúp tôi hiểu rõ hơn sự khác biệt giữa Semantic Segmentation, Instance Segmentation và Panoptic Segmentation; cách xác định ranh giới mask, phân biệt các instance và xử lý những trường hợp bị che khuất.

Tôi cũng nhận thấy rằng chất lượng annotation không chỉ phụ thuộc vào công cụ mà còn phụ thuộc vào việc hiểu đúng định nghĩa class, áp dụng nhất quán quy tắc gán nhãn và thực hiện kiểm tra chất lượng dữ liệu trước khi xuất dataset.

**Trạng thái hoàn thiện bài nộp:** [Điền trạng thái thực tế của CVAT export, ZIP và GitHub].
