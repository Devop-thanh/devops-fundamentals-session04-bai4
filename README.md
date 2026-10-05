# Báo cáo Bài 4: Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)

## 1. Mục tiêu
- Cấu hình tệp tin ẩn `.gitignore` để tự động bỏ qua các file nhạy cảm.
- Gỡ bỏ file đã commit ra khỏi cache theo dõi của Git một cách an toàn.
- Chỉnh sửa thông điệp của commit gần nhất bằng tùy chọn `--amend`.

## 2. Các bước thực hiện
Trong quá trình làm bài, em đã lỡ tạo và commit nhầm file `credentials.txt` bằng lệnh:
```bash
git add credentials.txt
git commit -m "Add credentials file"
```

### Bước 1: Tạo file .gitignore
Để Git tự động bỏ qua file `credentials.txt` trong tương lai, em đã tạo file `.gitignore` và thêm tên file vào:
```bash
echo "credentials.txt" > .gitignore
```

### Bước 2: Gỡ bỏ file khỏi cache của Git
Vì file đã lỡ commit nên việc thêm vào `.gitignore` là chưa đủ, em cần gỡ bỏ file ra khỏi bộ nhớ đệm (cache) của Git bằng lệnh `git rm --cached`. Lệnh này giúp Git ngừng theo dõi file nhưng **vẫn giữ lại file vật lý** trên ổ đĩa cứng của máy tính:
```bash
git rm --cached credentials.txt
```
Kết quả hiển thị:
```
rm 'credentials.txt'
```

### Bước 3: Sửa đổi lịch sử commit (Amend)
Cuối cùng, em thêm file `.gitignore` vào staging area và dùng tùy chọn `--amend` để gộp thay đổi mới vào commit trước đó, đồng thời sửa lại tin nhắn commit thành `"up"` cho sạch sẽ (theo đúng quy chuẩn bài tập):
```bash
git add .gitignore
git commit --amend -m "up"
```

## 3. Kết quả kiểm tra
Kiểm tra trạng thái các file không còn bị theo dõi nhầm và lệnh `git log -n 1` hiển thị thông điệp commit đã được sửa thành công:

```bash
git log -n 1
```
**Kết quả hiển thị:**
```
commit 13dfd4f129cebf5fc9715c9502637355bbded8ca (HEAD -> main)
Author: thanh <tranthanh020120016@gmail.com>
Date:   Mon Oct 5 11:59:37 2026 +0700

    up
```
