## **Phần 1: Đề xuất chiến lược**

### **Chiến lược 1: Phân rã theo trạng thái của chuyến**

Tách Epic dựa trên thời điểm khách thực hiện hủy:

- F1 – Hủy trước khi tài xế nhận chuyến  
- F2 – Hủy sau khi tài xế nhận chuyến

### **Chiến lược 2: Phân rã theo hành vi/chức năng**

Tách Epic thành các chức năng chính của hệ thống:

- F1 – Thực hiện hủy chuyến  
- F2 – Tính phí hủy chuyến  
- F3 – Tính lại giá chuyến cho khách còn lại  
- F4 – Thông báo thay đổi giá chuyến

## **Phần 2: So Sánh**

| Tiêu chí  | Chiến lược 1 – Theo trạng thái  | Chiến lược 2 – Theo chức năng  |
| :---: | ----- | ----- |
| **Independent**  | \+ Mỗi Feature tập trung vào một trạng thái rõ ràng: trước hoặc sau khi tài xế nhận chuyến. Ít phụ thuộc chéo khi triển khai.  | – Các chức năng phụ thuộc lẫn nhau. Hủy chuyến phải liên quan đến tính phí, tính lại giá và thông báo nên khó triển khai hoàn toàn độc lập.  |
| **Small**  | \+ Phạm vi được giới hạn theo từng trạng thái nghiệp vụ nên dễ tiếp tục tách thành User Story nhỏ.  | – Một số Feature có thể khá nhỏ nhưng khi triển khai thực tế phải kết hợp nhiều chức năng mới tạo thành luồng hoàn chỉnh.  |
| **Valuable**  | \+ Mỗi Feature tạo ra một giá trị nghiệp vụ rõ ràng: xử lý đúng chính sách hủy và phí tương ứng  | – Một số Feature riêng lẻ chưa tạo ra giá trị hoàn chỉnh cho người dùng. Ví dụ "Tính phí hủy" nếu không kết hợp với việc hủy chuyến thì chưa mang lại một luồng nghiệp vụ hoàn chỉnh.  |

## **Phần 3: Lựa chọn**

- Chọn chiến lược 1 \- Phân rã theo trạng thái của chuyến. Chiến lược này phù hợp hơn vì mỗi Feature gắn trực tiếp với một quy tắc nghiệp vụ rõ ràng, đồng thời tạo ra giá trị có thể kiểm chứng được   
- User Story: “Là một khách hàng, tôi muốn hủy chuyến ghép của mình, để hệ thống áp dụng đúng phí hủy dựa trên thời điểm máy chủ ghi nhận yêu cầu hủy “  
- Trường hợp hủy đúng lúc tài xế nhận chuyến:  
+ Given:  
* Khách đang có một chuyến ghép.  
* Tài xế thực hiện nhận chuyến gần như đồng thời với yêu cầu hủy của khách.  
* Hệ thống ghi nhận thời điểm tài xế nhận chuyến và thời điểm khách hủy trên máy chủ.  
+ When;  
* Khách gửi yêu cầu hủy chuyến.  
* Hệ thống xác định trạng thái dựa trên thời điểm được máy chủ ghi nhận.  
+ Then:   
* Nếu thời điểm máy chủ ghi nhận yêu cầu hủy trước thời điểm tài xế nhận chuyến \-\> khách được miễn phí hủy.  
* Nếu thời điểm máy chủ ghi nhận yêu cầu hủy sau thời điểm tài xế nhận chuyến \-\> khách bị tính phí hủy 10.000đ.  
* Không sử dụng thời gian hiển thị trên thiết bị của khách hoặc tài xế làm căn cứ tính phí.

  