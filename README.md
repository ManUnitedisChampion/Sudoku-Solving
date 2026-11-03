# Sudoku Solver: DFS Backtracking vs. MRV Heuristic

Dự án này triển khai và so sánh thuật toán **Tìm kiếm theo chiều sâu (Depth-First Search - DFS)** kết hợp **Backtracking** thuần túy và phiên bản cải tiến sử dụng **Chiến lược chọn ô có ít khả năng nhất (Minimum Remaining Values - MRV Heuristic)** để giải các bài toán Sudoku kích thước **4×4** và **6×6**.

---

## 👨‍💻 Thông Tin Cá Nhân (Student Info)

- **Họ và tên:** Đặng Nguyễn Ngọc Hải(11252770), Nguyễn Bình Minh(11255394), Trần Huy Hoàng(11253240), Nguyễn Gia Hưng (11253367) 
- **Lớp:** AI67A
- **Trường/Khoa:** Khoa Khoa học dữ liệu & Trí tuệ nhân tạo
- **Môn học:** Nhập môn trí tuệ nhân tạo

---

## 📌 Giới Thiệu Bài Toán

Sudoku là một trò chơi giải đố logic điền số:
- Với bảng **$4 \times 4$**: Sử dụng các số từ $1 \rightarrow 4$, gồm 4 vùng con kích thước $2 \times 2$.
- Với bảng **$6 \times 6$**: Sử dụng các số từ $1 \rightarrow 6$, gồm 6 vùng con kích thước $2 \times 3$.

**Quy tắc:** Mỗi dòng, mỗi cột và mỗi vùng con ($n \times m$) phải chứa đầy đủ các chữ số mà không có số nào bị trùng lặp.

---

## 🧠 Thuật Toán Sử Dụng

### 1. DFS + Backtracking Thuần Túy
- Thuật toán duyệt qua các ô trống theo thứ tự lần lượt (từ trên xuống dưới, từ trái sang phải).
- Với mỗi ô trống, thử điền các số hợp lệ từ $1 \rightarrow N$.
- Nếu gặp bế tắc (không thể điền tiếp), thuật toán quay lui (backtrack) lại ô trước đó và thử giá trị khác.

### 2. DFS + MRV Heuristic (Minimum Remaining Values)
- Thay vì chọn ô trống tiếp theo theo thứ tự tuyến tính, MRV ưu tiên chọn ô trống **có ít khả năng điền đúng nhất** (ô có số lượng giá trị hợp lệ còn lại ít nhất).
- **Mục tiêu:** Phát hiện và cắt nhánh bế tắc sớm hơn trên cây tìm kiếm, làm giảm mạnh số bước quay lui (backtrack count) và thời gian thực thi.

---

## 📊 Kết Quả So Sánh Thực Tế (Experimental Results)

Dưới đây là bảng thống kê kết quả chạy thực nghiệm giữa hai phương pháp trên cùng các bộ dữ liệu Sudoku mẫu:

| Thuật Toán | Kích Thước Bảng | Số Nút Duyệt (Nodes) | Số Lần Quay Lui (Backtracks) | Thời Gian Chạy (Execution Time) |
| :--- | :---: | :---: | :---: | :---: |
| **Standard DFS** | $4 \times 4$ | 13 | 1 | ~0.05 - 0.08 ms |
| **DFS + MRV** | $4 \times 4$ | 12 | 0 | ~0.2 - 0.5 ms |
| **Standard DFS** | $6 \times 6$ | 292 | 268 | ~1 - 1.52 ms |
| **DFS + MRV** | $6 \times 6$ | 41 | 17 | ~2.4 - 3.5 ms |

> **Nhận xét:** Chiến lược MRV làm giảm đáng kể số nút cần duyệt và số lần quay lui trên các bảng Sudoku có kích thước lớn hơn ($6 \times 6$).

---

## 🛠️ Cấu Trúc File & Hướng Dẫn Cài Đặt

### Cấu trúc dự án
```text
.
├── SodokuSolver.ipynb   # File Jupyter Notebook chứa mã nguồn và kết quả chạy chi tiết
└── README.md            # Tài liệu hướng dẫn và báo cáo dự án
```

### Yêu cầu môi trường
- Python 3.8+
- Jupyter Notebook / JupyterLab / VS Code (có Python Extension)

### Cách chạy Notebook
1. Mở file `SodokuSolver.ipynb` bằng Jupyter Notebook hoặc VS Code.
2. Chạy toàn bộ các ô lệnh (Run All) để xem kết quả kiểm tra tính hợp lệ của bảng, quá trình giải và chỉ số thời gian/bước duyệt thực tế.