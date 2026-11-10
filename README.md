# 19.11 — Chuyên Hạ Long · V6

V6 phát triển từ nền tảng V5, giữ nguyên ý tưởng tổng thể: khu vực video/ảnh ở phần đầu, lời mời khám phá Vườn Trái Tim và kho 36 lời chúc theo ba khối.

## Những gì được giữ nguyên
- Giữ nguyên bố cục và ý tưởng video nổi bật + thư viện video/hình ảnh.
- Giữ nguyên cơ chế thêm video sau thông qua `MEDIA_ITEMS` trong `data.js`.
- Giữ nguyên toàn bộ 36 lớp và 36 lời chúc trong `data.js` từ V5; không biên tập lại câu chữ, emoji hay nội dung đa ngôn ngữ.
- Giữ nguyên bộ lọc khối, tìm kiếm, mở thư ngẫu nhiên và khả năng đổi giao diện.
- Thư mục `media/` vẫn để trống/chờ video. Không thêm video mẫu hoặc thay đổi nội dung video.

## Cải tiến V6
1. **Midnight Galaxy:** nền tối mặc định, tinh vân tím-xanh, bụi sao và ánh sáng nền tiết chế.
2. **Nhận diện thư:** mỗi môn/lớp có màu riêng thay vì chỉ chia ba màu gần nhau theo khối.
3. **Mở thư có nhịp:** hộp thư xuất hiện bằng chuyển động nhẹ trước khi bắt đầu gõ chữ.
4. **Hiệu ứng đánh máy:** hiển thị từng ký tự theo nhịp chậm hơn, có khoảng nghỉ tự nhiên ở dấu câu và xử lý chữ có dấu/emoji theo cụm ký tự.
5. **Âm thanh gõ phím:** tiếng click điện tử rất nhẹ, bật mặc định; có nút tắt/bật. Âm thanh dùng Web Audio, không cần tải file âm thanh.
6. **Điều khiển đọc:** chọn tốc độ Chậm/Vừa/Nhanh, Tạm dừng/Đọc tiếp, Hiện toàn bộ.
7. **Tiến độ:** thanh tiến độ cho biết phần lời chúc đã xuất hiện.
8. **Trải nghiệm nhỏ:** số lượng kết quả lọc, trạng thái nút rõ ràng, phản hồi khi chạm, focus bàn phím và hỗ trợ `prefers-reduced-motion`.
9. **Tối ưu di động:** hộp thư và cụm điều khiển tự xếp lại trên màn hình nhỏ.

## Cấu trúc
- `index.html`: cấu trúc trang và hộp thư.
- `style.css`: giao diện V6 và các hiệu ứng.
- `app.js`: tương tác, bộ lọc, hiệu ứng đánh máy, âm thanh, thư viện media.
- `data.js`: dữ liệu 36 lớp, 36 lời chúc và cấu hình media.
- `media/`: chờ video/ảnh thật.

## Thêm video sau
Cấu hình `MEDIA_ITEMS` trong `data.js` theo hướng dẫn bên dưới và đặt file thật trong `media/`:

```js
const MEDIA_ITEMS = [
  {
    title: "Video 19.11",
    src: "media/video-1911.mp4",
    type: "video",
    poster: "media/poster-1911.jpg"
  }
];
```

Sau đó tải toàn bộ thư mục dự án lên máy chủ/GitHub Pages. Video đầu tiên sẽ được chọn làm nội dung nổi bật.

## Lưu ý âm thanh và trình duyệt
- Âm thanh gõ phím được tạo tại trình duyệt bằng Web Audio sau thao tác mở thư; một số trình duyệt có thể cần thao tác người dùng trước khi phát âm thanh.
- Nếu người xem tắt âm thanh, hiệu ứng chữ vẫn hoạt động bình thường.
- Chế độ tối là mặc định. Nút góc trên vẫn cho phép chuyển sáng nếu người dùng muốn.
- Khi bật cài đặt giảm chuyển động của hệ điều hành, chữ sẽ hiện đầy đủ để tránh gây khó chịu.

## Kiểm tra đã thực hiện
- JavaScript được kiểm tra cú pháp bằng Node.js.
- Dữ liệu có 12 lớp ở mỗi khối, tổng cộng 36 lớp và 36 nội dung thư.
- `data.js` được giữ nguyên byte-for-byte so với bản V5.
- `media/` không được bổ sung video mới.
- Cần kiểm thử trực quan thêm trên điện thoại và máy tính trước khi phát hành chính thức.
