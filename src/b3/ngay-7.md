# Debugging trong Python bằng PyCharm IDE


## Mục tiêu

Sau bài viết này bạn sẽ biết được cách:

    - Thiết lập và sử dụng breakpoint trong PyCharm.
    - Chạy chương trình ở chế độ Debug và kiểm tra giá trị biến.
    - Sử dụng các công cụ như Step Over, Watch, và Evaluate Expression.
    - Sửa lỗi chỉ số vượt quá giới hạn trong vòng lặp.


Dưới đây là một ví dụ minh họa các cách gỡ lỗi (debugging) thông thường trong Python bằng PyCharm IDE. Ví dụ này sẽ sử dụng một đoạn code đơn giản có lỗi, và tôi sẽ hướng dẫn từng bước cách sử dụng các công cụ gỡ lỗi trong PyCharm để tìm và sửa lỗi.

## Ví dụ: Tính tổng các số trong danh sách

### Mã nguồn (có lỗi cố ý)

```python
def calculate_sum(numbers):
    total = 0
    for i in range(len(numbers) + 1):  # Lỗi 1: Vượt quá chỉ số của danh sách
        total += numbers[i]
    return total

def main():
    my_list = [1, 2, 3, 4, 5]
    result = calculate_sum(my_list)
    print(f"Tổng của danh sách là: {result}")

if __name__ == "__main__":
    main()
```

**Vấn đề**: Chương trình trên sẽ gặp lỗi `IndexError: list index out of range` vì vòng lặp `for` truy cập chỉ số vượt quá độ dài của danh sách.

## Các bước gỡ lỗi trong PyCharm

### Bước 1: Chạy chương trình và xác định lỗi
1. Mở PyCharm, tạo một file Python mới (ví dụ: `debug_example.py`) và sao chép mã nguồn trên.
2. Nhấn `Run` (Shift + F10) để chạy chương trình.
3. PyCharm sẽ hiển thị lỗi trong cửa sổ Run:
   ```
   IndexError: list index out of range
   ```
   Điều này cho biết lỗi xảy ra trong hàm `calculate_sum` khi truy cập `numbers[i]`.

### Bước 2: Thiết lập điểm ngắt (Breakpoint)
- Trong PyCharm, nhấp vào lề trái của dòng code mà bạn nghi ngờ có lỗi (ví dụ: dòng `total += numbers[i]` trong hàm `calculate_sum`).
- Một dấu chấm đỏ sẽ xuất hiện, biểu thị breakpoint.
- Điều này sẽ tạm dừng chương trình tại dòng đó khi chạy ở chế độ gỡ lỗi.

### Bước 3: Chạy ở chế độ gỡ lỗi (Debug Mode)
- Nhấn `Debug` (Shift + F9) hoặc nhấp vào biểu tượng con bọ (bug) trong thanh công cụ.
- PyCharm sẽ chạy chương trình và dừng lại tại breakpoint đã đặt.
- Cửa sổ Debug sẽ mở ra, hiển thị:
  - **Variables**: Các biến hiện tại (`total`, `numbers`, `i`).
  - **Call Stack**: Ngăn xếp lệnh gọi (cho biết chương trình đang ở đâu).

### Bước 4: Kiểm tra giá trị biến
- Tại breakpoint, kiểm tra giá trị của `i` và `len(numbers)` trong cửa sổ Variables.
- Giả sử `i = 5` và `len(numbers) = 5`, điều này cho thấy `i` đang truy cập chỉ số không hợp lệ (vì danh sách chỉ có chỉ số từ 0 đến 4).
- Điều này xác nhận lỗi nằm ở giới hạn của vòng lặp `for`.

### Bước 5: Sử dụng Watch để theo dõi biểu thức
- Trong cửa sổ Debug, nhấp vào `Add to Watches` và nhập biểu thức `len(numbers)` hoặc `i < len(numbers)`.
- Điều này giúp bạn theo dõi các giá trị hoặc điều kiện trong suốt quá trình thực thi.

### Bước 6: Bước qua code (Step Through Code)
Sử dụng các nút điều khiển trong cửa sổ Debug:
- **Step Over (F8)**: Chạy dòng hiện tại và chuyển đến dòng tiếp theo.
- **Step Into (F7)**: Đi vào bên trong hàm nếu có lời gọi hàm.
- **Resume Program (F9)**: Tiếp tục chạy cho đến breakpoint tiếp theo hoặc kết thúc.

Nhấn `Step Over` để kiểm tra từng lần lặp của vòng lặp. Khi `i = 5`, bạn sẽ thấy lỗi xảy ra.

### Bước 7: Sửa lỗi
Dựa trên phân tích, lỗi xảy ra do vòng lặp chạy từ 0 đến `len(numbers)` (thay vì `len(numbers) - 1`). Sửa lại hàm `calculate_sum`:

```python
def calculate_sum(numbers):
    total = 0
    for i in range(len(numbers)):  # Sửa lỗi: Bỏ +1
        total += numbers[i]
    return total
```

### Bước 8: Kiểm tra lại
- Chạy lại chương trình bằng `Run` hoặc `Debug` để xác nhận lỗi đã được sửa.
- Kết quả mong đợi:
  ```
  Tổng của danh sách là: 15
  ```

### Bước 9: Sử dụng công cụ bổ sung trong PyCharm
- **Evaluate Expression**: Nhấp chuột phải tại breakpoint, chọn `Evaluate Expression` để kiểm tra giá trị của bất kỳ biểu thức nào (ví dụ: `numbers[i]`).
- **Conditional Breakpoint**: Nhấp chuột phải vào breakpoint, thêm điều kiện (ví dụ: `i >= len(numbers)`) để chỉ dừng khi điều kiện đúng.
- **Log Breakpoint**: Cấu hình breakpoint để in giá trị biến ra console mà không dừng chương trình.

## Các mẹo gỡ lỗi khác trong PyCharm

- **Sử dụng Console để kiểm tra nhanh**:
  Trong cửa sổ Python Console, bạn có thể nhập các lệnh để kiểm tra hàm hoặc biến, ví dụ:
  ```python
  numbers = [1, 2, 3, 4, 5]
  len(numbers)
  ```

- **Kiểm tra Stack Trace**:
  Khi lỗi xảy ra, nhấp vào các liên kết trong stack trace trong cửa sổ Run để nhảy đến dòng code gây lỗi.

- **Tìm kiếm lỗi phổ biến**:
  Sử dụng tính năng Code Inspection của PyCharm (màu vàng/xanh dưới code) để phát hiện lỗi tiềm ẩn trước khi chạy.