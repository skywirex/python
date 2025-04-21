# Json trong Python


## 1. Cơ bản về JSON và Python

**JSON (JavaScript Object Notation)** là một định dạng dữ liệu nhẹ, dễ đọc, được sử dụng để trao đổi dữ liệu giữa các hệ thống. Trong Python, JSON được xử lý thông qua module `json`.

### Đặc điểm của JSON:

- Dữ liệu JSON bao gồm các cặp key-value.
- Các kiểu dữ liệu cơ bản:
  - Chuỗi (string): `"name": "John"`
  - Số (number): `"age": 30`
  - Boolean: `"is_student": true`
  - Mảng (array): `"scores": [90, 85, 88]`
  - Đối tượng (object): `"address": {"street": "123 Main St", "city": "Hanoi"}`
  - Null: `"nickname": null`

### Module `json` trong Python

Module `json` cung cấp các phương thức để:

- Chuyển đổi dữ liệu Python sang JSON (*serialization*).
- Chuyển đổi JSON thành dữ liệu Python (*deserialization*).

**Cách nhập module:**

```python
import json
```

## 2. Các thao tác cơ bản với JSON

### 2.1. Chuyển đổi từ Python sang JSON (Serialization)

Sử dụng `json.dumps()` để chuyển đổi một đối tượng Python (dict, list, str, int, float, bool, None) thành chuỗi JSON.

```python
import json

data = {
    "name": "Nguyen Van A",
    "age": 25,
    "is_student": True,
    "scores": [90, 85, 88],
    "address": {"street": "123 Main St", "city": "Hanoi"}
}

json_string = json.dumps(data)
print(json_string)

# Định dạng đẹp (pretty print)
json_string_pretty = json.dumps(data, indent=4)
print(json_string_pretty)
```

### 2.2. Chuyển đổi từ JSON sang Python (Deserialization)

Sử dụng `json.loads()` để chuyển chuỗi JSON thành đối tượng Python.

```python
import json

json_string = '{"name": "Nguyen Van A", "age": 25, "is_student": true}'

data = json.loads(json_string)
print(data)
print(data["name"])  # Output: Nguyen Van A
```

### 2.3. Làm việc với file JSON

**Ghi JSON vào file (`json.dump`):**

```python
import json

data = {"name": "Nguyen Van A", "age": 25}
with open("data.json", "w") as file:
    json.dump(data, file, indent=4)
```

**Đọc JSON từ file (`json.load`):**

```python
import json

with open("data.json", "r") as file:
    data = json.load(file)
print(data)
```

## 3. Các kỹ thuật nâng cao với JSON

### 3.1. Xử lý các kiểu dữ liệu phức tạp

**Tùy chỉnh mã hóa JSON (`default`):**

```python
import json
from datetime import datetime

data = {"name": "Nguyen Van A", "created_at": datetime.now()}

def custom_serializer(obj):
    if isinstance(obj, datetime):
        return obj.isoformat()
    raise TypeError("Type not serializable")

json_string = json.dumps(data, default=custom_serializer)
print(json_string)
```

**Tùy chỉnh giải mã JSON (`object_hook`):**

```python
import json

class User:
    def __init__(self, name, age):
        self.name = name
        self.age = age

def object_hook(dict_data):
    if "name" in dict_data and "age" in dict_data:
        return User(dict_data["name"], dict_data["age"])
    return dict_data

json_string = '{"name": "Nguyen Van A", "age": 25}'
user = json.loads(json_string, object_hook=object_hook)
print(user.name, user.age)
```

### 3.2. Xử lý JSON lớn với `ijson`

**Cài đặt:**

```bash
pip install ijson
```

**Ví dụ:**

```python
import ijson

with open("large_data.json", "r") as file:
    parser = ijson.items(file, "item")
    for item in parser:
        print(item)
```

### 3.3. Xử lý lỗi JSON

```python
import json

invalid_json = '{"name": "Nguyen Van A", "age": 25'  # Thiếu dấu }

try:
    data = json.loads(invalid_json)
except json.JSONDecodeError as e:
    print(f"Error decoding JSON: {e}")
```

### 3.4. Tối ưu hóa hiệu suất với `orjson` hoặc `ujson`

**Cài đặt:**

```bash
pip install orjson
```

**Ví dụ với `orjson`:**

```python
import orjson

data = {"name": "Nguyen Van A", "age": 25}
json_bytes = orjson.dumps(data)
print(json_bytes.decode())
```

### 3.5. Làm việc với API và JSON

```python
import requests

response = requests.get("https://api.github.com/users/octocat")
data = response.json()
print(data["login"])
```

## 4. Ứng dụng thực tế

### 4.1. Lưu trữ cấu hình

```python
import json

config = {
    "database": {"host": "localhost", "port": 5432},
    "debug": True
}

with open("config.json", "w") as file:
    json.dump(config, file, indent=4)

with open("config.json", "r") as file:
    config = json.load(file)
print(config["database"]["host"])
```

### 4.2. Xây dựng API với Flask

```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.route("/api/user")
def get_user():
    user = {"name": "Nguyen Van A", "age": 25}
    return jsonify(user)

if __name__ == "__main__":
    app.run()
```

### 4.3. Phân tích dữ liệu lớn (log, API, NoSQL)

```python
import json

log_data = '''
[
    {"timestamp": "2025-04-21T10:00:00", "event": "login", "user": "Nguyen Van A"},
    {"timestamp": "2025-04-21T10:01:00", "event": "logout", "user": "Nguyen Van A"}
]
'''

logs = json.loads(log_data)
for log in logs:
    print(f"{log['timestamp']}: {log['event']} by {log['user']}")
```

## 5. Tài liệu và tài nguyên học thêm

- [Tài liệu chính thức của Python](https://docs.python.org/3/library/json.html)
- Thư viện nâng cao:
  - [orjson](https://github.com/ijl/orjson)
  - [ijson](https://github.com/isagalaev/ijson)

### Học qua dự án:

- Xây dựng ứng dụng lưu trữ danh bạ sử dụng JSON.
- Tạo một API đơn giản với Flask hoặc FastAPI.
- Phân tích dữ liệu từ API công khai như GitHub hoặc OpenWeather.

---

## Tóm tắt

- **Cơ bản:** `json.dumps`, `json.loads`, `json.dump`, `json.load`.
- **Nâng cao:** Tùy chỉnh mã hóa/giải mã, xử lý dữ liệu lớn (`ijson`), tối ưu (`orjson`), làm việc với API.
- **Thực hành:** Lưu trữ cấu hình, xây dựng API, phân tích dữ liệu.

