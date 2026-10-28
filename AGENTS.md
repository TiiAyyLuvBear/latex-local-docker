# Hướng dẫn cho coding agent

- Đọc README.md và xác định hệ điều hành, Docker Engine, VS Code và LaTeX Workshop trước khi thiết lập. Không giả định người dùng đã cài hay khởi động Docker.
- Dùng Docker image `texlive/texlive:latest`, chạy `latexmk -xelatex`; không cài TeX Live trực tiếp trên máy nếu người dùng không yêu cầu. Giữ các tệp nguồn và dữ liệu của người dùng.
- Nếu Docker hoặc VS Code chưa có, giải thích điều kiện tiên quyết và chỉ cài khi môi trường cho phép. Khi cần thao tác tương tác hoặc quyền mà agent không có, báo rõ bước bị chặn.
- Với VS Code, cài `James-Yu.latex-workshop` nếu thiếu, mở thư mục dự án, dùng cấu hình `.vscode/settings.json`. Không ghi đè cấu hình người dùng toàn cục.
- Kiểm thử bằng lệnh Docker phù hợp hệ điều hành trong README. Kiểm tra mã thoát, sự tồn tại của `main.pdf` và nội dung tiếng Việt, công thức trong PDF nếu có công cụ đọc PDF. Báo cáo rõ kết quả và những gì chưa kiểm tra; không tuyên bố thành công chỉ vì image đã tải.
- Khi sửa tài liệu, biên dịch lại tài liệu bị ảnh hưởng; không commit PDF và tệp phụ trừ khi người dùng yêu cầu. Không xóa dữ liệu người dùng. Giữ các thay đổi ngoài phạm vi tác vụ.
- Nếu thêm hoặc chạy mã Python, dùng virtual environment; hỏi người dùng khi không có script kích hoạt phù hợp theo chỉ dẫn của họ. Giao kèm testcase và kết quả kiểm thử trước khi hoàn tất công việc lập trình.
