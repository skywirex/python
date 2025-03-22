# Ngày 5: Cấu trúc dữ liệu trong Python (4 giờ học)  

## Lịch học gợi ý (4 giờ)
- **Giờ 1**: Stack (30 phút) + Queue (30 phút).
- **Giờ 2**: Dictionary (45 phút) + Tuple (15 phút).
- **Giờ 3**: Cây (60 phút).
- **Giờ 4**: Danh sách liên kết (45 phút) + Ôn tập (15 phút).

## 1. Stack (Ngăn xếp) - 30 phút

**Khái niệm**: Stack là cấu trúc dữ liệu "vào sau, ra trước" (**LIFO - Last In, First Out**). Giống như xếp đĩa, bạn chỉ lấy được đĩa trên cùng.

**Triển khai trong Python**: Dùng list với `append()` (đẩy vào) và `pop()` (lấy ra).

```python
# Tạo stack
stack = []

# Đẩy phần tử vào
stack.append(1)
stack.append(2)
stack.append(3)
print("Stack sau khi thêm:", stack)  # [1, 2, 3]

# Lấy phần tử ra
top = stack.pop()
print("Phần tử lấy ra:", top)  # 3
print("Stack sau khi pop:", stack)  # [1, 2]
```

**Ứng dụng**: Kiểm tra ngoặc hợp lệ (e.g., `()`, `{}`), quay lại thao tác (undo).

**Bài tập**: Viết hàm kiểm tra chuỗi ngoặc như `"()"` hoặc `"({[]})"` có hợp lệ không.

---

## 2. Queue (Hàng đợi) - 30 phút

**Khái niệm**: Queue là "vào trước, ra trước" (**FIFO - First In, First Out**). Như xếp hàng mua vé.

**Triển khai trong Python**: Dùng `collections.deque` cho hiệu quả (thay vì list).

```python
from collections import deque

# Tạo queue
queue = deque()

# Thêm phần tử
queue.append(1)
queue.append(2)
queue.append(3)
print("Queue sau khi thêm:", list(queue))  # [1, 2, 3]

# Lấy phần tử
front = queue.popleft()
print("Phần tử lấy ra:", front)  # 1
print("Queue sau khi pop:", list(queue))  # [2, 3]
```

**Ứng dụng**: Xử lý tác vụ theo thứ tự, hàng đợi in ấn.

**Bài tập**: Mô phỏng hàng đợi người mua vé, thêm 5 người, phục vụ 3 người.

---

## 3. Dictionary (Từ điển) - 45 phút

**Khái niệm**: Lưu dữ liệu dạng **key-value** (khóa-giá trị), truy cập nhanh qua key.

**Triển khai trong Python**:

```python
# Tạo dictionary
my_dict = {"name": "Alex", "age": 25, "city": "Hanoi"}

# Truy cập
print(my_dict["name"])  # Alex

# Thêm/sửa
my_dict["job"] = "Developer"
my_dict["age"] = 26
print("Sau khi cập nhật:", my_dict)  # {'name': 'Alex', 'age': 26, 'city': 'Hanoi', 'job': 'Developer'}

# Xóa
del my_dict["city"]
print("Sau khi xóa:", my_dict)  # {'name': 'Alex', 'age': 26, 'job': 'Developer'}
```

**Ứng dụng**: Đếm tần suất từ, lưu thông tin cấu trúc (như hồ sơ).

**Bài tập**: Đếm số lần xuất hiện của mỗi chữ cái trong chuỗi `"hello world"`.

---

## 4. Tuple (Bộ dữ liệu) - 30 phút

**Khái niệm**: Giống list nhưng **không thay đổi được** (immutable), dùng để lưu dữ liệu cố định.

**Triển khai trong Python**:

```python
# Tạo tuple
my_tuple = (1, 2, 3, "hello")

# Truy cập
print(my_tuple[0])  # 1
print(my_tuple[-1])  # hello

# Đếm và tìm
print(my_tuple.count(2))  # 1 (số lần xuất hiện của 2)
print(my_tuple.index("hello"))  # 3 (vị trí của "hello")
```

**Ứng dụng**: Lưu tọa độ `(x, y)`, trả về nhiều giá trị từ hàm.

**Bài tập**: Viết hàm trả về tuple chứa `(tổng, hiệu)` của 2 số.

---

## Lưu ý
- **Thực hành**: Sau mỗi phần, chạy code và thử sửa đổi (thêm/xóa phần tử, in ngược, v.v.).
- **Debug**: Dùng `print()` để kiểm tra giá trị giữa chừng.
- **Mở rộng**: Tìm hiểu thêm về `set` (tập hợp) hoặc cách tối ưu cây nhị phân.

---

## 📌 **Tóm tắt**
| Cấu trúc dữ liệu | Đặc điểm chính |
|-----------------|-----------------|
| **Stack** | LIFO (Vào sau, ra trước) |
| **Queue** | FIFO (Vào trước, ra trước) |
| **Dictionary** | Dữ liệu dạng key-value, truy xuất nhanh |
| **Tuple** | Giống list nhưng không thay đổi được |
| **Tree** | Dạng phân cấp, có nút gốc và nút con |
| **Linked List** | Danh sách các nút liên kết với nhau |

