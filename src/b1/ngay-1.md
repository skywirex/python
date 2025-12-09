# Ngày 1: Nền Tảng Cơ Bản (5 giờ)

**Mục tiêu:** Làm quen với Python, cách nhập/xuất dữ liệu và kiểm soát luồng cơ bản.

## Giờ 1: `print()` và Biến (Variable) - 60 phút
### Lý thuyết (20 phút)
 * `print()`: In dữ liệu (chuỗi, số, biến).
 * Biến: Lưu giá trị của dữ liệu, không cần khai báo kiểu.

### Varibles (Biến)

Biến trong Python là một tên đại diện để **lưu những giá trị của dữ liệu**. Dữ liệu lưu trữ có nhiều loại, Python có năm loại dữ liệu tiêu chuẩn, đó là: Numbers, String, List, Tuple và Dictionary.  

Python là ngôn ngữ dynamically typed, tức là không cần khai báo kiểu dữ liệu cho biến trước khi sử dụng. Python sẽ tự động xác định kiểu dữ liệu dựa trên giá trị được gán.  

Tên biến có thể là 1 kí tự, nhưng thông thường là một từ hoặc là một cụm từ mô tả ngắn dưới dạng chữ thường cách nhau bởi dấu gạch dưới.

![varibles](https://pub-b731809282d4443bba205fbf4c8ae4ee.r2.dev/98f3312f83fcd4ac7c8dea96b5bc2f37.png)

Lưu ý khi đặt tên biến:
 * Tên biến chỉ có thể chứa chữ cái, số và dấu gạch dưới (_).
 * Không được bắt đầu bằng số (hợp lệ: my_var, không hợp lệ: 2var).
 * Python phân biệt chữ hoa - chữ thường (age và Age là hai biến khác nhau).
 * Không được trùng với từ khóa của Python (ví dụ: if, for, while không thể dùng làm tên biến).

Dưới đây là ví dụ cụ thể cho năm loại dữ liệu tiêu chuẩn trong Python:

**1. Kiểu số (Numbers)**

Kiểu số bao gồm số nguyên (int), số thực (float), và số phức (complex).

Ví dụ:

```python
so_nguyen = 10         # int
so_thuc = 3.14         # float
so_phuc = 2 + 3j       # complex

print(so_nguyen, type(so_nguyen))  # 10 <class 'int'>
print(so_thuc, type(so_thuc))      # 3.14 <class 'float'>
print(so_phuc, type(so_phuc))      # (2+3j) <class 'complex'>
```

**2. Kiểu chuỗi (String)**

Chuỗi ký tự có thể được tạo bằng dấu nháy đơn '...', nháy đôi "...", hoặc chuỗi nhiều dòng '''...'''.

Ví dụ:

```python
chuoi = "Hello, Python!"
chuoi_nhieu_dong = """Đây là một chuỗi 
nhiều dòng trong Python"""

print(chuoi)  
print(chuoi_nhieu_dong)
print(type(chuoi))  # <class 'str'>
```

**3. Kiểu danh sách (List)**

Danh sách chứa nhiều phần tử, có thể thay đổi được (mutable).

Ví dụ:

```python
danh_sach = [1, 2.5, "Python", True]

print(danh_sach)  
print(danh_sach[2])  # Python (truy cập phần tử theo chỉ mục)
danh_sach.append("New Item")  # Thêm phần tử vào danh sách
print(danh_sach)
print(type(danh_sach))  # <class 'list'>
```
**4. Kiểu bộ (Tuple)**

Giống list, nhưng không thể thay đổi sau khi khởi tạo (immutable).

Ví dụ:

```python
bo = (10, 20, "Hello")

print(bo)  
print(bo[1])  # 20
# bo[0] = 100  # ❌ Lỗi vì tuple không thể thay đổi
print(type(bo))  # <class 'tuple'>
```

**5. Kiểu từ điển (Dictionary)**

Lưu trữ dữ liệu theo cặp key: value, giúp truy xuất dữ liệu nhanh chóng.

Ví dụ:

```python
tu_dien = {
    "ten": "Python",
    "nam_phat_hanh": 1991,
    "nguoi_tao": "Guido van Rossum"
}

print(tu_dien)  
print(tu_dien["ten"])  # Python (truy cập bằng key)
tu_dien["phien_ban"] = 3.10  # Thêm một cặp key-value
print(tu_dien)
print(type(tu_dien))  # <class 'dict'>
```

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
- **Công cụ:** Dùng IDLE, VS Code.