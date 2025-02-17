# Ngày 1

Dành 3 giờ để nắm vững 4 khái niệm chính:  

1. **Hàm `print()`** – Dùng để hiển thị dữ liệu ra màn hình.  
2. **Biến (Variable)** – Dùng để lưu trữ giá trị.  
3. **Nhập dữ liệu (`input()`)** – Lấy dữ liệu từ người dùng.  
4. **Câu lệnh điều kiện (`if-else`)** – Kiểm tra điều kiện và thực hiện các hành động tương ứng.  

---

### 1. `print()`: Xuất dữ liệu ra màn hình  

Hàm `print()` giúp in thông tin ra màn hình.  

**Ví dụ:**  
```python
print("Xin chào, Python!")
print("Tổng của 5 + 3 là:", 5 + 3)
```

📌 **Lưu ý**: Dùng dấu `,` để nối nhiều giá trị trong `print()`.  

---

### 2. Biến trong Python  

Biến dùng để lưu trữ dữ liệu. Python không cần khai báo kiểu dữ liệu, chỉ cần gán giá trị.  

**Ví dụ:**  
```python
ten = "Alice"
tuoi = 25
diem_tb = 8.5

print("Tên:", ten)
print("Tuổi:", tuoi)
print("Điểm trung bình:", diem_tb)
```

📌 **Lưu ý**:  
- Biến không được đặt tên bắt đầu bằng số.  
- Không dùng dấu cách trong tên biến (dùng `_` thay thế).  

---

### 3. Nhập dữ liệu từ bàn phím (`input()`)  

Hàm `input()` giúp nhập dữ liệu từ người dùng.  
- Mặc định, `input()` trả về kiểu **chuỗi (`str`)**.  
- Dùng `int()` hoặc `float()` để chuyển sang số nếu cần.  

**Ví dụ:**  
```python
ten = input("Nhập tên của bạn: ")
tuoi = int(input("Nhập tuổi của bạn: "))  # Chuyển đổi thành số nguyên
print("Xin chào,", ten, "bạn", tuoi, "tuổi!")
```

📌 **Lưu ý**: Dùng `int()` hoặc `float()` khi nhập số để có thể thực hiện tính toán.  

---

### 4. Câu lệnh điều kiện `if-else`  

Dùng `if-else` để kiểm tra điều kiện và quyết định chương trình sẽ chạy như thế nào.  

**Ví dụ:**  
```python
diem = float(input("Nhập điểm của bạn: "))

if diem >= 5:
    print("Bạn đã đậu!")
else:
    print("Bạn đã rớt!")
```

📌 **Lưu ý**:  
- Dùng dấu **:`** sau `if` và `else`.  
- Thụt lề (indent) quan trọng trong Python.  

---

### 📌 Tóm tắt nhanh  
- Dùng `print()` để in ra màn hình.  
- Biến lưu trữ dữ liệu, không cần khai báo kiểu.  
- `input()` nhận dữ liệu từ người dùng.  
- `if-else` để kiểm tra điều kiện.  

Dưới đây là một số bài tập thực hành cho từng phần để bạn luyện tập.  

---

### 📝 **Bài 1: Luyện tập `print()`**  
Viết chương trình in ra màn hình các thông tin sau:  
```
Học Python cơ bản
Tổng của 15 và 25 là: 40
```
👉 **Gợi ý**: Dùng `print()` và phép cộng `+`.  

---

### 📝 **Bài 2: Luyện tập về biến**  
1. Tạo 3 biến: `ten`, `tuoi`, `so_thich`, gán giá trị cho chúng.  
2. In ra màn hình câu:  
   ```
   Xin chào, tôi là [tên]. Tôi [tuổi] tuổi và tôi thích [sở thích].
   ```  
👉 **Gợi ý**: Sử dụng `print()` với dấu `,` hoặc chuỗi f-string (`f"..."`).  

---

### 📝 **Bài 3: Nhập dữ liệu từ bàn phím**  
Viết chương trình yêu cầu người dùng nhập tên và năm sinh, sau đó tính tuổi và in ra màn hình.  
```
Nhập tên của bạn: An
Nhập năm sinh của bạn: 2000
Xin chào An! Năm nay bạn 24 tuổi.
```
👉 **Gợi ý**: Dùng `input()`, `int()` để tính tuổi.  

---

### 📝 **Bài 4: Câu lệnh `if-else`**  
Viết chương trình nhập điểm trung bình của một học sinh và kiểm tra kết quả:  
- Nếu điểm >= 8 → "Giỏi"  
- Nếu điểm >= 5 → "Khá"  
- Nếu điểm < 5 → "Yếu"  

👉 **Gợi ý**: Dùng `if-elif-else`.  

---

### 🔥 **Bài 5: Tổng hợp**  
Viết chương trình yêu cầu người dùng nhập hai số và hiển thị menu:  
```
Nhập số thứ nhất: 10  
Nhập số thứ hai: 5  
Chọn phép tính: (+, -, *, /)  
Nhập phép tính: *  
Kết quả: 50  
```
👉 **Gợi ý**:  
- Dùng `input()` để nhập hai số và phép tính.  
- Dùng `if-elif-else` để xử lý từng phép toán.  
