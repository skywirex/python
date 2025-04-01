# Ngày 3: Lập trình đơn giản

### 1. **Hoán đổi hai biến**
```python
a = 5
b = 10

# Hoán đổi
a, b = b, a

print("Sau khi hoán đổi: a =", a, ", b =", b)
```

Bài toán hoán đổi hai biến thường được sử dụng trong lập trình để thay đổi giá trị của hai biến mà không làm mất dữ liệu. Dưới đây là một số tình huống thực tế mà hoán đổi hai biến có thể hữu ích:  

---
**Sắp xếp danh sách (Sorting Algorithms)**  
Khi triển khai các thuật toán sắp xếp như **Bubble Sort, Selection Sort, Quick Sort**, ta thường cần hoán đổi vị trí của các phần tử để đưa danh sách về thứ tự mong muốn.  
Ví dụ:  
```python
arr = [3, 1, 2]
arr[0], arr[1] = arr[1], arr[0]  # Hoán đổi 3 và 1
print(arr)  # Output: [1, 3, 2]
```
---

---

**Hoán đổi giá trị trong trò chơi (Game Development)**  
Khi lập trình game, ta có thể cần hoán đổi vị trí của hai đối tượng, ví dụ như hai quân cờ trong một bàn cờ.  

---

---

**Đổi chỗ hai biến trong thuật toán đệ quy**  
Một số bài toán đệ quy yêu cầu hoán đổi hai giá trị để xử lý thuận tiện hơn, như trong **đảo ngược mảng**.  
Ví dụ:  
```python
def reverse_list(lst, start, end):
    if start >= end:
        return
    lst[start], lst[end] = lst[end], lst[start]  # Hoán đổi
    reverse_list(lst, start + 1, end - 1)

arr = [1, 2, 3, 4, 5]
reverse_list(arr, 0, len(arr) - 1)
print(arr)  # Output: [5, 4, 3, 2, 1]
```
---

---

**Hoán đổi giá trị trong thuật toán tìm kiếm tối ưu**  
Khi thực hiện **tối ưu hóa bộ nhớ hoặc thuật toán tìm kiếm**, việc hoán đổi hai biến có thể giúp giảm chi phí tính toán.

Ví dụ: **Hoán đổi giá trị nhỏ nhất lên đầu danh sách**  
```python
arr = [4, 2, 9, 1]
min_index = arr.index(min(arr))
arr[0], arr[min_index] = arr[min_index], arr[0]  # Đưa giá trị nhỏ nhất về đầu danh sách
print(arr)  # Output: [1, 2, 9, 4]
```

---

---

**Đảo ngược giá trị hai biến trong xử lý dữ liệu**  
Ví dụ: **Đổi tiền tệ giữa hai loại ví trong ứng dụng tài chính**  
```python
wallet_a = 100  # Ví A có 100 đô
wallet_b = 50   # Ví B có 50 đô

wallet_a, wallet_b = wallet_b, wallet_a  # Đổi giá trị

print(wallet_a, wallet_b)  # Output: 50 100
```

---

### **Tóm lại**  
Hoán đổi hai biến không chỉ là một bài tập đơn giản mà còn rất hữu ích trong các thuật toán, xử lý dữ liệu, và lập trình game.

---

### 2. **Chuyển đổi độ C sang độ F**


**Chuyển đổi độ C sang độ F để làm gì?** 

Việc chuyển đổi từ **độ C (Celsius, °C)** sang **độ F (Fahrenheit, °F)** rất quan trọng trong nhiều lĩnh vực như **khoa học, y tế, hàng không, dự báo thời tiết và du lịch**.  

Công thức chuyển đổi:  

\\[ °F = (°C \times \frac{9}{5}) + 32 \\]

---

### **Ứng dụng thực tế của chuyển đổi nhiệt độ**  

🔹 **Dự báo thời tiết**  
- Ở Mỹ, Canada hoặc các nước sử dụng đơn vị Fahrenheit, khi đọc dự báo thời tiết của một quốc gia khác sử dụng độ C (ví dụ: Việt Nam, châu Âu), ta cần chuyển đổi giữa hai hệ đơn vị.  

🔹 **Y tế (đo thân nhiệt)**  
- Một số nhiệt kế sử dụng °C, trong khi ở Mỹ dùng °F. Ví dụ:  
  - 37°C = 98.6°F (nhiệt độ cơ thể bình thường).  
  - 40°C = 104°F (sốt cao, cần cấp cứu).  

🔹 **Hàng không và khoa học**  
- Trong ngành hàng không, các hệ thống đo lường thường cần chuyển đổi giữa °C và °F để đảm bảo tính đồng nhất trên toàn cầu.  

🔹 **Du lịch & nấu ăn**  
- Nếu bạn du lịch đến Mỹ và thấy công thức nấu ăn yêu cầu lò nướng ở 350°F, bạn có thể cần chuyển đổi sang °C để sử dụng lò của mình (~176°C).

```python
def c_to_f(celsius):
    return (celsius * 9/5) + 32

c = float(input("Nhập độ C: "))
print(f"{c}°C = {c_to_f(c)}°F")
```

---

### 3. **Tính tổng các chữ số của một số**

**Tính tổng các chữ số của một số để làm gì?**  

Việc tính tổng các chữ số của một số có nhiều ứng dụng trong **toán học, mã hóa, kiểm tra số đặc biệt** và **tính toán số học**. Một số ứng dụng cụ thể:  

🔹 **Kiểm tra số Harshad (Niven Number)**  
   - Một số chia hết cho tổng các chữ số của nó được gọi là **số Harshad**.  
   - Ví dụ: 18 → \( 1 + 8 = 9 \), mà \( 18 \div 9 = 2 \) (chia hết) → 18 là số Harshad.  

🔹 **Kiểm tra số may mắn (Lucky Number)**  
   - Một số có tổng chữ số bằng 7 hoặc 9 thường được coi là may mắn trong nhiều nền văn hóa.  

🔹 **Xác minh số trong kiểm tra tính hợp lệ**  
   - Một số hệ thống số serial hoặc mã vạch sử dụng tổng các chữ số như một phần kiểm tra lỗi (checksum).  

---

### **Cách tính tổng các chữ số của một số trong Python**  
Dưới đây là cách viết chương trình Python để tính tổng các chữ số của một số nguyên **dương hoặc âm**.  

#### **Cách 1: Chuyển số thành chuỗi rồi tính tổng**
```python
def sum_of_digits(n):
    return sum(int(digit) for digit in str(abs(n)))  # abs() để xử lý số âm

num = int(input("Nhập số nguyên: "))
print("Tổng các chữ số:", sum_of_digits(num))
```
📌 **Ví dụ chạy chương trình**  
```
Nhập số nguyên: 1234
Tổng các chữ số: 10
```
```
Nhập số nguyên: -567
Tổng các chữ số: 18
```

---

#### **Cách 2: Dùng vòng lặp (không chuyển sang chuỗi)**
```python
def sum_of_digits(n):
    n = abs(n)  # Bỏ dấu âm nếu có
    total = 0
    while n > 0:
        total += n % 10  # Lấy chữ số cuối cùng
        n //= 10  # Bỏ chữ số cuối cùng
    return total

num = int(input("Nhập số nguyên: "))
print("Tổng các chữ số:", sum_of_digits(num))
```

### 4. **Kiểm tra số nguyên tố**

### **Kiểm tra số nguyên tố để làm gì?**  

Số nguyên tố là một khái niệm quan trọng trong **toán học, mật mã học, khoa học máy tính** và **các thuật toán số học**. Một số ứng dụng thực tế của việc kiểm tra số nguyên tố:  

🔹 **Mật mã RSA (Bảo mật thông tin)**  
   - Hệ thống mã hóa **RSA** dựa trên hai số nguyên tố rất lớn để tạo khóa bảo mật.  

🔹 **Thuật toán phân tích số nguyên**  
   - Một số thuật toán như **Fermat’s Factorization** cần kiểm tra số nguyên tố để tìm ước số lớn nhất.  

🔹 **Tối ưu hóa thuật toán tìm số nguyên tố lớn**  
   - Trong các bài toán lớn như **Tìm số nguyên tố Mersenne**, kiểm tra số nguyên tố rất quan trọng.  

---

### **Cách kiểm tra số nguyên tố trong Python**  

#### **Cách 1: Dùng vòng lặp cơ bản**
```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, n):  # Duyệt từ 2 đến n-1
        if n % i == 0:
            return False
    return True

num = int(input("Nhập số nguyên: "))
print(f"{num} là số nguyên tố" if is_prime(num) else f"{num} không phải số nguyên tố")
```
📌 **Ví dụ chạy chương trình:**  
```
Nhập số nguyên: 7
7 là số nguyên tố
```
```
Nhập số nguyên: 10
10 không phải số nguyên tố
```

---

#### **Cách 2: Cải thiện hiệu suất (Chỉ kiểm tra đến √n)**
💡 **Tối ưu**: Một số \( n \) không phải số nguyên tố nếu nó có ước số nhỏ hơn hoặc bằng \( \sqrt{n} \).  

```python
import math

def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(math.sqrt(n)) + 1):  # Chỉ kiểm tra đến √n
        if n % i == 0:
            return False
    return True

num = int(input("Nhập số nguyên: "))
print(f"{num} là số nguyên tố" if is_prime(num) else f"{num} không phải số nguyên tố")
```
🚀 **Tối ưu hơn nhiều**, đặc biệt với số lớn!  

---

#### **Cách 3: Kiểm tra số nguyên tố nhanh hơn (Bỏ qua số chẵn, chỉ kiểm tra số lẻ)**
💡 **Tối ưu hơn nữa**:  
- Nếu \( n \) **chia hết cho 2 hoặc 3**, thì không cần kiểm tra nữa.  
- Kiểm tra các số có dạng **\( 6k ± 1 \)** giúp giảm số lần lặp.  

```python
import math

def is_prime(n):
    if n < 2:
        return False
    if n in (2, 3):
        return True
    if n % 2 == 0 or n % 3 == 0:
        return False
    for i in range(5, int(math.sqrt(n)) + 1, 6):  # Kiểm tra 6k ± 1
        if n % i == 0 or n % (i + 2) == 0:
            return False
    return True

num = int(input("Nhập số nguyên: "))
print(f"{num} là số nguyên tố" if is_prime(num) else f"{num} không phải số nguyên tố")
```

---

**Mở rộng bài toán**
- **Tìm tất cả số nguyên tố trong khoảng từ 1 đến N?**  
- **Sinh số nguyên tố ngẫu nhiên?**  
- **Tính tổng các số nguyên tố trong một danh sách?**  

---

### 5. **Tạo số ngẫu nhiên**

### **Tạo số ngẫu nhiên để làm gì?**  

Việc tạo số ngẫu nhiên rất quan trọng trong nhiều lĩnh vực như:  

🔹 **Bảo mật & Mật mã học** → Dùng trong mã OTP, tạo khóa bảo mật.  
🔹 **Trò chơi & Mô phỏng** → Dùng để tạo quái vật, bài ngẫu nhiên, mô phỏng vật lý.  
🔹 **Thuật toán & Machine Learning** → Khởi tạo dữ liệu ngẫu nhiên cho AI.  
🔹 **Thống kê & Khoa học dữ liệu** → Tạo mẫu thử để kiểm tra mô hình.  

---

### **Cách tạo số ngẫu nhiên trong Python**  

Python có thư viện `random` để tạo số ngẫu nhiên.  

#### **1️⃣ Tạo số nguyên ngẫu nhiên trong một khoảng**  
```python
import random

num = random.randint(1, 100)  # Số ngẫu nhiên từ 1 đến 100
print("Số ngẫu nhiên:", num)
```
📌 **Ví dụ Output:**  
```
Số ngẫu nhiên: 42
```

---

#### **2️⃣ Tạo số thực ngẫu nhiên giữa hai giá trị**
```python
num = random.uniform(1.5, 10.5)  # Số thực ngẫu nhiên từ 1.5 đến 10.5
print("Số thực ngẫu nhiên:", num)
```
📌 **Ví dụ Output:**  
```
Số thực ngẫu nhiên: 6.2783
```

---

#### **3️⃣ Tạo số ngẫu nhiên từ danh sách cho trước**
```python
choices = [10, 20, 30, 40, 50]
num = random.choice(choices)  # Lấy ngẫu nhiên một phần tử từ danh sách
print("Số ngẫu nhiên:", num)
```
📌 **Ví dụ Output:**  
```
Số ngẫu nhiên: 30
```

---

#### **4️⃣ Tạo danh sách số ngẫu nhiên**
```python
random_numbers = [random.randint(1, 100) for _ in range(5)]  # Danh sách 5 số ngẫu nhiên
print("Danh sách số ngẫu nhiên:", random_numbers)
```
📌 **Ví dụ Output:**  
```
Danh sách số ngẫu nhiên: [23, 76, 12, 89, 45]
```

---

#### **5️⃣ Xáo trộn danh sách ngẫu nhiên**
```python
numbers = [1, 2, 3, 4, 5]
random.shuffle(numbers)  # Xáo trộn danh sách
print("Danh sách sau khi xáo trộn:", numbers)
```
📌 **Ví dụ Output:**  
```
Danh sách sau khi xáo trộn: [3, 1, 5, 2, 4]
```

---

**Mở rộng bài toán**
- **Sinh mật khẩu ngẫu nhiên?** 🔐  
- **Sinh số nguyên tố ngẫu nhiên?**  
- **Sinh dữ liệu giả (Fake Data) để kiểm thử?**

### 6. **Loại bỏ phần tử trùng lặp trong danh sách**
```python
def remove_duplicates(lst):
    return list(set(lst))

numbers = [1, 2, 2, 3, 4, 4, 5]
print("Danh sách sau khi loại bỏ trùng lặp:", remove_duplicates(numbers))
```


Dưới đây là các bài tập lập trình đơn giản đã được bổ sung công dụng ứng dụng thực tế cho từng bài để bạn thấy được giá trị của chúng trong đời sống hoặc lập trình. Mỗi bài vẫn giữ nguyên tính đơn giản, phù hợp để học Python trong khoảng 4 giờ tổng cộng.

## 1. Hoán đổi hai biến
**Mô tả:** Nhập hai số từ người dùng và hoán đổi giá trị của chúng mà không dùng biến tạm.  
**Thời gian:** ~30 phút  
**Mã mẫu:**  
```python
a = float(input("Nhập số thứ nhất: "))
b = float(input("Nhập số thứ hai: "))
print(f"Trước khi hoán đổi: a = {a}, b = {b}")
a, b = b, a
print(f"Sau khi hoán đổi: a = {a}, b = {b}")
```
**Công dụng thực tế:**  
- Trong thuật toán sắp xếp (như Bubble Sort), hoán đổi giá trị là thao tác cơ bản để sắp xếp danh sách (ví dụ: sắp xếp điểm số học sinh từ thấp đến cao).  
- Ứng dụng trong xử lý dữ liệu khi cần đổi chỗ hai giá trị trong bộ nhớ mà không tốn thêm không gian.

## 2. Chuyển đổi độ C sang độ F
**Mô tả:** Nhập nhiệt độ (°C) và chuyển đổi sang độ F bằng công thức: °F = °C * 9/5 + 32.  
**Thời gian:** ~30 phút  
**Mã mẫu:**  
```python
celsius = float(input("Nhập nhiệt độ (°C): "))
fahrenheit = celsius * 9/5 + 32
print(f"{celsius}°C tương đương {fahrenheit}°F")
```
**Công dụng thực tế:**  
- Dùng trong ứng dụng thời tiết để chuyển đổi nhiệt độ giữa các đơn vị cho người dùng ở các quốc gia khác nhau (Mỹ dùng °F, Việt Nam dùng °C).  
- Hỗ trợ kỹ sư hoặc nhà khoa học chuyển đổi nhanh dữ liệu nhiệt độ khi làm việc với thiết bị quốc tế.

## 3. Tính tổng các chữ số của một số
**Mô tả:** Nhập một số nguyên và tính tổng các chữ số của nó (ví dụ: 123 → 1 + 2 + 3 = 6).  
**Thời gian:** ~45 phút  
**Mã mẫu:**  
```python
number = int(input("Nhập một số nguyên: "))
total = 0
while number > 0:
    total += number % 10
    number //= 10
print(f"Tổng các chữ số: {total}")
```
**Công dụng thực tế:**  
- Kiểm tra tính hợp lệ của mã số (như số ISBN của sách hoặc mã vạch) bằng cách tính tổng chữ số và so sánh với quy tắc.  
- Ứng dụng trong trò chơi hoặc bài toán giải đố liên quan đến số học.

## 4. Kiểm tra số nguyên tố
**Mô tả:** Nhập một số nguyên và kiểm tra xem nó có phải số nguyên tố không.  
**Thời gian:** ~1 giờ  
**Mã mẫu:**  
```python
num = int(input("Nhập một số nguyên: "))
if num < 2:
    print(f"{num} không phải số nguyên tố.")
else:
    is_prime = True
    for i in range(2, int(num ** 0.5) + 1):
        if num % i == 0:
            is_prime = False
            break
    if is_prime:
        print(f"{num} là số nguyên tố.")
    else:
        print(f"{num} không phải số nguyên tố.")
```
**Công dụng thực tế:**  
- Dùng trong mật mã học (như thuật toán RSA) để tạo khóa mã hóa dựa trên số nguyên tố lớn.  
- Ứng dụng trong kiểm tra tính tối ưu của các bài toán phân bổ tài nguyên (ví dụ: chia công việc không bị trùng lặp).

## 5. Tạo số ngẫu nhiên
**Mô tả:** Tạo một số ngẫu nhiên trong khoảng do người dùng nhập (min và max).  
**Thời gian:** ~30 phút  
**Mã mẫu:**  
```python
import random
min_val = int(input("Nhập giá trị nhỏ nhất: "))
max_val = int(input("Nhập giá trị lớn nhất: "))
random_num = random.randint(min_val, max_val)
print(f"Số ngẫu nhiên: {random_num}")
```
**Công dụng thực tế:**  
- Dùng trong trò chơi (như xúc xắc, rút thăm may mắn) để tạo kết quả ngẫu nhiên.  
- Ứng dụng trong mô phỏng (simulation) để thử nghiệm các kịch bản (ví dụ: mô phỏng giao thông hoặc dự đoán thời tiết).

## 6. Loại bỏ phần tử trùng lặp trong danh sách
**Mô tả:** Nhập danh sách số (cách nhau bằng dấu cách) và loại bỏ các phần tử trùng lặp.  
**Thời gian:** ~45 phút  
**Mã mẫu:**  
```python
input_list = input("Nhập danh sách số (cách nhau bằng dấu cách): ").split()
numbers = [int(x) for x in input_list]
unique_numbers = list(set(numbers))
print(f"Danh sách sau khi loại bỏ trùng lặp: {unique_numbers}")
```
**Công dụng thực tế:**  
- Xử lý dữ liệu trong cơ sở dữ liệu để loại bỏ các bản ghi trùng (ví dụ: danh sách khách hàng không lặp lại).  
- Dùng trong phân tích dữ liệu để làm sạch tập dữ liệu trước khi phân tích (data cleaning).

## Lời khuyên
- **Thực hành:** Dành khoảng 30-60 phút cho mỗi bài, tổng cộng 4 giờ. Chạy thử với nhiều giá trị đầu vào khác nhau để kiểm tra tính đúng đắn.  
- **Ứng dụng thêm:** Nghĩ xem bạn có thể kết hợp các bài này vào một dự án lớn hơn không (ví dụ: một công cụ tính toán đa năng).  
- **Kiểm tra lỗi:** Thử nhập dữ liệu không hợp lệ để xem chương trình phản ứng thế nào và cải thiện nếu cần.


