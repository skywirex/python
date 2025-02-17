# Ngày 5: Cấu trúc dữ liệu trong Python (4 giờ học)  

## 🔥 **1. Stack (Ngăn xếp)**
**Đặc điểm:**  
- Cấu trúc **LIFO** (*Last In, First Out* – Vào sau, ra trước).  
- Có hai thao tác chính:  
  - `push()`: Thêm phần tử vào ngăn xếp.  
  - `pop()`: Lấy phần tử ra khỏi ngăn xếp.  

**Cách triển khai bằng list:**  
```python
stack = []

# Thêm phần tử vào stack
stack.append(1)
stack.append(2)
stack.append(3)

# Lấy phần tử ra (LIFO)
print(stack.pop())  # 3
print(stack.pop())  # 2
```

📌 **Ghi nhớ:** Python list có sẵn `append()` và `pop()` để hoạt động như Stack.  

---

## 🔥 **2. Queue (Hàng đợi)**
**Đặc điểm:**  
- Cấu trúc **FIFO** (*First In, First Out* – Vào trước, ra trước).  
- Thao tác chính:  
  - `enqueue()`: Thêm phần tử vào cuối hàng đợi.  
  - `dequeue()`: Lấy phần tử ra khỏi đầu hàng đợi.  

**Cách triển khai bằng `collections.deque`:**  
```python
from collections import deque

queue = deque()

# Thêm phần tử vào queue
queue.append(1)
queue.append(2)
queue.append(3)

# Lấy phần tử ra (FIFO)
print(queue.popleft())  # 1
print(queue.popleft())  # 2
```

📌 **Ghi nhớ:** Dùng `deque` thay vì list để tối ưu hiệu suất.  

---

## 🔥 **3. Dictionary (Từ điển)**
**Đặc điểm:**  
- Lưu dữ liệu theo cặp `key: value`.  
- Truy xuất dữ liệu nhanh hơn list.  

**Ví dụ sử dụng:**  
```python
sinh_vien = {
    "ten": "Nguyen Van A",
    "tuoi": 20,
    "diem": 8.5
}

# Truy xuất dữ liệu
print(sinh_vien["ten"])  # Nguyen Van A
print(sinh_vien.get("diem"))  # 8.5

# Thêm mới hoặc cập nhật
sinh_vien["lop"] = "12A1"
sinh_vien["diem"] = 9.0
```

📌 **Ghi nhớ:** Dùng `.get()` để tránh lỗi nếu key không tồn tại.  

---

## 🔥 **4. Tuple (Bộ giá trị)**
**Đặc điểm:**  
- Giống list nhưng **bất biến** (không thay đổi được sau khi tạo).  
- Truy xuất nhanh hơn list.  

**Ví dụ sử dụng:**  
```python
toado = (10, 20)

# Truy xuất giá trị
print(toado[0])  # 10
print(toado[1])  # 20

# Không thể thay đổi giá trị (sẽ báo lỗi)
# toado[0] = 100  # ❌ Lỗi!
```

📌 **Ghi nhớ:** Dùng tuple khi dữ liệu không cần thay đổi.  

---

## 🔥 **5. Cây (Tree)**
**Đặc điểm:**  
- Cấu trúc dữ liệu có **nút gốc** và các **nút con**.  
- Mỗi nút có thể có nhiều con, nhưng chỉ có một cha.  

**Triển khai cây nhị phân bằng lớp `Node`:**  
```python
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

# Tạo cây
root = Node(10)
root.left = Node(5)
root.right = Node(15)

# Duyệt cây theo thứ tự NLR (Preorder)
def preorder(node):
    if node:
        print(node.value, end=" ")
        preorder(node.left)
        preorder(node.right)

preorder(root)  # Output: 10 5 15
```

📌 **Ghi nhớ:** Cây nhị phân có thể duyệt theo **Preorder (NLR), Inorder (LNR), Postorder (LRN)**.  

---

## 🔥 **6. Danh sách liên kết (Linked List)**
**Đặc điểm:**  
- Gồm các **nút (node)** liên kết với nhau.  
- Mỗi nút chứa **dữ liệu** và **trỏ đến nút tiếp theo**.  

**Triển khai danh sách liên kết đơn:**  
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        last = self.head
        while last.next:
            last = last.next
        last.next = new_node

    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end=" -> ")
            temp = temp.next
        print("None")

# Sử dụng danh sách liên kết
ll = LinkedList()
ll.append(1)
ll.append(2)
ll.append(3)

ll.print_list()  # Output: 1 -> 2 -> 3 -> None
```

📌 **Ghi nhớ:** So với list, danh sách liên kết **tốn bộ nhớ hơn nhưng thêm/xóa nhanh hơn**.  

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

