# Ngày 1: Nền Tảng Cơ Bản (5 giờ)

**Mục tiêu:** Làm quen với Python, cách nhập/xuất dữ liệu và kiểm soát luồng cơ bản.

## Giờ 1: `print()` và Biến (Variable) - 60 phút
### Lý thuyết (20 phút)
- `print()`: In dữ liệu (chuỗi, số, biến).
- Biến: Lưu giá trị, không cần khai báo kiểu.

### Thực hành (30 phút)
```python
name = "Alex"
age = 25
print(f"Hi, I’m {name}, {age} years old.")
```

### Bài tập (10 phút)
Tạo 3 biến (tên, tuổi, thành phố) và in thành câu hoàn chỉnh.

---

## Giờ 2: `input()` - 60 phút
### Lý thuyết (20 phút)
- Lấy dữ liệu người dùng.
- Chuyển kiểu (`int()`, `float()`).

### Thực hành (30 phút)
```python
name = input("Your name: ")
age = int(input("Your age: "))
print(f"In 10 years, {name} will be {age + 10}.")
```

### Bài tập (10 phút)
Hỏi năm sinh, tính tuổi `(2025 - năm sinh)`.

---

## Giờ 3: Câu lệnh điều kiện (`if-else`) - 60 phút
### Lý thuyết (20 phút)
- Kiểm tra điều kiện với `if`, `elif`, `else`.

### Thực hành (30 phút)
```python
age = int(input("Enter age: "))
if age >= 18:
    print("Adult")
else:
    print("Minor")
```

### Bài tập (10 phút)
Hỏi số, kiểm tra chẵn/lẻ (dùng `%`).

---

## Giờ 4: Chuỗi (Strings) - 60 phút
### Lý thuyết (20 phút)
- Cắt chuỗi, phương thức (`upper()`, `lower()`, `len()`).

### Thực hành (30 phút)
```python
text = "python"
print(text[0:3])  # pyt
print(text.upper())  # PYTHON
print(len(text))  # 6
```

### Bài tập (10 phút)
Hỏi tên, in chữ cái đầu in hoa.

---

## Giờ 5: Toán tử (Operators) - 60 phút
### Lý thuyết (20 phút)
- Toán tử số học (`+`, `-`, `*`, `/`, `%`).
- Toán tử so sánh (`==`, `<`).
- Toán tử logic (`and`, `or`).

### Thực hành (30 phút)
```python
a = 10
b = 3
print(a + b, a % b)  # 13 1
print(a > b and b != 0)  # True
```

### Bài tập (10 phút)
Hỏi 2 số, in tổng và kiểm tra số nào lớn hơn.

---

## **Kết quả Ngày 1**
Bạn hiểu cách nhập/xuất dữ liệu, lưu trữ, thao tác chuỗi và ra quyết định cơ bản.

---

# **Lưu Ý**
- **Thực hành:** Chạy code từng phần, thử thay đổi giá trị.
- **Ôn tập:** Cuối mỗi ngày, viết lại 1-2 ví dụ không nhìn code.
- **Công cụ:** Dùng IDLE, VS Code hoặc Google Colab để chạy.