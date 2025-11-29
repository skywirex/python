# Bước 2: Bắt đầu phát triển phần mềm (Xây dựng dự án)

### Virtual Environment trong Python là gì?
Virtual Environment (môi trường ảo) trong Python là một cách để tạo ra một môi trường độc lập cho từng dự án, giúp tránh xung đột giữa các phiên bản thư viện. Khi sử dụng Virtual Environment, bạn có thể cài đặt các gói Python riêng cho từng dự án mà không ảnh hưởng đến hệ thống hoặc các dự án khác.

## Cách sử dụng Virtual Environment trên **Linux** và **Windows**

### 1. Cài đặt Virtual Environment
Trước tiên, bạn cần cài đặt module `venv` (được tích hợp sẵn từ Python 3.3 trở đi). Nếu bạn chưa có, hãy cài đặt bằng lệnh:

```sh
pip install virtualenv
```

### 2. Tạo Virtual Environment
Di chuyển đến thư mục dự án của bạn và chạy lệnh:

#### Trên **Linux/macOS**
```sh
python3 -m venv myenv
```

#### Trên **Windows**
```sh
python -m venv myenv
```
Lệnh trên sẽ tạo một thư mục `myenv` chứa môi trường ảo.

### 3. Kích hoạt Virtual Environment

#### Trên **Linux/macOS**
```sh
source myenv/bin/activate
python3 -m venv ~/py_envs
source ~/py_envs/bin/activate
python3 -m pip install xyz
```

#### Trên **Windows** (CMD)
```cmd
myenv\Scripts\activate
```

#### Trên **Windows** (PowerShell)

```powershell
myenv\Scripts\Activate.ps1
```
Sau khi kích hoạt, bạn sẽ thấy tên môi trường (`myenv`) xuất hiện trước dấu nhắc lệnh.

### 4. Cài đặt gói trong Virtual Environment
Sau khi kích hoạt môi trường ảo, bạn có thể cài đặt các thư viện Python mà không ảnh hưởng đến hệ thống:

```sh
pip install <tên_thư_viện>
```

Ví dụ:
```sh
pip install numpy pandas
```

### 5. Kiểm tra danh sách thư viện đã cài đặt
```sh
pip list
```

### 6. Hủy kích hoạt Virtual Environment
Để thoát khỏi môi trường ảo, dùng lệnh:
```sh
deactivate
```

### 7. Xóa Virtual Environment
Nếu bạn muốn xóa môi trường ảo, chỉ cần xóa thư mục chứa nó:
```sh
rm -rf myenv   # Linux/macOS
rd /s /q myenv  # Windows (CMD)
```

### 8. Lưu danh sách thư viện và cài đặt lại
Nếu bạn muốn chia sẻ danh sách thư viện hoặc cài lại môi trường, hãy dùng:

**Xuất danh sách thư viện**
```sh
pip freeze > requirements.txt
```

**Cài đặt lại từ danh sách**
```sh
pip install -r requirements.txt
```

**Tóm lại**, Virtual Environment giúp cô lập thư viện cho từng dự án Python, tránh xung đột giữa các phiên bản. Việc sử dụng nó rất đơn giản với các lệnh `venv`, `activate`, `deactivate`, và `pip`.

## Ví dụ

Ba lệnh sau được sử dụng để tạo và làm việc với một môi trường ảo trong Python:  

```sh
python3 -m venv ~/py_envs
source ~/py_envs/bin/activate
python3 -m pip install xyz
```

## Giải thích từng lệnh:

### 1. Tạo môi trường ảo
```sh
python3 -m venv ~/py_envs
```
🔹 **Ý nghĩa**:
- `python3 -m venv` → Sử dụng mô-đun `venv` của Python để tạo một môi trường ảo.
- `~/py_envs` → Thư mục nơi môi trường ảo sẽ được tạo (nằm trong thư mục Home của user).  

📌 **Kết quả**:  
- Một thư mục `py_envs` sẽ được tạo trong `~/`, chứa các file cần thiết để chạy môi trường ảo:
  - `bin/` (hoặc `Scripts/` trên Windows) – Chứa các file thực thi.
  - `lib/` – Chứa các thư viện Python cài đặt trong môi trường ảo.
  - `include/` – Chứa các file header.
  - `pyvenv.cfg` – File cấu hình của môi trường ảo.

### **2. Kích hoạt môi trường ảo**
```sh
source ~/py_envs/bin/activate
```
🔹 **Ý nghĩa**:
- `source` → Chạy script để thiết lập môi trường hiện tại.
- `~/py_envs/bin/activate` → Chạy script kích hoạt môi trường ảo.  

📌 **Kết quả**:
- Dấu nhắc lệnh (terminal) sẽ thay đổi, hiển thị tên môi trường ảo, ví dụ:
  ```
  (py_envs) user@hostname:~$
  ```
- Bây giờ, Python và `pip` sẽ sử dụng môi trường ảo thay vì hệ thống Python toàn cục.

### **3. Cài đặt một thư viện vào môi trường ảo**
```sh
python3 -m pip install xyz
```
🔹 **Ý nghĩa**:
- `python3 -m pip` → Chạy `pip` bên trong môi trường ảo.
- `install xyz` → Cài đặt thư viện `xyz` vào môi trường ảo.  

📌 **Kết quả**:
- Thư viện `xyz` sẽ được cài đặt **chỉ trong môi trường ảo** (`~/py_envs/lib/...`), không ảnh hưởng đến hệ thống.  
- Bạn có thể kiểm tra các gói đã cài bằng:
  ```sh
  pip list
  ```

## Tóm tắt:

1. **Tạo** môi trường ảo trong thư mục `~/py_envs`.
2. **Kích hoạt** môi trường ảo để làm việc với nó.
3. **Cài đặt thư viện** vào môi trường ảo mà không ảnh hưởng đến hệ thống.  
