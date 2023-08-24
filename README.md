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
Lệnh trên tạo ra một commit với nội dung lấy từ vùng staging, một điểm trong lịch sử commit được tạo ra với thông tin là dòng thông tin nhập vào. Có thể xem lại lịch sử này bằng lệnh git log,
Mặc đinh thi hành git log nó liệt kê các commit theo thứ tự từ mới nhất đến cũ nhất, mỗi commit có các thông tin gồm: mã hash của commit, dòng thông báo, người tạo commit và ngày tạo commit.
```shell
git log
```
Một số thiết lập hay dùng với git log:
+Nếu chỉ muốn hiện thị một số commit log. Ví dụ hiện thị log của 2 commit cuối thì cho thêm -2 vào lệnh:
```shell
git log -2
```
+Nếu muốn hiện thị chi tiết các thay đổi của từng commit thì thêm vào tham số -p
```shell
git log -p -2
```
+Nếu hiện thị thống kế gọn hơn về sự thay đổi thì dùng tham số --stat, hoặc dạng ngắn gọn hơn là --shortstat:
```shell
git log --stat -5
```
+Nếu hiển thị định dạng thông tin chung về commit (mã hash, dòng thông tin) trên một dòng thì dùng tham số --oneline:
```shell
git log --oneline
git log --stat -10 --oneline
```
6. _**Lệnh git reset**_

Tác dụng: Khi đã thực hiện commit, commit đó chưa public (chưa đẩy lên Remote Repo bằng lệnh git push) thì bạn có thể hủy (undo) commit đó với hai trường hợp bằng lệnh git reset như sau:
```shell
git reset --soft <commit id>
```
Câu lệnh này sẽ di chuyển HEAD về vị trí commit reset. Trạng thái của Stage và tất cả sự thay đổi của file đều được giữ nguyên.
```shell
git reset --hard <commit id>
```
Câu lệnh này sẽ di chuyển HEAD về vị trí commit reset và loại bỏ tất cả sự thay đổi của file.

7. _**Lệnh git diff**_

Tác dụng: Hiển thị thông tin thay đổi giữa thư mục làm việc và vùng index (staging) hoặc với commit cũ, thông tin thay đổi giữa index(staging) và commit, thông tin thay đổi giữa hai nhánh.

Vài trường hợp sử dụng của **git diff**:

+Kiểm tra sự thay đổi thư mục làm việc:
```shell
git diff
```
+Kiểm tra sự thay đổi của index (staging) với commit cuối:
```shell
git diff --staged
```
+Kiểm tra thay đổi giữa hai commit:
```shell
git diff hash-commit1 hash-commit2
```
+Kiểm tra sự thay đổi của hai nhánh:
```shell
git diff branch1 branch2
```
8. _**Lệnh git clone**_

Tác dụng: Lệnh **git clone** để sao chép, copy một Git Repo về máy local. Một số trường hợp sử dụng:
- Copy một Repo từ máy Remote về Local
- Copy một Repo từ thư mục này sang một thư mục khác:
Trên máy của bạn có một Git Repo ở đường dẫn path-git, bạn có thể copy sang vị trí khác bằng lệnh:
```shell
git clone path-git
```
Có thể chỉ rõ thư mục cần copy về thay vì tại thư mục hiện tại:
```shell
git clone path-git path-des
```
- Copy một Repo từ một Url (https) ví dụ GitHub:
```shell
git clone url-repo
```
Mặc định nó sẽ sao chép về nhánh hoạt động, để xem tất cả các nhánh có trên Remote dùng lệnh:
```shell
git branch --remote
```
Khi copy Repo bình thường thì nó tự động tạo ra kết nối đến remote Repo để có thể Push. Kết nối này có tên mặc định **origin**, sau khi copy thì có thể kiểm tra bằng:
```shell
git remote -v
```
9. _**Lệnh git checkout**_

Tác dụng: Lệnh git checkout được dùng để chuyển nhánh hoặc để phục hồi file trong thư mục làm việc từ một commit trước đây.
Sử dụng để chuyển nhánh:
```shell
git checkout <branch name>
```
Sử dụng để trở về một commit có mã HASH nào đó bằng lệnh:
```shell
git checkout <HASH>
```
10. _**Lệnh git branch**_

Tác dụng: Dùng để thao tác với các nhánh.

+Dùng để kiểm tra branch hiện tại:
```shell
git branch
```
+Để tạo mới một branch:
```shell
git branch <name branch>
```
+Để chuyển và tạo mới:
```shell
git checkout -b <name_branch>
```
11. _**Lệnh git merge**_

Tác dụng: Lệnh git merge sử dụng để gộp nhánh, gộp nhánh này vào nhánh khác.
```shell
git merge <new_branch>
```
12. _**Lệnh git rebase**_

Tác dụng: Lệnh **git rebase** gộp các commit từ nhánh này vào nhánh khác, bằng cách xây dựng lại các commit base kế thừa từ nhánh khác và viết lại lịch sử commit sau các commit cơ sở mới.
Ví dụ, để gộp nhánh <branch_name> vào master, đứng ở master thực hiện lệnh:
```shell
git rebase <branch_name>
```
13. _**Lệnh git push**_

Tác dụng: Thực hiện lệnh **git push** để tạo upstream, đẩy dữ liệu từ local repo đến remote repo, push các nhánh, xóa các nhánh của remote. Lệnh git push được sử dụng để đẩy các commit mới ở máy trạm (local repo) lên server (remote repo). Nguồn để đẩy lên là nhánh mà con trỏ HEAD đang trỏ tới (nhánh làm việc).

Sử dụng **git push**:

+Đẩy lên server lần đầu tiên:
Nếu là lần đầu tiên đẩy Local Repo lên Remote Repo mới khởi tạo thì cần tạo ra một theo dõi kết nối, upstream giữa local và remote, vậy hãy dùng tham số -u. Ví dụ đẩy lên remote có tên origin và tạo upstream cho nhánh master
```shell
git push -u origin master
```
+Đẩy lên server:
Sau khi có upstream, mỗi lần cần đẩy dữ liệu lên remote của nhánh master, chỉ việc thực hiện lệnh:
```shell
git push
```
+Đẩy một nhánh cụ thể, ví dụ đẩy nhánh beta lên remote có tê origin:
```shell
git push origin beta
```
+Đẩy lên server tất cả các nhánh:
Đẩy tất cả các nhánh ở local lên server có tên origin:
```shell
git push origin --all
```
+Xóa một nhánh trên remote
```shell

git push origin --delete beta
```
+Ghi đè nhánh với --force
Có thể ghi đè toàn bộ một nhánh ở remote bởi một nhánh ở master, dùng lệnh này cận thận. Ví dụ, ghi đè toàn nhánh master ở remote, giống với master của local:
```shell
git push --force origin master
```
14. _**Lệnh git fetch**_ và _**Lệnh git pull**_

Tác dụng: Lệnh git pull và git fetch được dùng để cập nhật dữ liệu mới từ kho chứa ở remote về kho chứa local. Về bản chất, **Git Pull** chính là sự kết hợp của 2 lệnh **Git Fetch** và **Git Merge**. Gai đoạn đầu, **Git Pull** sẽ thực thi lệnh **Git Fetch** ở phạm vi nhánh cục bộ mà HEAD được trỏ đến. Khi dữ liệu được tải xuống, **Git Pull** sẽ bắt đầu quy trình hợp nhất như **Git Merge**. Một merge commit mới sẽ được tạo và HEAD cũng được cập nhật để trỏ đến merge commit đó.

Câu lệnh Git Pull dùng để đồng bộ Remote repository vào Local repository thường có cấu trúc sau:
```shell
git pull origin branch
```
Trong đó, origin là tên Remote repository và branch là nhánh muốn đồng bộ.

Ví dụ, để đồng bộ master branch từ Remote repository vào Local repository, chúng ta sẽ dùng lệnh:
```shell
git pull origin master
```
Kho chứa của bạn tên origin, tải về tất cả thông tin của nó từ remote:
```shell
git fetch origin hoặc git fetch --all
```
Tải thông tin của một nhánh cụ thể, ví dụ master của remote origin:
```shell
git fetch origin master
```
