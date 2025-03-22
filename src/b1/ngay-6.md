# Ngày 6: Lập trình hướng đối tượng (OOP) trong Python

Tôi sẽ thiết kế một khóa học 5 giờ về Lập trình hướng đối tượng (OOP) trong Python, chia thành các phần rõ ràng, mỗi phần khoảng 1 giờ. Nội dung bao gồm lý thuyết cơ bản, ví dụ thực tế, và bài tập để bạn thực hành. Mục tiêu là bạn sẽ nắm được các khái niệm cốt lõi của OOP (**class, object, inheritance, encapsulation, polymorphism**) và áp dụng chúng trong Python.

## Giờ 1: Giới thiệu và Class/Object cơ bản

### Mục tiêu: 
Hiểu class, object là gì và cách tạo chúng trong Python.

### Lý thuyết (20 phút):
- OOP là gì? Lập trình dựa trên "đối tượng" (object) mô phỏng thế giới thực.
- **Class**: Bản thiết kế (blueprint) của đối tượng.
- **Object**: Thực thể cụ thể được tạo từ class.
- Cú pháp: `class TenClass:`.

### Ví dụ thực hành (30 phút):

```python
# Định nghĩa class
class Dog:
    def __init__(self, name, age):  # Hàm khởi tạo
        self.name = name  # Thuộc tính (attribute)
        self.age = age

    def bark(self):  # Phương thức (method)
        print(f"{self.name} says: Woof!")

# Tạo object
dog1 = Dog("Buddy", 3)
dog2 = Dog("Max", 5)

# Truy cập thuộc tính và phương thức
print(dog1.name, dog1.age)  # Buddy 3
dog1.bark()  # Buddy says: Woof!
dog2.bark()  # Max says: Woof!
```

### Bài tập (10 phút):
Tạo class `Car` với thuộc tính `brand`, `speed` và phương thức `honk()` in ra "Beep beep!".

---

## Giờ 2: Encapsulation (Đóng gói)

### Mục tiêu:
Học cách bảo vệ dữ liệu và ẩn chi tiết triển khai.

### Lý thuyết (20 phút):
- **Encapsulation**: Giới hạn truy cập trực tiếp vào dữ liệu, dùng thuộc tính private/public.
- Trong Python: Dùng `_` (protected) hoặc `__` (private) trước tên thuộc tính.

### Ví dụ thực hành (30 phút):

```python
class Person:
    def __init__(self, name, age):
        self.name = name  # Public
        self.__age = age  # Private

    def get_age(self):  # Getter
        return self.__age

    def set_age(self, age):  # Setter
        if age > 0:
            self.__age = age
        else:
            print("Age must be positive!")

# Tạo object
person = Person("Alice", 25)
print(person.name)  # Alice
print(person.get_age())  # 25
person.set_age(30)
print(person.get_age())  # 30
person.set_age(-5)  # Age must be positive!
```

### Bài tập (10 phút):
Tạo class `BankAccount` với thuộc tính private `__balance`, thêm phương thức `deposit()` và `withdraw()` để thay đổi số dư (kiểm tra số dư không âm).

---

## Giờ 3: Inheritance (Kế thừa)

### Mục tiêu:
Hiểu cách tái sử dụng code qua kế thừa.

### Lý thuyết (20 phút):
- **Inheritance**: Class con (**subclass**) thừa hưởng thuộc tính/phương thức từ class cha (**superclass**).
- Cú pháp: `class SubClass(SuperClass):`

### Ví dụ thực hành (30 phút):

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def eat(self):
        print(f"{self.name} is eating.")

class Cat(Animal):  # Kế thừa từ Animal
    def meow(self):
        print(f"{self.name} says: Meow!")

class Dog(Animal):
    def bark(self):
        print(f"{self.name} says: Woof!")

# Sử dụng
cat = Cat("Luna")
dog = Dog("Rex")
cat.eat()  # Luna is eating.
cat.meow()  # Luna says: Meow!
dog.eat()  # Rex is eating.
dog.bark()  # Rex says: Woof!
```

### Bài tập (10 phút):
Tạo class `Vehicle` với thuộc tính `speed`, sau đó tạo subclass `Bicycle` và `Motorcycle` với phương thức riêng (e.g., `ring_bell()`, `rev_engine()`).

---

## Giờ 4: Polymorphism (Đa hình)

### Mục tiêu:
Học cách các đối tượng khác nhau phản hồi cùng một phương thức theo cách riêng.

### Lý thuyết (20 phút):
- **Polymorphism**: Nhiều class có thể dùng chung tên phương thức, nhưng hành vi khác nhau.

### Ví dụ thực hành (30 phút):

```python
class Animal:
    def speak(self):
        pass  # Phương thức trống, để subclass định nghĩa

class Cat(Animal):
    def speak(self):
        return "Meow!"

class Dog(Animal):
    def speak(self):
        return "Woof!"

# Đa hình
animals = [Cat(), Dog()]
for animal in animals:
    print(animal.speak())  # Meow! rồi Woof!
```

### Bài tập (10 phút):
Tạo class `Shape` với phương thức `area()`, sau đó tạo subclass `Circle` (diện tích: πr²) và `Rectangle` (diện tích: dài × rộng). Gọi `area()` cho từng hình.

---

## Giờ 5: Tổng hợp và Dự án nhỏ

### Mục tiêu:
Kết hợp tất cả khái niệm vào một ví dụ thực tế.

### Dự án: Quản lý thư viện (40 phút)

```python
class Book:
    def __init__(self, title, author):
        self.__title = title
        self.__author = author
        self.__is_borrowed = False

    def get_title(self):
        return self.__title

    def borrow(self):
        if not self.__is_borrowed:
            self.__is_borrowed = True
            print(f"{self.__title} has been borrowed.")
        else:
            print(f"{self.__title} is already borrowed.")

class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)
        print(f"Added {book.get_title()} to library.")

# Sử dụng
book1 = Book("Python 101", "John Doe")
library = Library()
library.add_book(book1)
book1.borrow()
```

---

## Lịch học gợi ý (5 giờ)
- **Giờ 1**: Class/Object cơ bản.
- **Giờ 2**: Encapsulation.
- **Giờ 3**: Inheritance.
- **Giờ 4**: Polymorphism.
- **Giờ 5**: Dự án tổng hợp.


Trong 5 giờ, bạn có thể học về các khái niệm chính của OOP trong Python:
  
1. **Đối tượng (Object)**  
2. **Lớp (Class)**  
3. **Phương thức & Constructor (`__init__`)**  
4. **Kế thừa (Inheritance)**  

---

## 🏆 **1. Đối tượng và Lớp (Object & Class)**  
**Lớp (Class)** là một bản thiết kế (blueprint) để tạo ra **đối tượng (Object)**.  

### 🔹 **Ví dụ về Class và Object**  
```python
class Nguoi:
    def __init__(self, ten, tuoi):
        self.ten = ten
        self.tuoi = tuoi

# Tạo đối tượng từ lớp
nguoi_1 = Nguoi("An", 25)
nguoi_2 = Nguoi("Bình", 30)

# Truy xuất dữ liệu
print(nguoi_1.ten, "-", nguoi_1.tuoi)  # An - 25
print(nguoi_2.ten, "-", nguoi_2.tuoi)  # Bình - 30
```

📌 **Ghi nhớ:**  
- `class` dùng để định nghĩa một lớp.  
- `self` đại diện cho đối tượng của lớp.  

---

## 🔥 **2. Phương thức (Method) & Constructor (`__init__`)**  
**Phương thức** là các hàm được định nghĩa bên trong lớp để xử lý dữ liệu.  
**Constructor (`__init__`)** là phương thức đặc biệt được gọi khi tạo đối tượng.  

### 🔹 **Ví dụ về phương thức**
```python
class SinhVien:
    def __init__(self, ten, diem):
        self.ten = ten
        self.diem = diem

    def hien_thi(self):
        print(f"Sinh viên {self.ten} có điểm {self.diem}")

# Tạo đối tượng
sv = SinhVien("Linh", 9)

# Gọi phương thức
sv.hien_thi()  # Sinh viên Linh có điểm 9
```

📌 **Ghi nhớ:**  
- `__init__()` chạy tự động khi tạo đối tượng.  
- Phương thức truy cập dữ liệu bằng `self`.  

---

## 🏗 **3. Kế thừa (Inheritance)**  
Kế thừa giúp một lớp con **(child class)** sử dụng lại các thuộc tính và phương thức của lớp cha **(parent class)**.  

### 🔹 **Ví dụ về kế thừa**
```python
class Nguoi:
    def __init__(self, ten, tuoi):
        self.ten = ten
        self.tuoi = tuoi

    def hien_thi(self):
        print(f"Tôi là {self.ten}, {self.tuoi} tuổi")

# Lớp SinhVien kế thừa từ Nguoi
class SinhVien(Nguoi):
    def __init__(self, ten, tuoi, diem):
        super().__init__(ten, tuoi)  # Gọi constructor của lớp cha
        self.diem = diem

    def hien_thi(self):
        super().hien_thi()
        print(f"Điểm trung bình: {self.diem}")

# Tạo đối tượng SinhVien
sv = SinhVien("Hoàng", 20, 8.5)
sv.hien_thi()
```

📌 **Ghi nhớ:**  
- `super().__init__()` gọi constructor của lớp cha.  
- Lớp con có thể ghi đè phương thức (`hien_thi()`).  

---

## 🎯 **Bài tập thực hành OOP**  
### 🔥 **Bài 1: Tạo lớp `HinhTron`**  
Viết lớp `HinhTron` có:  
- **Thuộc tính:** `ban_kinh`  
- **Phương thức:** `chu_vi()` và `dien_tich()`  

👉 **Gợi ý:** Dùng công thức:  
- Chu vi = `2 * 3.14 * r`  
- Diện tích = `3.14 * r * r`  

---

### 🔥 **Bài 2: Tạo lớp `DongVat` và lớp con `Meo`**  
- Lớp `DongVat`: có phương thức `keu()` in ra `"Động vật kêu"`  
- Lớp `Meo` kế thừa `DongVat` và ghi đè `keu()` để in `"Meo meo"`  

👉 **Gợi ý:** Dùng `super().keu()` nếu muốn gọi phương thức lớp cha.  

---

### 🔥 **Constructor (`__init__`) trong Python**  

#### ✅ **1. Constructor là gì?**  
Constructor là một **phương thức đặc biệt** trong lớp Python, được gọi **tự động** khi một đối tượng mới được tạo.  
- Trong Python, constructor được định nghĩa bằng **`__init__()`**.  
- Nó dùng để **khởi tạo giá trị ban đầu** cho các thuộc tính của đối tượng.  

---

#### ✅ **2. Cách sử dụng `__init__()`**
Cú pháp của constructor:  
```python
class TenLop:
    def __init__(self, tham_so1, tham_so2, ...):
        self.thuoc_tinh1 = tham_so1
        self.thuoc_tinh2 = tham_so2
```

📌 **Ví dụ cơ bản:**  
```python
class Nguoi:
    def __init__(self, ten, tuoi):
        self.ten = ten  # Gán giá trị tham số cho thuộc tính
        self.tuoi = tuoi

# Tạo đối tượng
nguoi1 = Nguoi("An", 25)

# In ra thuộc tính của đối tượng
print(nguoi1.ten)  # An
print(nguoi1.tuoi)  # 25
```

🚀 **Khi tạo `nguoi1 = Nguoi("An", 25)`, Python tự động gọi `__init__()`**  
→ `self.ten = "An"` và `self.tuoi = 25`  

---

#### ✅ **3. Constructor mặc định (Không có tham số)**
Nếu không cần tham số, constructor có thể viết như sau:  
```python
class DongVat:
    def __init__(self):
        print("Một con vật mới đã được tạo!")

# Tạo đối tượng
dv = DongVat()  # Output: Một con vật mới đã được tạo!
```

📌 **Ghi nhớ:** Nếu constructor không có tham số, nó vẫn được gọi tự động khi tạo đối tượng.  

---

#### ✅ **4. Constructor với giá trị mặc định**
Có thể đặt giá trị mặc định cho tham số để tránh lỗi khi không truyền giá trị.  
```python
class HocSinh:
    def __init__(self, ten="Không tên", lop="12A1"):
        self.ten = ten
        self.lop = lop

# Tạo đối tượng không truyền tham số
hs1 = HocSinh()
print(hs1.ten, "-", hs1.lop)  # Không tên - 12A1

# Tạo đối tượng có truyền tham số
hs2 = HocSinh("Minh", "12B3")
print(hs2.ten, "-", hs2.lop)  # Minh - 12B3
```

📌 **Lợi ích:** Nếu người dùng không truyền tham số, chương trình vẫn chạy bình thường.  

---

#### ✅ **5. Constructor trong kế thừa (`super()`)**
Khi một lớp kế thừa từ lớp khác, ta có thể dùng `super().__init__()` để gọi constructor của lớp cha.  

📌 **Ví dụ:**  
```python
class Nguoi:
    def __init__(self, ten, tuoi):
        self.ten = ten
        self.tuoi = tuoi

# Lớp SinhVien kế thừa từ Nguoi
class SinhVien(Nguoi):
    def __init__(self, ten, tuoi, diem):
        super().__init__(ten, tuoi)  # Gọi constructor của lớp cha
        self.diem = diem

# Tạo đối tượng
sv = SinhVien("Hoa", 20, 8.5)

print(sv.ten)  # Hoa
print(sv.tuoi)  # 20
print(sv.diem)  # 8.5
```

🚀 **`super().__init__(ten, tuoi)`** giúp SinhVien kế thừa thuộc tính từ lớp `Nguoi`.  

---

#### ✅ **6. Constructor có thể làm gì?**
Constructor không chỉ dùng để khởi tạo biến mà còn có thể:  
✅ Kiểm tra dữ liệu đầu vào  
✅ Mở file, kết nối cơ sở dữ liệu  
✅ Thiết lập trạng thái ban đầu của đối tượng  

📌 **Ví dụ kiểm tra dữ liệu hợp lệ:**  
```python
class NhanVien:
    def __init__(self, ten, luong):
        if luong < 0:
            raise ValueError("Lương không thể âm!")
        self.ten = ten
        self.luong = luong

# Tạo đối tượng hợp lệ
nv = NhanVien("Nam", 5000)
print(nv.ten, "-", nv.luong)  # Nam - 5000

# Tạo đối tượng với lương âm (sẽ báo lỗi)
# nv2 = NhanVien("Linh", -3000)  # ❌ ValueError: Lương không thể âm!
```

---

## 🎯 **Tóm tắt**
| **Tính năng**  | **Constructor (`__init__()`)** |
|---------------|---------------------------|
| **Tự động gọi** | Khi tạo đối tượng từ lớp |
| **Khởi tạo giá trị** | Gán giá trị ban đầu cho thuộc tính |
| **Có thể có tham số** | Dùng để truyền dữ liệu vào đối tượng |
| **Có thể có giá trị mặc định** | Tránh lỗi khi không truyền tham số |
| **Dùng trong kế thừa** | `super().__init__()` để gọi constructor lớp cha |

---

### 🔥 **Ví dụ thực tế về Constructor (`__init__()`) trong Python**  

Dưới đây là một số tình huống thực tế về cách sử dụng constructor (`__init__()`) trong Python.  

---

### ✅ **1. Tạo hệ thống quản lý sinh viên**  
📌 **Yêu cầu:**  
- Lớp `SinhVien` có các thuộc tính: `ho_ten`, `tuoi`, `diem`.  
- Khi tạo sinh viên mới, nếu `diem < 0` hoặc `diem > 10`, sẽ báo lỗi.  

### 📝 **Cách làm:**
```python
class SinhVien:
    def __init__(self, ho_ten, tuoi, diem):
        if diem < 0 or diem > 10:
            raise ValueError("Điểm phải từ 0 đến 10!")
        self.ho_ten = ho_ten
        self.tuoi = tuoi
        self.diem = diem

    def hien_thi(self):
        print(f"Sinh viên: {self.ho_ten}, Tuổi: {self.tuoi}, Điểm: {self.diem}")

# Tạo sinh viên hợp lệ
sv1 = SinhVien("Nguyễn Văn A", 20, 8.5)
sv1.hien_thi()  # Output: Sinh viên: Nguyễn Văn A, Tuổi: 20, Điểm: 8.5

# Tạo sinh viên có điểm không hợp lệ (sẽ báo lỗi)
# sv2 = SinhVien("Trần Thị B", 22, 12)  # ❌ ValueError: Điểm phải từ 0 đến 10!
```
🚀 **Lợi ích:** Giúp kiểm tra dữ liệu hợp lệ ngay từ khi khởi tạo đối tượng.  

---

### ✅ **2. Xây dựng hệ thống tài khoản ngân hàng**  
📌 **Yêu cầu:**  
- Lớp `TaiKhoanNganHang` có:  
  - `so_tai_khoan`  
  - `chu_tai_khoan`  
  - `so_du` (ban đầu mặc định là 0)  
- Tự động hiển thị thông tin khi tạo tài khoản.  

### 📝 **Cách làm:**
```python
class TaiKhoanNganHang:
    def __init__(self, so_tai_khoan, chu_tai_khoan, so_du=0):
        self.so_tai_khoan = so_tai_khoan
        self.chu_tai_khoan = chu_tai_khoan
        self.so_du = so_du

        print(f"Tài khoản {self.so_tai_khoan} của {self.chu_tai_khoan} đã được tạo với số dư: {self.so_du} VNĐ")

# Tạo tài khoản mới
tk1 = TaiKhoanNganHang("123456789", "Nguyễn Văn C", 500000)
tk2 = TaiKhoanNganHang("987654321", "Lê Thị D")  # Số dư mặc định 0
```
🚀 **Lợi ích:**  
- Mặc định số dư = 0 nếu không nhập.  
- Hiển thị thông báo ngay khi tạo tài khoản.  

---

### ✅ **3. Quản lý sách trong thư viện**  
📌 **Yêu cầu:**  
- Lớp `Sach` có các thuộc tính: `tieu_de`, `tac_gia`, `nam_xuat_ban`.  
- Nếu năm xuất bản lớn hơn năm hiện tại, báo lỗi.  

### 📝 **Cách làm:**
```python
from datetime import datetime

class Sach:
    def __init__(self, tieu_de, tac_gia, nam_xuat_ban):
        nam_hien_tai = datetime.now().year
        if nam_xuat_ban > nam_hien_tai:
            raise ValueError("Năm xuất bản không hợp lệ!")
        self.tieu_de = tieu_de
        self.tac_gia = tac_gia
        self.nam_xuat_ban = nam_xuat_ban

    def hien_thi(self):
        print(f"Sách: {self.tieu_de}, Tác giả: {self.tac_gia}, Năm XB: {self.nam_xuat_ban}")

# Tạo sách hợp lệ
sach1 = Sach("Doraemon", "Fujiko F. Fujio", 1990)
sach1.hien_thi()  # Output: Sách: Doraemon, Tác giả: Fujiko F. Fujio, Năm XB: 1990

# Tạo sách với năm xuất bản không hợp lệ (sẽ báo lỗi)
# sach2 = Sach("Tương lai AI", "John Doe", 2030)  # ❌ ValueError: Năm xuất bản không hợp lệ!
```
🚀 **Lợi ích:**  
- Kiểm tra hợp lệ **ngay khi tạo đối tượng**.  

---

### ✅ **4. Quản lý nhân viên công ty**  
📌 **Yêu cầu:**  
- Lớp `NhanVien` có các thuộc tính: `ho_ten`, `luong_co_ban`, `thuong`.  
- Lương thực nhận = `luong_co_ban + thuong`.  
- Nếu `luong_co_ban` nhỏ hơn 0, báo lỗi.  

### 📝 **Cách làm:**
```python
class NhanVien:
    def __init__(self, ho_ten, luong_co_ban, thuong=0):
        if luong_co_ban < 0:
            raise ValueError("Lương cơ bản không thể âm!")
        self.ho_ten = ho_ten
        self.luong_co_ban = luong_co_ban
        self.thuong = thuong
        self.luong_thuc_nhan = self.luong_co_ban + self.thuong

    def hien_thi(self):
        print(f"Nhân viên: {self.ho_ten}, Lương thực nhận: {self.luong_thuc_nhan} VNĐ")

# Tạo nhân viên hợp lệ
nv1 = NhanVien("Trần Văn E", 7000000, 1000000)
nv1.hien_thi()  # Output: Nhân viên: Trần Văn E, Lương thực nhận: 8000000 VNĐ

# Tạo nhân viên với lương âm (sẽ báo lỗi)
# nv2 = NhanVien("Lê Văn F", -5000000)  # ❌ ValueError: Lương cơ bản không thể âm!
```
🚀 **Lợi ích:**  
- Kiểm tra lỗi **trước khi thêm nhân viên**.  
- Tự động tính lương thực nhận.  

---

## 🎯 **Tóm tắt**
| **Ví dụ** | **Constructor làm gì?** |
|------------|---------------------|
| **Quản lý sinh viên** | Kiểm tra điểm hợp lệ (0-10) |
| **Tài khoản ngân hàng** | Tự động tạo tài khoản & đặt số dư mặc định |
| **Quản lý sách** | Kiểm tra năm xuất bản không vượt quá năm hiện tại |
| **Quản lý nhân viên** | Kiểm tra lương hợp lệ & tính lương thực nhận |

---

### 🔥 **Ví dụ về Ví Ethereum (ETH) sử dụng Constructor (`__init__()`) trong Python**  

📌 **Yêu cầu:**  
1. Tạo lớp `EthereumWallet` để quản lý ví ETH.  
2. Khi tạo ví mới, tự động:  
   - Tạo địa chỉ ví (giả lập bằng chuỗi hex).  
   - Thiết lập số dư mặc định là 0 ETH.  
3. Cung cấp các phương thức để:  
   - Kiểm tra số dư.  
   - Nạp ETH vào ví.  
   - Gửi ETH sang ví khác (phải kiểm tra số dư hợp lệ).  

---

### 📝 **Cách làm:**
```python
import random
import string

class EthereumWallet:
    def __init__(self, owner_name):
        self.owner_name = owner_name
        self.address = self.generate_address()
        self.balance = 0.0  # Số dư mặc định là 0 ETH

    def generate_address(self):
        """Tạo địa chỉ ví ETH ngẫu nhiên (giả lập)"""
        return "0x" + ''.join(random.choices(string.hexdigits, k=40)).lower()

    def check_balance(self):
        """Kiểm tra số dư ví"""
        print(f"Ví của {self.owner_name} ({self.address}) có số dư: {self.balance} ETH")

    def deposit(self, amount):
        """Nạp ETH vào ví"""
        if amount > 0:
            self.balance += amount
            print(f"Nạp {amount} ETH thành công! Số dư mới: {self.balance} ETH")
        else:
            print("❌ Số tiền nạp phải lớn hơn 0!")

    def send_eth(self, recipient_wallet, amount):
        """Gửi ETH sang ví khác"""
        if amount > self.balance:
            print("❌ Giao dịch thất bại: Số dư không đủ!")
        elif amount <= 0:
            print("❌ Số tiền gửi phải lớn hơn 0!")
        else:
            self.balance -= amount
            recipient_wallet.balance += amount
            print(f"✅ Gửi {amount} ETH thành công đến {recipient_wallet.address}")
            print(f"Số dư còn lại trong ví: {self.balance} ETH")

# Tạo 2 ví ETH
alice_wallet = EthereumWallet("Alice")
bob_wallet = EthereumWallet("Bob")

# Kiểm tra số dư ban đầu
alice_wallet.check_balance()
bob_wallet.check_balance()

# Alice nạp 10 ETH vào ví
alice_wallet.deposit(10)

# Alice gửi 3 ETH cho Bob
alice_wallet.send_eth(bob_wallet, 3)

# Kiểm tra số dư sau giao dịch
alice_wallet.check_balance()
bob_wallet.check_balance()
```

---

### ✅ **Giải thích mã nguồn:**
1. **`__init__()`**  
   - Khi tạo một ví mới, nó sẽ **tự động** tạo địa chỉ ETH ngẫu nhiên và thiết lập số dư về `0.0`.  
2. **Phương thức `generate_address()`**  
   - Giả lập một địa chỉ ETH bằng cách tạo một chuỗi hex ngẫu nhiên dài 40 ký tự.  
3. **Phương thức `check_balance()`**  
   - Hiển thị số dư hiện tại của ví.  
4. **Phương thức `deposit(amount)`**  
   - Nạp ETH vào ví (chỉ chấp nhận số dương).  
5. **Phương thức `send_eth(recipient_wallet, amount)`**  
   - Kiểm tra số dư trước khi gửi ETH đến ví khác.  
   - Nếu số dư hợp lệ, tiến hành giao dịch và cập nhật số dư của cả hai ví.  

---

### 🎯 **Kết quả mong đợi:**
```
Ví của Alice (0x4b9f0d3a19f72e85a4...) có số dư: 0.0 ETH
Ví của Bob (0x2e8a1c4d99b62f1a7b...) có số dư: 0.0 ETH

Nạp 10 ETH thành công! Số dư mới: 10.0 ETH

✅ Gửi 3 ETH thành công đến 0x2e8a1c4d99b62f1a7b...
Số dư còn lại trong ví: 7.0 ETH

Ví của Alice (0x4b9f0d3a19f72e85a4...) có số dư: 7.0 ETH
Ví của Bob (0x2e8a1c4d99b62f1a7b...) có số dư: 3.0 ETH
```

---

### 🚀 **Mở rộng**:
- **Thêm xác thực giao dịch bằng Private Key**  
- **Kết nối API để gửi ETH thực tế qua blockchain**  
- **Ghi lịch sử giao dịch vào file hoặc database**  

### 🔥 **Mở rộng ví Ethereum: Xác thực giao dịch & Lịch sử giao dịch**  
Chúng ta sẽ thêm hai tính năng quan trọng:  
✅ **Xác thực giao dịch bằng Private Key** (Giả lập ký giao dịch)  
✅ **Lưu lịch sử giao dịch vào danh sách**  

---

## 🏗 **1. Mô tả nâng cấp**
1. **Mỗi ví sẽ có một Private Key** để xác thực giao dịch.  
2. **Giao dịch chỉ được thực hiện nếu có chữ ký hợp lệ**.  
3. **Lịch sử giao dịch được lưu lại** để tra cứu.  

---

## 📝 **Cập nhật mã nguồn**
```python
import random
import string
import hashlib

class EthereumWallet:
    def __init__(self, owner_name):
        self.owner_name = owner_name
        self.address = self.generate_address()
        self.private_key = self.generate_private_key()
        self.balance = 0.0
        self.transaction_history = []  # Lưu lịch sử giao dịch

    def generate_address(self):
        """Tạo địa chỉ ví ETH giả lập"""
        return "0x" + ''.join(random.choices(string.hexdigits, k=40)).lower()

    def generate_private_key(self):
        """Tạo Private Key ngẫu nhiên"""
        return ''.join(random.choices(string.hexdigits, k=64)).lower()

    def check_balance(self):
        """Kiểm tra số dư ví"""
        print(f"Ví {self.owner_name} ({self.address}) có số dư: {self.balance} ETH")

    def deposit(self, amount):
        """Nạp ETH vào ví"""
        if amount > 0:
            self.balance += amount
            self.transaction_history.append(f"Nạp {amount} ETH")
            print(f"✅ Nạp {amount} ETH thành công! Số dư mới: {self.balance} ETH")
        else:
            print("❌ Số tiền nạp phải lớn hơn 0!")

    def sign_transaction(self, recipient, amount):
        """Giả lập ký giao dịch bằng private key (hash SHA256)"""
        message = f"{self.address}->{recipient.address}:{amount}:{self.private_key}"
        return hashlib.sha256(message.encode()).hexdigest()

    def send_eth(self, recipient_wallet, amount, signature):
        """Gửi ETH với xác thực chữ ký"""
        if amount > self.balance:
            print("❌ Giao dịch thất bại: Số dư không đủ!")
        elif amount <= 0:
            print("❌ Số tiền gửi phải lớn hơn 0!")
        elif signature != self.sign_transaction(recipient_wallet, amount):
            print("❌ Giao dịch bị từ chối: Chữ ký không hợp lệ!")
        else:
            self.balance -= amount
            recipient_wallet.balance += amount
            self.transaction_history.append(f"Gửi {amount} ETH đến {recipient_wallet.address}")
            recipient_wallet.transaction_history.append(f"Nhận {amount} ETH từ {self.address}")
            print(f"✅ Giao dịch thành công! Gửi {amount} ETH đến {recipient_wallet.address}")

    def show_transaction_history(self):
        """Hiển thị lịch sử giao dịch"""
        print(f"\n📜 Lịch sử giao dịch của {self.owner_name}:")
        for tx in self.transaction_history:
            print(f"- {tx}")

# Tạo 2 ví ETH
alice_wallet = EthereumWallet("Alice")
bob_wallet = EthereumWallet("Bob")

# Kiểm tra số dư ban đầu
alice_wallet.check_balance()
bob_wallet.check_balance()

# Alice nạp 10 ETH vào ví
alice_wallet.deposit(10)

# Alice tạo chữ ký và gửi 3 ETH cho Bob
signature = alice_wallet.sign_transaction(bob_wallet, 3)
alice_wallet.send_eth(bob_wallet, 3, signature)

# Kiểm tra số dư sau giao dịch
alice_wallet.check_balance()
bob_wallet.check_balance()

# Xem lịch sử giao dịch
alice_wallet.show_transaction_history()
bob_wallet.show_transaction_history()
```

---

## 🎯 **Cách hoạt động của nâng cấp**
1. **Tạo ví**: Mỗi ví có một **Private Key** và địa chỉ ETH.  
2. **Nạp ETH**: ETH có thể được nạp vào ví, lưu vào lịch sử giao dịch.  
3. **Xác thực giao dịch**:  
   - Khi gửi ETH, hệ thống tạo một chữ ký **dựa trên Private Key**.  
   - Nếu chữ ký **không khớp**, giao dịch bị từ chối.  
4. **Lưu lịch sử giao dịch**: Mọi giao dịch được ghi lại để có thể kiểm tra sau.  

---

## 🏆 **Kết quả mong đợi**
```
Ví Alice (0x4b9f0d3a19f72e85a4...) có số dư: 0.0 ETH
Ví Bob (0x2e8a1c4d99b62f1a7b...) có số dư: 0.0 ETH

✅ Nạp 10 ETH thành công! Số dư mới: 10.0 ETH
✅ Giao dịch thành công! Gửi 3 ETH đến 0x2e8a1c4d99b62f1a7b...

Ví Alice (0x4b9f0d3a19f72e85a4...) có số dư: 7.0 ETH
Ví Bob (0x2e8a1c4d99b62f1a7b...) có số dư: 3.0 ETH

📜 Lịch sử giao dịch của Alice:
- Nạp 10 ETH
- Gửi 3 ETH đến 0x2e8a1c4d99b62f1a7b...

📜 Lịch sử giao dịch của Bob:
- Nhận 3 ETH từ 0x4b9f0d3a19f72e85a4...
```

---

## 🚀 **Mở rộng thêm**
- ✅ **Thêm phí giao dịch** (giữ lại một phần ETH khi gửi).  
- ✅ **Kết nối API Blockchain (Infura, Alchemy) để giao dịch thực tế**.  
- ✅ **Tích hợp mã QR để quét và gửi ETH nhanh hơn**.  

### 🌐 **Kết nối API Blockchain để gửi ETH thực tế**  
Chúng ta sẽ sử dụng **Web3.py** để kết nối với mạng **Ethereum** thông qua **Infura** hoặc **Alchemy**, giúp gửi ETH thực tế.

---

## ✅ **1. Chuẩn bị trước khi lập trình**  
📌 **Cài đặt thư viện Web3.py**:  
```bash
pip install web3
```

📌 **Đăng ký tài khoản trên Infura hoặc Alchemy**:  
- **Infura**: [https://infura.io](https://infura.io)  
- **Alchemy**: [https://www.alchemy.com](https://www.alchemy.com)  
- Sau khi đăng ký, lấy **API URL** (HTTP Endpoint) của mạng **Ethereum (Mainnet hoặc Testnet như Goerli, Sepolia).**  

📌 **Tạo ví Ethereum trên Metamask & lấy thông tin quan trọng**:  
- **Private Key** của ví gửi ETH.  
- **Địa chỉ ví nhận ETH**.  

⚠️ **Lưu ý bảo mật**: Không chia sẻ **Private Key** với bất kỳ ai!  

---

## 🚀 **2. Code gửi ETH thực tế với Web3.py**  

### **📌 Gửi ETH từ một ví đến một ví khác**
```python
from web3 import Web3

# Thay thế bằng API Endpoint từ Infura hoặc Alchemy
INFURA_URL = "https://sepolia.infura.io/v3/YOUR_INFURA_PROJECT_ID"

# Kết nối với mạng Ethereum
web3 = Web3(Web3.HTTPProvider(INFURA_URL))

# Kiểm tra kết nối thành công
if web3.is_connected():
    print("✅ Đã kết nối với Ethereum Blockchain!")
else:
    print("❌ Kết nối thất bại!")

# Thông tin giao dịch
SENDER_ADDRESS = "0xYOUR_SENDER_WALLET_ADDRESS"  # Ví gửi
PRIVATE_KEY = "YOUR_PRIVATE_KEY"  # ⚠️ Không chia sẻ với ai!
RECEIVER_ADDRESS = "0xYOUR_RECEIVER_WALLET_ADDRESS"  # Ví nhận
AMOUNT_ETH = 0.01  # Số ETH muốn gửi

# Lấy nonce của giao dịch (số lượng giao dịch đã gửi từ ví này)
nonce = web3.eth.get_transaction_count(SENDER_ADDRESS)

# Tạo giao dịch
tx = {
    'nonce': nonce,
    'to': RECEIVER_ADDRESS,
    'value': web3.to_wei(AMOUNT_ETH, 'ether'),  # Chuyển ETH thành Wei (đơn vị nhỏ nhất)
    'gas': 21000,  # Gas limit tiêu chuẩn cho giao dịch ETH
    'gasPrice': web3.to_wei(20, 'gwei'),  # Phí gas (Gwei)
    'chainId': 11155111,  # ID mạng Sepolia Testnet (Mainnet là 1)
}

# Ký giao dịch bằng Private Key
signed_tx = web3.eth.account.sign_transaction(tx, PRIVATE_KEY)

# Gửi giao dịch lên blockchain
tx_hash = web3.eth.send_raw_transaction(signed_tx.rawTransaction)

# Lấy ID giao dịch (Transaction Hash)
print(f"✅ Giao dịch đang xử lý: {web3.to_hex(tx_hash)}")

# Kiểm tra trạng thái giao dịch
receipt = web3.eth.wait_for_transaction_receipt(tx_hash)
if receipt.status == 1:
    print("✅ Giao dịch thành công!")
else:
    print("❌ Giao dịch thất bại!")
```

---

## 🎯 **Giải thích mã nguồn**
1. **Kết nối với Ethereum bằng Infura**  
   - Sử dụng `Web3.HTTPProvider(INFURA_URL)` để kết nối với mạng blockchain.  
2. **Tạo & ký giao dịch**  
   - Giao dịch chứa `to` (địa chỉ nhận), `value` (số ETH), `gas` (phí).  
   - Sử dụng `web3.eth.account.sign_transaction()` để ký bằng **Private Key**.  
3. **Gửi giao dịch lên blockchain**  
   - `web3.eth.send_raw_transaction()` để gửi ETH.  
   - Chờ xác nhận bằng `wait_for_transaction_receipt()`.  

---

## 🔬 **Kiểm tra giao dịch trên Blockchain**
Sau khi gửi, lấy **Transaction Hash** và kiểm tra trên Etherscan:  
🔗 **Ethereum Mainnet**: [https://etherscan.io/](https://etherscan.io/)  
🔗 **Sepolia Testnet**: [https://sepolia.etherscan.io/](https://sepolia.etherscan.io/)  

Dán **Transaction Hash** vào ô tìm kiếm để xem trạng thái giao dịch.

---

## ⚠️ **Lưu ý quan trọng**
- **Không bao giờ chia sẻ Private Key**.  
- Nếu test, hãy **dùng ví Testnet** (Sepolia, Goerli) thay vì Mainnet.  
- Phí gas có thể thay đổi, kiểm tra trên [Ethereum Gas Tracker](https://etherscan.io/gastracker).  

---

## 🚀 **Mở rộng thêm**
- ✅ **Tạo Smart Contract để gửi ETH tự động**.  
- ✅ **Tích hợp Metamask để gửi ETH từ trình duyệt**.  
- ✅ **Xây dựng giao diện web với Flask/Django**.


