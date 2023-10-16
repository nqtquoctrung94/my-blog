---
title: Giải Sudoku bằng thuật toán quay lui
date: 2023 Oct 15
categories: [Algorithm, Sudoku]
tags: [algorithm, recursion, sudoku, backtracking]
math: true
excerpt_separator: <!--excerpt-end-->
---

<!--excerpt-start-->
Imma write something about Sudoku here.
<!--excerpt-end-->


## Giới thiệu

- Sudoku là ô chữ số có dạng lưới 9x9 ô
- Mỗi hàng, mỗi cột, và mỗi ô 3x3 nhỏ phải chứa các số từ 1 đến 9 và không có số trùng nhau 
- (thực ra có trùng thì mình cũng không điền đủ các số từ 1 đến 9 được)

## Hiển thị Sudoku trong Python

Trước khi giải thì cần xem xét làm sao để nhập trước. Giả sử chúng ta có [câu đố Sudoku trên trang WebSudoku](https://www.websudoku.com/?level=4&set_id=5364661123) như sau:

![Sudoku Example light](/assets/img/sudoku-solver/sudoku-example-light.png){: .light }
![Sudoku Example dark](/assets/img/sudoku-solver/sudoku-example-dark.png){: .dark }

Thường thì các ô Sudoku sẽ được input ở dạng array 9x9 như sau:

```python
sudoku_grid = [[0, 0, 0, 0, 0, 2, 0, 3, 0],
               [0, 0, 5, 8, 0, 0, 9, 0, 0],
               [9, 0, 0, 0, 0, 5, 0, 0, 0],
               [0, 1, 3, 4, 0, 6, 0, 8, 0],
               [0, 6, 0, 0, 0, 0, 0, 7, 0],
               [0, 8, 0, 5, 0, 1, 6, 4, 0],
               [0, 0, 0, 3, 0, 0, 0, 0, 6],
               [0, 0, 2, 0, 0, 7, 4, 0, 0],
               [0, 7, 0, 6, 0, 0, 0, 0, 0]]
```

Input như vậy thì cũng đã đủ để bắt tay vào giải rồi. Nhưng để dễ nhìn kết quả, chúng ta có thể tạo một hàm hiển thị sudoku đơn giản như sau

```python
def display_sudoku(grid, blank_notation = "-"):
    for row in range(9):

        # In thêm dòng ngăn cách nếu ở các dòng 3, 6
        if row in (3,6):
            print("------+-------+------")

        # In thêm | để chia cột nếu ở các cột 3, 6
        for col in range(9):
            if col in (3,6):
                print("| ", end="")

            # Nếu là số 0, tức là giá trị chưa được điền, thì đổi thành blank_notation tuỳ ý
            number = grid[row][col]
            if number == 0:
                number = blank_notation

            # Viết số trong mảng, thêm khoảng cách " " phía sau
            print(number, end = " ")
        print()

sudoku_grid = [[0, 0, 0, 0, 0, 2, 0, 3, 0],
               [0, 0, 5, 8, 0, 0, 9, 0, 0],
               [9, 0, 0, 0, 0, 5, 0, 0, 0],
               [0, 1, 3, 4, 0, 6, 0, 8, 0],
               [0, 6, 0, 0, 0, 0, 0, 7, 0],
               [0, 8, 0, 5, 0, 1, 6, 4, 0],
               [0, 0, 0, 3, 0, 0, 0, 0, 6],
               [0, 0, 2, 0, 0, 7, 4, 0, 0],
               [0, 7, 0, 6, 0, 0, 0, 0, 0]]
display_sudoku(sudoku_grid, blank_notation=".")
```

Output
```
. . . | . . 2 | . 3 . 
. . 5 | 8 . . | 9 . . 
9 . . | . . 5 | . . . 
------+-------+------
. 1 3 | 4 . 6 | . 8 . 
. 6 . | . . . | . 7 . 
. 8 . | 5 . 1 | 6 4 . 
------+-------+------
. . . | 3 . . | . . 6 
. . 2 | . . 7 | 4 . . 
. 7 . | 6 . . | . . . 
```

Ở đây mình có thể giá trị `blank_notation` để tiện cho việc quan sát. Ta có thể thử tuỳ chỉnh thành các cách ghi khác, tuy nhiên chỉ nên sử dụng 1 ký tự thôi.

Input
```python
display_sudoku(sudoku_grid, blank_notation=0)
```

Output
```
0 0 0 | 0 0 2 | 0 3 0 
0 0 5 | 8 0 0 | 9 0 0 
9 0 0 | 0 0 5 | 0 0 0 
------+-------+------
0 1 3 | 4 0 6 | 0 8 0 
0 6 0 | 0 0 0 | 0 7 0 
0 8 0 | 5 0 1 | 6 4 0 
------+-------+------
0 0 0 | 3 0 0 | 0 0 6 
0 0 2 | 0 0 7 | 4 0 0 
0 7 0 | 6 0 0 | 0 0 0 
```

## Xét điều kiện để điền giá trị

Dựa theo luật chơi của Sudoku, ta có:
- Trong hàng không có giá trị trùng lặp
- Trong cột không có giá trị trùng lặp
- Trong ô 3x3 không có giá trị trùng lặp

Vậy ta có thể viết hàm để kiểm tra 3 điều kiện trên, và trả về `True` nếu có thể điền giá trị vào ô, và `False` nếu đã tồn tại giá trị ở hàng, cột, hoặc ô 3x3 rồi.

```python
def can_input(grid, value, row, col):
    # Kiểm tra xem trong hàng muốn nhập đã có giá trị này chưa
    for i in range(9):
        if grid[row][i] == value:
            return False
        
    # Kiểm tra xem trong cột muốn nhập đã có giá trị này chưa
    for i in range(9):
        if grid[i][col] == value:
            return False

    # Xác định vị trí ô 3x3 nhỏ chứa vị trí muốn điền
    small_row = (row//3)*3
    small_col = (col//3)*3

    # Kiểm tra toàn bộ 9 ô trong mảng 3x3 xem đã có giá trị này chưa
    for i in range(3):
        for j in range(3):
            if grid[small_row + i][small_col + j] == value:
                return False

    # Nếu chưa có ở đâu hết thì có thể điền value
    return True
```

## Giải Sudoku bằng thuật toán quay lui

Hàm quay lui thực ra là một trong những thuật toán brute-force (thử tất cả các biến cho đến khi tìm được kết quả).

Hàm này sẽ:
- Check từ hàng đầu đến cuối, trái qua phải
- Nếu thấy trống thì thử các số từ 1 đến 9 xem có hợp lý không. <br>
    -> Đây chính là lý do chúng ta có hàm `can_input` ở trên để kiểm tra điều kiện.
- Sau khi điền xong, hàm sẽ tiếp tục tiến tới ô tiếp theo và tiếp tục thử. 
    - Nếu không thể tìm được số nào phù hợp cho ô tiếp theo, có nghĩa là các ô trước đó đã điền sai.<br> 
    -> Lúc này hàm sẽ lui lại ô cũ, trả lại các giá trị đã điền, và thử lại với giá trị mới. Đây chính là vì sao hàm được gọi là `Backtracking`, 

Trên trang Wikipedia về [Sudoku solving algorithms](https://en.wikipedia.org/wiki/Sudoku_solving_algorithms) có ảnh gif thể hiện các bước thử số của thuật toán quay lui này.

![Sudoku Example light](/assets/img/sudoku-solver/sudoku-solved-by-bactracking.gif)

Sau đây là code dựa theo video [Python Sudoku Solver](https://www.youtube.com/watch?v=G_UYXzGuqvM) của Computerphile:

```python
def sudoku_solver(grid):
    for row in range(9):
        for col in range(9):

            # Ở đây nếu có ô vẫn chưa điền thì tiếp tujcc thử giá trị
            # Nếu đã điền hết rồi thì phương trình sẽ đi thẳng đến display_sudoku(grid)
            if grid[row][col] == 0:
                
                # Thử từng giá trị từ 1 đến 9
                for value in range(1, 10):
                    if can_input(grid, value, row, col):

                        # Nếu điền được, gọi lại hàm để giải tiếp ô tiếp theo
                        grid[row][col] = value
                        sudoku_solver(grid)

                        # Nếu hàm bên trên bị kẹt, không thể điền tiếp nữa, thì ở đây sẽ trả lại về 0 và thử xét lại với giá trị khác
                        grid[row][col] = 0

                # Trả về rỗng nếu không tìm được giá trị phù hợp.
                # Lúc này hàm sẽ quay ngược lại bước điền giá trị `0`
                return
            
    # Sau khi toàn bộ bảng đã được điền thì hiện ra kết quả
    display_sudoku(grid)
```

Nếu không muốn sử dụng 2 vòng lặp `row` và `col`, ta cũng có thể đưa 2 giá trị này vào phần input của hàm và tăng tương ứng trong mỗi lần chạy.

```python
def sudoku_solver2(grid, row=0, col=0):

    if col == 9:
        if row == 8:
            # Nếu đã đến cột cuối, dòng cuối rồi thì là đã giải xong, in ra sudoku
            display_sudoku(grid)
            return
        
        # Nếu chưa đến dòng cuối, thì tăng số dòng +1, chuyển cột về 0
        sudoku_solver2(grid, row+1, 0)
    else:
        if grid[row][col] == 0:

            # Thử từng giá trị từ 1 đến 9
            for value in range(1, 10):
                if can_input(grid, value, row, col):

                    # Nếu điền được, gọi lại hàm để giải tiếp ô ở cột tiếp theo
                    grid[row][col] = value
                    sudoku_solver2(grid, row, col+1)

                    # Nếu hàm bên trên bị kẹt, không thể điền tiếp nữa, thì ở đây sẽ trả lại về 0 và thử xét lại với giá trị khác
                    grid[row][col] = 0

        # Nếu ô hiện tại không trống thì qua cột tiếp theo
        else:
            sudoku_solver2(grid, row, col+1)
```

## Trường hợp tệ nhất của Hàm quay lui

Chúng ta cũng thâ


## Các nguồn tham khảo
- Geeks for Geeks:
    - [Algorithm to Solve Sudoku | Sudoku Solver](https://www.geeksforgeeks.org/sudoku-backtracking-7/)
- Wikipedia:
    - [Sudoku solving algorithms](https://en.wikipedia.org/wiki/Sudoku_solving_algorithms)
- Youtube channels:
    - Computerphile: [Python Sudoku Solver](https://www.youtube.com/watch?v=G_UYXzGuqvM)
    - Games Computers Play: [Sudoku Solver in Python (using 10 different solving strategies)](https://www.youtube.com/watch?v=ek8LDDt2M44)
    - Games Computers Play: [Sudoku solvers: backtracking or logic?](https://www.youtube.com/watch?v=8kKlEnBxa5M)

Papers:
- A Hybrid Approach for the Sudoku problem: Using
Constraint Programming in Iterated Local Search


Hình ảnh được tạo bằng công cụ [Figma](https://www.figma.com/) <br>
Ảnh động được tạo bằng công cụ [ezgif.com](https://ezgif.com/)