### 1. Output của git status sau khi tạo 3 file:
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        part1/

nothing added to commit but untracked files present (use "git add" to track)

### 2. Output của git status sau khi stage notes và todo:
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   part1/notes.txt
        new file:   part1/todo.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        part1/draft.md
        status_log.md.txt

### 3. Output của git diff (unstaged):
diff --git a/part1/notes.txt b/part1/notes.txt
index 8d1c8b6..81bac45 100644
--- a/part1/notes.txt
+++ b/part1/notes.txt
@@ -1 +1,5 @@
+1
+1
+2
+3

### 4. Output của git diff --staged:
diff --git a/part1/notes.txt b/part1/notes.txt
index 8d1c8b6..81bac45 100644
--- a/part1/notes.txt
+++ b/part1/notes.txt
@@ -1 +1,5 @@
+1
+1
+2
+3

### 5. Giải thích về Tracked, Untracked và lệnh git commit -a:
- **Tracked file:** Là những file đã được Git theo dõi (đã từng được `git add` hoặc `git commit` trước đó). Ví dụ: `notes.txt`.
- **Untracked file:** Là những file mới tạo, chưa từng được đưa vào Git lần nào. Git không biết đến sự tồn tại của chúng. Ví dụ: `draft.md` ở các bước đầu.
- **Tại sao `git commit -a` hoạt động với file đã tracked:** Tham số `-a` (viết tắt của all) yêu cầu Git tự động quét toàn bộ các **tracked files**, nếu thấy có thay đổi thì tự động `add` và `commit` chúng luôn trong một lệnh.
- **Tại sao nó không tự động thêm file mới:** Vì tham số `-a` được thiết kế để chỉ quan tâm đến các file nằm trong danh sách theo dõi. Các file mới (untracked) cần được người dùng xác nhận rõ ràng bằng lệnh `git add` để tránh việc vô tình commit nhầm các file rác hoặc file hệ thống.

### 6. Sự khác biệt giữa git fetch và git pull:
- **git fetch:** Lệnh này chỉ tải "thông tin" cập nhật từ remote (GitHub) về máy tính để Git nhận biết có sự thay đổi (như báo cáo behind 1 commit). Tuy nhiên, nó **KHÔNG** tự động gộp (merge) sự thay đổi đó vào các file trong Working Directory. Bằng chứng là sau khi chạy `fetch`, file `README.md` trên ổ cứng vẫn chưa có dòng chữ mới.
- **git pull:** Bản chất của `pull` là sự kết hợp của `fetch` và `merge`. Lệnh này không chỉ tải thông tin về mà còn lập tức gộp mã nguồn mới từ remote vào nhánh hiện tại trên máy. Bằng chứng là sau khi chạy `pull`, file `README.md` trên ổ cứng đã xuất hiện ngay dòng chữ vừa được thêm từ GitHub UI.