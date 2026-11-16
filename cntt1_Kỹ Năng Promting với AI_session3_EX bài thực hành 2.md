# yêu cầu 

## bài làm

**context** : hệ thống Thương mại điện tử phân tích tự động hàng nghìn phản hồi của khách hàng mỗi ngày để định hướng dữ liệu cho các phòng ban xử lý (Kỹ thuật, CSKH, Giao hàng, Kho vận).

**request** : phân tích phản hồi của khách hàng được cung cấp thành một đối tượng dữ liệu duy nhất chứa các trường: sentiment, topics, score, và summary.

**explanation** : 
- sentiment: Chỉ nhận 1 trong 3 giá trị cố định: Positive, Negative, hoặc Neutral.
- topics: Mảng chứa các tag [Product, Delivery, Service, System , feedback đa vấn đề phải gắn tất cả các tag tương ứng.
- score: Điểm số hài lòng từ 1 đến 5.
- summary: Tóm tắt ngắn gọn dưới 15 từ, lọc bỏ từ cảm thán thừa.
- Ngoại lệ: Phản hồi trống hoặc ký tự lỗi -> trả về tag `Invalid`.

**action** : 
1. Đọc và phân tích nội dung phản hồi của khách hàng.
2. Trích xuất sắc thái, chủ đề, chấm điểm và tóm tắt.
3. Tổng hợp kết quả thành định dạng JSON duy nhất.

**tone** : Khách quan, chính xác, kỹ thuật, chuẩn dữ liệu máy đọc.

**extras** :  đầu ra bắt buộc  là định dạng json object thô duy nhất, tuyệt đối không kèm văn bản trang trí hoặc mã bọc ngoài.

**Ví dụ mẫu** : 
 
Input: "Shop đóng gói kỹ, giao hàng siêu nhanh, sản phẩm dùng thích lắm!"
Output: {"sentiment": "Positive", "topics": ["Product", "Delivery"], "score": 5, "summary": "Đóng gói kỹ, giao nhanh và sản phẩm tốt"}

### input (đầu vào) : 
- "Giao hàng nhanh nhưng hộp sản phẩm bị móp méo, dùng không đúng mô tả."

### output (đầu ra) :
- json
```
{
  "sentiment": "Negative",
  "topics": ["Product", "Delivery"],
  "score": 2,
  "summary": "Giao nhanh nhưng sản phẩm móp méo và sai mô tả"
}
```
