# Ngày 2: Tăng Cường và Tổ Chức Code (5 giờ)

**Mục tiêu:** Làm việc với dữ liệu phức tạp hơn, tự động hóa và tổ chức code.

## Giờ 1: Vòng lặp (Loops) - 60 phút
### Lý thuyết (20 phút)
- `for` (lặp qua dãy).
- `while` (lặp theo điều kiện).

### Thực hành (30 phút)
```python
for i in range(1, 4):
    print(i)  # 1 2 3

count = 0
while count < 3:
    print(count)
    count += 1
```

### Bài tập (10 phút)
In bảng cửu chương 3.

---

## Giờ 2: Danh sách (Lists) - 60 phút
### Lý thuyết (20 phút)
- Tạo, thêm (`append()`), xóa (`pop()`), truy cập (`[index]`).

### Thực hành (30 phút)
```python
numbers = [1, 2, 3]
numbers.append(4)
print(numbers)  # [1, 2, 3, 4]

for num in numbers:
    print(num * 2)  # 2 4 6 8
```

### Bài tập (10 phút)
Hỏi 3 số, lưu vào danh sách, in tổng.

---

## Giờ 3: Hàm (Functions) - 60 phút
### Lý thuyết (20 phút)
- Định nghĩa hàm, tham số, `return`.

### Thực hành (30 phút)
```python
def square(num):
    return num * num

print(square(5))  # 25
```

### Bài tập (10 phút)
Viết hàm kiểm tra số nguyên tố.

---

## Giờ 4: Kiểu dữ liệu khác (Tuple, Dictionary, Set) - 60 phút
### Lý thuyết (20 phút)
- **Tuple:** Không thay đổi (`(1, 2)`).
- **Dictionary:** Key-value (`{"key": "value"}`).
- **Set:** Không trùng (`{1, 2, 3}`).

### Thực hành (30 phút)
```python
point = (3, 4)
info = {"name": "Alex", "age": 25}
unique = {1, 1, 2}

print(point[0], info["name"], unique)  # 3 Alex {1, 2}
```

### Bài tập (10 phút)
Tạo dictionary lưu tên và điểm 3 môn, in điểm trung bình.

---

## Giờ 5: Xử lý lỗi (Try-Except) và Ôn tập - 60 phút
### Lý thuyết (15 phút)
- Dùng `try-except` để xử lý lỗi.

### Thực hành (25 phút)
```python
try:
    num = int(input("Enter a number: "))
    print(num / 2)
except ValueError:
    print("Invalid input!")
```

### Dự án nhỏ (20 phút)
Viết chương trình:
1. Hỏi tên, tuổi, 3 điểm môn học (dùng `input()`).
2. Lưu vào dictionary.
3. Dùng hàm tính điểm trung bình.
4. Kiểm tra tuổi > 18 để in `"Adult"`.
5. Dùng `try-except` để xử lý lỗi nhập liệu.

---

### **Kết quả Ngày 2**
Bạn biết tự động hóa, quản lý dữ liệu, viết code tái sử dụng và xử lý lỗi.

---

# **Tóm Tắt Khái Niệm Đã Bao Phủ**
## **Ngày 1:**
- `print()`, biến, `input()`, `if-else`, chuỗi, toán tử.

## **Ngày 2:**
- Vòng lặp, danh sách, hàm, tuple/dictionary/set, xử lý lỗi.