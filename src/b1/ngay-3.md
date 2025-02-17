# Ngày 3

Dưới đây là các bài tập lập trình đơn giản bằng Python:

### 1. **Hoán đổi hai biến**
```python
a = 5
b = 10

# Hoán đổi
a, b = b, a

print("Sau khi hoán đổi: a =", a, ", b =", b)
```

---

### 2. **Chuyển đổi độ C sang độ F**
```python
def c_to_f(celsius):
    return (celsius * 9/5) + 32

c = float(input("Nhập độ C: "))
print(f"{c}°C = {c_to_f(c)}°F")
```

---

### 3. **Tính tổng các chữ số của một số**
```python
def sum_of_digits(n):
    return sum(int(digit) for digit in str(abs(n)))

num = int(input("Nhập số nguyên: "))
print("Tổng các chữ số:", sum_of_digits(num))
```

---

### 4. **Kiểm tra số nguyên tố**
```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

num = int(input("Nhập số nguyên: "))
print(f"{num} là số nguyên tố" if is_prime(num) else f"{num} không phải số nguyên tố")
```

---

### 5. **Tạo số ngẫu nhiên**
```python
import random

random_number = random.randint(1, 100)
print("Số ngẫu nhiên:", random_number)
```

---

### 6. **Loại bỏ phần tử trùng lặp trong danh sách**
```python
def remove_duplicates(lst):
    return list(set(lst))

numbers = [1, 2, 2, 3, 4, 4, 5]
print("Danh sách sau khi loại bỏ trùng lặp:", remove_duplicates(numbers))
```

Bài toán hoán đổi hai biến thường được sử dụng trong lập trình để thay đổi giá trị của hai biến mà không làm mất dữ liệu. Dưới đây là một số tình huống thực tế mà hoán đổi hai biến có thể hữu ích:  

### 1. **Sắp xếp danh sách (Sorting Algorithms)**  
Khi triển khai các thuật toán sắp xếp như **Bubble Sort, Selection Sort, Quick Sort**, ta thường cần hoán đổi vị trí của các phần tử để đưa danh sách về thứ tự mong muốn.  
Ví dụ:  
```python
arr = [3, 1, 2]
arr[0], arr[1] = arr[1], arr[0]  # Hoán đổi 3 và 1
print(arr)  # Output: [1, 3, 2]
```

---

### 2. **Hoán đổi giá trị trong trò chơi (Game Development)**  
Khi lập trình game, ta có thể cần hoán đổi vị trí của hai đối tượng, ví dụ như hai quân cờ trong một bàn cờ.  

---

### 3. **Đổi chỗ hai biến trong thuật toán đệ quy**  
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

### 4. **Hoán đổi giá trị trong thuật toán tìm kiếm tối ưu**  
Khi thực hiện **tối ưu hóa bộ nhớ hoặc thuật toán tìm kiếm**, việc hoán đổi hai biến có thể giúp giảm chi phí tính toán.

Ví dụ: **Hoán đổi giá trị nhỏ nhất lên đầu danh sách**  
```python
arr = [4, 2, 9, 1]
min_index = arr.index(min(arr))
arr[0], arr[min_index] = arr[min_index], arr[0]  # Đưa giá trị nhỏ nhất về đầu danh sách
print(arr)  # Output: [1, 2, 9, 4]
```

---

### 5. **Đảo ngược giá trị hai biến trong xử lý dữ liệu**  
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


### **Chuyển đổi độ C sang độ F để làm gì?**  

Việc chuyển đổi từ **độ C (Celsius, °C)** sang **độ F (Fahrenheit, °F)** rất quan trọng trong nhiều lĩnh vực như **khoa học, y tế, hàng không, dự báo thời tiết và du lịch**.  

Công thức chuyển đổi:  
\[
°F = (°C \times \frac{9}{5}) + 32
\]

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