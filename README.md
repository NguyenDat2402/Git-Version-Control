# C Programming Language Course

## Variables

## Array

## Decision

## Looping

## Function

## Macro

## Bit Operation

## Memory Management

## Pointer Basic 

## Pointer Advance

## Data Structure

## Algorithms

## Optimization

## Common Defects

## Unit Testing

## Git Version Control
Git là một hệ thống quản lý phiên bản phân tán (Distributed Version Control System).Git sẽ ghi nhớ lại toàn bộ lịch sử thay đổi của source code trong dự án. Bạn sửa file nào, thêm dòng code nào, xóa dòng code nào, bỏ thừa dấu ở đâu... tất cả các hành động đều được Git ghi lại. Qua đó giúp dự án có thể điều tra nguyên nhân gây lỗi hệ thống, tổng hợp code trở nên dễ dàng hơn.

Một số khái niệm liên quan đến GIT:
- Repository: Repository là kho lưu trữ tất cả những thông tin cần thiết để quản lý các sửa đổi và lịch sử của toàn bộ project. Repository của Git được phân thành 2 loại là remote repository và local repository.
+Local Repository: Tất cả các thay đổi đã được commit sẽ được lưu ở local repo cho đến khi chúng được đẩy (push) lên remote repo. Các thay đổi này chỉ tồn tại ở trên local của người dùng.
+Remote Repository: Các thay đổi đã được commit tại local repo sẽ được cập nhật lên remote repo. Lúc này những người làm việc chung cùng repo đó có thể cập nhật/kéo (pull) các thay đổi đó về máy của mình

Tất cả các file ở Local Repo đều ở một trong 2 trạng thái:
- Untracked Files: Các file này dù có thay đổi / thêm / xoá thì git cũng ko quan tâm, vì nó không nằm trong danh sách theo dõi của nó. Khi chúng ta sử dụng lệnh “git status” thì các file này sẽ có title là “Untracked files”.
- Tracked Files: Những files đã được thêm vào danh sách theo dõi của git được gọi là Tracked Files, những file này khi chúng ta thay đổi / thêm / xoá thì git sẽ nhận biết được điều đó và lưu các thay đổi này lại theo yêu cầu của chúng ta.

Trong các Tracked Files được git theo dõi lại có các trạng thái sau:
 + Modified Files: Các file bị THAY ĐỔI
 + Staged Files: Các file bị THAY ĐỔI đã được ĐÁNH DẤU để chuẩn bị commit
 + Unmodified Files: Khi các file đã được ĐÁNH DẤU sau khi được COMMIT sẽ lại trở về trạng thái ko thay đổi. (Do các thay đổi này sau khi được commit sẽ được lưu vào thư mục .git, và chúng ta có thể restore về trạng thái đó bất cứ lúc nào).

**_CÁC LỆNH GIT CƠ BẢN_**
1. _**Lệnh git status**_
```shell
git status
```
Tác dụng: Lệnh git status hiện thị thông tin khác nhau (do thêm mới, xóa đi, sửa đổi các file) giữa các file.

2. _**Lệnh git init**_

Tác dụng: Lệnh **git init** được sử dưng để khởi tạo một kho chứa Git mới (Git Repo) ở local. Sau lệnh này một Repo sẽ xuất hiện ở local và bắt đầu thực thi được các lệnh khác của Git.
```shell
git init
```
3. _**Lệnh git init --bare**_

Khi bạn cần tạo ra một Repo Git mà nó chỉ có chức năng lưu trữ - không có thư mục làm việc thì thực hiện lệnh:
```shell
git init --bare
```
4. _**Lệnh git add**_

Tác dụng: Thêm thay đổi vào stage/index trong thư mục làm việc.
```shell
git add
```
5. _**Lệnh git commit**_

Tác dụng: Lệnh git commit thực hiện lưu vào CSDL Git toàn bộ nội dung chứa trong index (vùng staging) và kèm theo nó là một đoạn text thông tin (log) mô tả sự thay đổi của của commit này so với commit trước. Sau khi commit con trỏ HEAD tự động dịch chuyển đến commit này (Trong nhánh hiện tại).
```shell
git commit -m "Ghi chú về commit"
```
Lệnh trên tạo ra một commit với nội dung lấy từ vùng staging, một điểm trong lịch sử commit được tạo ra với thông tin là dòng thông tin nhập vào. Có thể xem lại lịch sử này bằng lệnh git log
```shell
git log
```
6. _**Lệnh git reset**_

Tác dụng: Khi đã thực hiện commit, commit đó chưa public (chưa đẩy lên Remote Repo bằng lệnh git push) thì bạn có thể hủy (undo) commit đó với hai trường hợp bằng lệnh git reset như sau:
```shell
git reset --soft <commit id>
```


