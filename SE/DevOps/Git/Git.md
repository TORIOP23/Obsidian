[How To Work With Multiple Github Accounts on your PC](https://gist.github.com/rahularity/86da20fe3858e6b311de068201d279e3)

[GitHub.com Help Documentation](https://docs.github.com/en)
## Mở đầu
- Ra đời 2005
- Tác giả Linus Torvald, hỗ trợ viết Linux kernel
- Toàn bộ code và history được lưu trên máy người dùng
- 3 khái niệm quan trọng: repo, commit, branch
    - Repo: dự án 1 source chứa toàn bộ dự án. Gồm 2 loại local và remote
    - Commit: thay đổi code sẽ là 1 commit, xem được ai xóa ai thêm
    - Branch: 1 nhánh mới
- Github mở rộng cho Git giúp Git có khả năng code chung
## Định nghĩa

- Mỗi file trong Git được quản lý với 3 trạng thái : _**committed, modified, staged**_
    - **committed** : các file của bạn đã được Git lưu trữ thành công
    - **modified** : các file đã bị thay đổi nhưng chưa commit
    - **stage** : đánh dấu sẽ commit phiên bản hiện tại của 1 tập tin đã modified trong lần commit sắp tới
    ![[git-2.png]]
    
    - Staging area: là khu vực để theo dõi các cái file được thực hiện ở các lần commit tiếp theo: sử dụng: git add (tên file)
		- ![[git-3.png]]
        - Sau khi add thì file sẽ tới Staging Area

## Các lệnh cơ bản

```java
git init                  // tạo repository (quản lý lịch sử)
git clone <url>           // lấy từ trên mạng về
git pull                  // đồng bộ từ trên mạng về máy
git add và git add .      // thêm commit, git add . để add toàn bộ
git commit -m "message"   // nên gõ thêm 1 message
git push                  // đồng bộ từ máy lên mạng
git log                   **//** xem lại lịch sử
git status                // sẽ chỉ ra untracked file
```

```cpp
git remote
git restore  - - staged (tên file) đừa từ staged về khu vực làm việc
git merge (tên branch): đưa những thay đổi trên branch lên main
git reset —soft (hard +(tên): xóa commit (đưa vào staging), soft xóa commit cuối cùng, hard xóa hẳn commit
git remote show origin // xem git của bạn đang hướng đến repository nào
```

```java
git branch (new_branch_name) // creat new branches
git checkout (other_branch) // switch branch
git branch -m (new_name) // Renaming your local head Branches
git branch -m (old_name) (new_name) // Renaming any local branch
git branch // see what branch we have
git branch -r   // show all branch on remote

git branch --delete <branch_name> // Xoá một branch ở phía local
git branch --delete --remotes <remote_name>/<branch_name> // Xoá một branch remote lưu ở local
git push <remote_name> --delete <branch_name> // Xoá một branch ở phía remote

git push <remote_name> <branch_name>  // Push một branch ở local lên remote, 2 branch cùng tên
git push <remote_name> <local_branch>:<remote_branch> // 2 branch khác tên

git push -u origin <local branch>
git branch main -u origin/toriop
```

- Git stash được sử dụng khi muốn lưu lại các thay đổi nhưng chưa commit, thường rất hữu dụng khi bạn muốn đổi sang 1 branch khác mà lại đang làm dở ở branch hiện tại.

```java
git stash // Lưu toàn bộ nội dung công việc đang làm dở
git stash list // Xem danh sách stash
git stash pop // Apply stash gần nhất và xóa stash đó
git stash apply stash@{<index>} // Apply stash
git stash show stash@{<index>} // Xem nội dung stash
git stash drop stash@{<index>} // Xóa stash
git stash clear  // Xóa toàn bộ stash
```

```tsx
git config --list
git config --list --local
git config user.name "your name"
git config user.email "your email"
```

Best practice for commit message

```bash
feat – a new feature is introduced with the changes
fix – a bug fix has occurred
chore – changes that do not relate to a fix or feature and don't modify src or test files (for example updating dependencies)
refactor – refactored code that neither fixes a bug nor adds a feature
docs – updates to documentation such as a the README or other markdown files
style – changes that do not affect the meaning of the code, likely related to code formatting such as white-space, missing semi-colons, and so on.
test – including new or correcting previous tests
perf – performance improvements
ci – continuous integration related
build – changes that affect the build system or external dependencies
revert – reverts a previous commit
```

## [[Lisence]]
[Github Licenses: Những điều cần biết khi chọn license cho repo Github](https://viblo.asia/p/github-licenses-nhung-dieu-can-biet-khi-chon-license-cho-repo-github-yZjJYgZ0VOE)