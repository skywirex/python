# Bất đồng bộ (asynchronous) trong Python


Trong Python, **"bất đồng bộ"** là cách viết mã cho phép các tác vụ chạy độc lập mà không cần đợi nhau hoàn thành.  
Thông thường, Python thực thi mã từng dòng (đồng bộ), nên nếu một tác vụ (như tải file) mất thời gian, chương trình sẽ đợi đến khi xong mới chuyển sang dòng tiếp theo.  

Lập trình bất đồng bộ, sử dụng `async` và `await`, cho phép chương trình bắt đầu một tác vụ và tiếp tục làm việc khác trong khi tác vụ đó chạy nền.  
Điều này rất hữu ích cho các tác vụ như lấy dữ liệu từ web, đọc file, hoặc xử lý nhiều yêu cầu, nơi việc đợi sẽ làm chậm chương trình.

## **Các khái niệm quan trọng**
- `async`: Đánh dấu một hàm là bất đồng bộ, nghĩa là nó có thể tạm dừng để mã khác chạy trong khi chờ đợi (như thao tác I/O).
- `await`: Tạm dừng hàm bất đồng bộ tại điểm đó cho đến khi tác vụ được chờ (như gọi mạng) hoàn thành, mà không làm tắc nghẽn phần còn lại của chương trình.

**Ví dụ minh họa:**  
Hãy nghĩ như nấu ăn:  
- **Đồng bộ** là bạn đợi nước sôi rồi mới thái rau.  
- **Bất đồng bộ** là bạn đun nước, thái rau trong lúc đợi, và quay lại khi nước sôi.

---

## **Ứng dụng thực tế**
Một trường hợp phổ biến là gửi nhiều yêu cầu web.  
- Nếu không dùng `async`, bạn phải đợi từng yêu cầu hoàn thành trước khi bắt đầu cái tiếp theo.  
- Với `async` và `await`, bạn có thể gửi tất cả yêu cầu cùng lúc và xử lý phản hồi khi chúng đến, tiết kiệm thời gian.

---

## **Ví dụ đơn giản**
Dưới đây là ví dụ sử dụng `asyncio` (thư viện bất đồng bộ của Python) để mô phỏng việc lấy dữ liệu từ hai "trang web" cùng lúc:

```python
import asyncio

# Mô phỏng một tác vụ mất thời gian (như lấy dữ liệu từ web)
async def fetch_data(site):
    print(f"Bắt đầu lấy dữ liệu từ {site}...")
    await asyncio.sleep(2)  # Mô phỏng độ trễ 2 giây (ví dụ: yêu cầu mạng)
    print(f"Đã lấy xong dữ liệu từ {site}")
    return f"Dữ liệu từ {site}"

# Hàm bất đồng bộ chính để chạy nhiều tác vụ
async def main():
    # Bắt đầu cả hai tác vụ "cùng lúc"
    task1 = fetch_data("Site A")
    task2 = fetch_data("Site B")
    
    # Chờ cả hai hoàn thành và lấy kết quả
    results = await asyncio.gather(task1, task2)
    print("Hoàn thành tất cả! Kết quả:", results)

# Chạy chương trình bất đồng bộ
asyncio.run(main())
```

### **Kết quả:**
```
Bắt đầu lấy dữ liệu từ Site A...
Bắt đầu lấy dữ liệu từ Site B...
Đã lấy xong dữ liệu từ Site A
Đã lấy xong dữ liệu từ Site B
Hoàn thành tất cả! Kết quả: ['Dữ liệu từ Site A', 'Dữ liệu từ Site B']
```

---

## **Chuyện gì đang xảy ra?**
1. `fetch_data` là hàm bất đồng bộ giả lập việc lấy dữ liệu với độ trễ 2 giây (`await asyncio.sleep(2)`).
2. Trong `main`, chúng ta bắt đầu cả hai "lần lấy dữ liệu" mà không cần đợi cái này xong mới làm cái kia.
3. `asyncio.gather` chạy chúng đồng thời và đợi tất cả hoàn thành.
4. **Tổng thời gian khoảng 2 giây (không phải 4)**, vì các tác vụ chồng lấp nhau.

> Đây là ví dụ đơn giản, nhưng trong thực tế, bạn có thể thay `asyncio.sleep` bằng `aiohttp.get` để lấy dữ liệu web thật.  
> Async tỏa sáng khi xử lý nhiều tác vụ phụ thuộc I/O như vậy!

---

## **Lược đồ đơn giản: Đồng bộ vs Bất đồng bộ**
### **1. Đồng bộ (Synchronous)**
```
Thời gian: 0s   2s   4s   6s
Task 1:   [----]         (Chờ 2 giây)
Task 2:         [----]   (Chờ 2 giây)
Tổng: 4 giây
```
- **Task 1 bắt đầu, mất 2 giây, chương trình đợi.**
- **Task 2 chỉ bắt đầu sau khi Task 1 xong, mất thêm 2 giây.**
- **Tổng thời gian: 4 giây.**

### **2. Bất đồng bộ (Asynchronous)**
```
Thời gian: 0s   2s   4s
Task 1:   [----]      
Task 2:   [----]      
Tổng: 2 giây
```
- **Task 1 và Task 2 bắt đầu cùng lúc.**
- **Cả hai chạy song song, mỗi cái mất 2 giây.**
- **Tổng thời gian: chỉ 2 giây, vì chúng chồng lấp.**

---

## **Giải thích hình dung**
Hãy tưởng tượng bạn là một đầu bếp trong bếp:

### **Đồng bộ:**
1. Bạn đun nước (**Task 1**) và đứng đợi 2 phút cho nước sôi, không làm gì khác.
2. Sau đó, bạn thái rau (**Task 2**) trong 2 phút.
3. **Tổng cộng: 4 phút.**

### **Bất đồng bộ:**
1. Bạn bật bếp đun nước (**Task 1**), rồi ngay lập tức đi thái rau (**Task 2**).
2. Trong khi nước sôi (2 phút), bạn đã thái xong rau (cũng 2 phút).
3. **Sau 2 phút, cả nước sôi lẫn rau thái đều xong.**
4. **Tổng cộng: chỉ 2 phút.**

`async` và `await` trong Python giống như bạn **"giao việc"** cho bếp đun nước và kiểm tra lại khi cần (`await`), thay vì đứng đợi.

---

## **Minh họa qua mã ví dụ trước**
```python
async def fetch_data(site):
    print(f"Bắt đầu lấy dữ liệu từ {site}...")
    await asyncio.sleep(2)  # Chờ 2 giây
    print(f"Đã lấy xong dữ liệu từ {site}")
    return f"Dữ liệu từ {site}"

async def main():
    results = await asyncio.gather(fetch_data("Site A"), fetch_data("Site B"))
    print("Kết quả:", results)

asyncio.run(main())
```

### **Lược đồ dòng thời gian:**
```
Thời gian: 0s       2s
Site A:   [--------]  (Bắt đầu -> Xong)
Site B:   [--------]  (Bắt đầu -> Xong)
Tổng: 2 giây
```
- **0s:** Cả "Site A" và "Site B" bắt đầu lấy dữ liệu.
- **Trong 2 giây:** Cả hai chạy song song.
- **2s:** Cả hai hoàn thành cùng lúc, **tổng thời gian chỉ 2 giây**.