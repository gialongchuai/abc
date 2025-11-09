```
gialo@MSI MINGW64 ~/Desktop/git_test (main)
$ git log --oneline

c79d7c3 (HEAD -> main, origin/main, opq) Merge pull request #3 from gialongchuai/lmn
008a18b (origin/lmn, lmn) resolve 02: test them 5
e4d9132 resolve 01: them 4

gialo@MSI MINGW64 ~/Desktop/git_test (opq)
$ git log --oneline

c79d7c3 (HEAD -> opq, origin/main) Merge pull request #3 from gialongchuai/lmn
008a18b (origin/lmn, lmn) resolve 02: test them 5
e4d9132 resolve 01: them 4

=====

gialo@MSI MINGW64 ~/Desktop/git_test (opq)
$ git log --oneline main

133b833 (main) main them 7

c79d7c3 (HEAD -> opq, origin/main) Merge pull request #3 from gialongchuai/lmn

gialo@MSI MINGW64 ~/Desktop/git_test (opq)
$ git log --oneline 

8f922ca (HEAD -> opq, origin/opq) test them hello world
85f4761 test them 6

c79d7c3 (origin/main) Merge pull request #3 from gialongchuai/lmn  
008a18b (origin/lmn, lmn) resolve 02: test them 5
e4d9132 resolve 01: them 4
```

Rebase từ nhánh `opq` lên đầu `main`, từ lúc tách ra từ `main` để phát triển thì `opq` có 2 commit mới:
```
8f922ca (HEAD -> opq, origin/opq) test them hello world
85f4761 test them 6
```

nên phải xử lý từng `commit 85f4761 -> 8f922ca` nếu có conflict xảy ra khi `main` và `opq` cùng sửa cùng 1 dòng thì phải xử lý còn không thì fast forward thì phải :vvvv
thành log sau:
```
gialo@MSI MINGW64 ~/Desktop/git_test (opq)
$ git log --oneline
796ee29 (HEAD -> opq, origin/opq) test them hello world
62daa42 resolve conflict: test them 6
133b833 (main) main them 7
```
Có thể hiểu là lúc `rebase main` có nghĩa muốn leo lên đầu nhánh khác thì phải giữ, tôn trọng nhánh khác, rồi xét lại mình xem từng có những thay đổi nào (những commit mới) thì phải xử lý từng cái 1 (từ cũ đến commit mới nhất).

Lúc rebase thành công không conflict chú ý nến không thay đổi cùng nhánh main thì nó sẽ fast forward cứ nghĩ an tâm nhưng thật chất đã có thể có sự thay đổi hồi nào không hay
-> nhánh main chú ý để merge vào lúc này nhé !!!!
