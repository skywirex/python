# Cơ bản về nhật kí (log) trong Python

Ghi nhật ký cơ bản trong Python liên quan đến việc sử dụng mô-đun `logging` có sẵn để ghi lại các sự kiện, lỗi hoặc thông tin trong quá trình thực thi chương trình. Đây là một cách mạnh mẽ để theo dõi những gì đang xảy ra trong mã của bạn, gỡ lỗi và giám sát hành vi ứng dụng mà không làm lộn xộn đầu ra với các lệnh `print`. Dưới đây là giải thích về cách hoạt động và cách áp dụng hiệu quả trong một dự án.

### Cơ bản về ghi nhật ký trong Python

Mô-đun `logging` cung cấp một khung linh hoạt với các thành phần chính sau:

- **Loggers**: Các đối tượng bạn sử dụng để ghi lại thông điệp. Mỗi logger có một tên, thường phân cấp (ví dụ: `myapp.module1`).
- **Handlers**: Quyết định nơi các thông điệp nhật ký được gửi đến (ví dụ: màn hình, tệp, mạng).
- **Formatters**: Xác định cấu trúc của đầu ra nhật ký (ví dụ: dấu thời gian, mức độ nhật ký, thông điệp).

#### Mức độ nhật ký

Chỉ ra mức độ nghiêm trọng của thông điệp:

- `DEBUG` (10): Thông tin chi tiết để gỡ lỗi.
- `INFO` (20): Xác nhận rằng mọi thứ đang hoạt động.
- `WARNING` (30): Điều gì đó bất ngờ nhưng không nghiêm trọng.
- `ERROR` (40): Một vấn đề cần chú ý.
- `CRITICAL` (50): Một thất bại nghiêm trọng.

Theo mặc định, ghi nhật ký của Python bắt đầu từ mức `WARNING`, vì vậy các thông điệp `DEBUG` và `INFO` sẽ không hiển thị trừ khi bạn cấu hình khác đi.

### Ví dụ đơn giản

```python
import logging

# Cấu hình cơ bản
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger("myapp")

# Ghi lại một số thông điệp
logger.debug("Điều này sẽ không hiển thị theo mặc định")
logger.info("Bắt đầu chương trình")
logger.warning("Có gì đó có thể không ổn")
logger.error("Đã xảy ra lỗi!")
```

#### Đầu ra (với `level=logging.INFO`):
```
INFO:myapp:Bắt đầu chương trình
WARNING:myapp:Có gì đó có thể không ổn
ERROR:myapp:Đã xảy ra lỗi!
```

---

## Cách áp dụng ghi nhật ký hiệu quả trong một dự án

### 1. Thiết lập cấu hình phù hợp

Sử dụng `basicConfig` cho các tập lệnh nhỏ, nhưng đối với các dự án lớn hơn, hãy cấu hình ghi nhật ký theo chương trình hoặc qua tệp cấu hình.

Ví dụ với một handler tệp:

```python
import logging

logger = logging.getLogger("myapp")
logger.setLevel(logging.DEBUG)  # Thiết lập mức độ của logger

# Tạo một handler tệp
fh = logging.FileHandler("app.log")
fh.setLevel(logging.DEBUG)

# Tạo một handler màn hình
ch = logging.StreamHandler()
ch.setLevel(logging.INFO)

# Xác định một formatter
formatter = logging.Formatter("%(asctime)s - %(name)s - %(levelname)s - %(message)s")
fh.setFormatter(formatter)
ch.setFormatter(formatter)

# Thêm handler vào logger
logger.addHandler(fh)
logger.addHandler(ch)

logger.debug("Thông tin gỡ lỗi cho tệp nhật ký")
logger.info("Thông tin chung cho cả màn hình và tệp")
logger.error("Thông điệp lỗi ở mọi nơi")
```

#### Đầu ra trong `app.log`:
```
2025-04-01 12:00:00,123 - myapp - DEBUG - Thông tin gỡ lỗi cho tệp nhật ký
2025-04-01 12:00:00,124 - myapp - INFO - Thông tin chung cho cả màn hình và tệp
2025-04-01 12:00:00,125 - myapp - ERROR - Thông điệp lỗi ở mọi nơi
```

#### Đầu ra màn hình:
```
2025-04-01 12:00:00,124 - myapp - INFO - Thông tin chung cho cả màn hình và tệp
2025-04-01 12:00:00,125 - myapp - ERROR - Thông điệp lỗi ở mọi nơi
```

### 2. Sử dụng Logger có tên

Trong một dự án với nhiều mô-đun, sử dụng tên logger phân cấp để phân biệt giữa các thành phần. Ví dụ:

```python
logger = logging.getLogger(__name__)
```

Điều này giúp truy vết nguồn gốc của thông điệp nhật ký.

### 3. Ghi lại thông tin có ý nghĩa

**NÊN:** Ghi lại các sự kiện quan trọng.

**KHÔNG:** Lạm dụng `DEBUG` hoặc ghi dữ liệu nhạy cảm.

Ví dụ:

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    logger.error("Phát hiện chia cho số không", exc_info=True)
```

### 4. Điều chỉnh mức độ nhật ký cho các môi trường

```python
import os
env = os.getenv("ENV", "dev")
logger.setLevel(logging.DEBUG if env == "dev" else logging.INFO)
```

### 5. Xoay vòng nhật ký cho các dự án lớn

```python
from logging.handlers import RotatingFileHandler

handler = RotatingFileHandler("app.log", maxBytes=1024*1024, backupCount=5)
handler.setFormatter(formatter)
logger.addHandler(handler)
```

### 6. Tập trung hóa cấu hình ghi nhật ký

```python
# logging_config.py
import logging

def setup_logging():
    logger = logging.getLogger("myapp")
    logger.setLevel(logging.DEBUG)
    handler = logging.FileHandler("app.log")
    handler.setLevel(logging.DEBUG)
    formatter = logging.Formatter("%(asctime)s - %(levelname)s - %(message)s")
    handler.setFormatter(formatter)
    logger.addHandler(handler)
    return logger
```

Sau đó nhập nó:

```python
from logging_config import setup_logging
logger = setup_logging()
logger.info("Ứng dụng đã khởi động")
```

### 7. Kiểm tra ghi nhật ký của bạn

Đảm bảo nhật ký được ghi như kỳ vọng bằng cách sử dụng unit test.

## Tại sao nó hiệu quả

- **Gỡ lỗi:** Nhật ký chỉ ra chính xác lỗi.
- **Giám sát:** Nhật ký `INFO` theo dõi hoạt động, `ERROR` đánh dấu vấn đề.
- **Khả năng mở rộng:** Ghi nhật ký có cấu trúc thích nghi với sự phát triển của dự án.

Hãy bắt đầu với ghi nhật ký cơ bản trên màn hình, sau đó mở rộng với các `handler` và `formatter` khi dự án của bạn yêu cầu!

