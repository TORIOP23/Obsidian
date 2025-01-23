[Linux Commands Cheat Sheet - DevNhaX - Viblo](https://viblo.asia/p/linux-commands-cheat-sheet-Rk74axnMVeO#_cac-lenh-ve-networking-7)

### `chmod` - Thay đổi quyền trong file

Các quyền cơ bản trong 1 file
- Read ~ r
- Write ~ w
- Execute ~ x

– Từ bên phải sang ký tự đầu tiên là dấu gạch ngang [-] thì là file, chữ **d** thì là folder
– 3 ký tự tiếp theo tương ứng là quyền đọc, ghi, thực thi của Owner (Người tạo file/folder)
– 3 ký tự tiếp theo nữa tương ứng là quyền đọc, ghi, thực thi của Owner Group (Group của người tạo file/folder)
– 3 kỳ tự cuối cùng tương ứng là quyền đọc, ghi, thực thi của EveryOne (Tất cả các user còn lại)

Các đối tượng tương tác trên 1 file
- u (user)
- g (group)
- o (others)

| #   | Permission              | rwx |
| --- | ----------------------- | --- |
| 7   | read, write and execute | rwx |
| 6   | read and write          | rw- |
| 5   | read and execute        | r-x |
| 4   | read only               | r–  |
| 3   | write and execute       | -wx |
| 2   | write only              | -w- |
| 1   | execute only            | –x  |
| 0   | none                    | —   |

```jsx
chmod (đối tượng) +
chmod u+x (file-name)
// + thêm vào, - loại bỏ
chmod 
```

