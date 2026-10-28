---
name: latex-docker
description: Dùng khi thiết lập, kiểm tra hoặc khắc phục môi trường biên dịch LaTeX local bằng Docker và VS Code.
---

# LaTeX local với Docker

Thực hiện yêu cầu của người dùng trong thư mục dự án được chỉ định. Đọc `AGENTS.md` và `README.md` của dự án này nếu có; ưu tiên cấu hình và tệp hiện có của người dùng.

1. Kiểm tra hệ điều hành, `docker version` (cả Client và Server), VS Code và extension `James-Yu.latex-workshop`. Nếu thiếu điều kiện tiên quyết hoặc Docker Engine chưa chạy, nêu chính xác bước cần thực hiện; không coi việc có Docker CLI là đủ.
2. Dùng image `texlive/texlive:latest` và `latexmk -xelatex` theo hướng dẫn trong README, trừ khi dự án hoặc người dùng chỉ định phiên bản khác. Tải image khi cần; không cài TeX Live trực tiếp nếu không được yêu cầu.
3. Với VS Code, cài LaTeX Workshop nếu thiếu và thiết lập cấu hình tại workspace. Không ghi đè cấu hình toàn cục hay tệp có sẵn mà chưa kiểm tra. Với thiết lập Docker tích hợp của LaTeX Workshop, dùng lệnh `latexmk`, đặt thư mục làm việc là thư mục tệp gốc và truyền tên tệp tương đối trong container.
4. Biên dịch tài liệu mẫu hoặc tài liệu người dùng chọn. Kiểm tra mã thoát và PDF được tạo; nếu có thể, kiểm tra tiếng Việt và công thức hiển thị đúng. Khi thất bại, đọc log và báo bước nào bị chặn. Không khẳng định PDF hiển thị đúng nếu chưa kiểm tra.
5. Báo lại lệnh kiểm thử, kết quả, đường dẫn PDF và các giới hạn. Giữ nguyên dữ liệu của người dùng; không tự ý đưa tệp cá nhân lên repository.
