# LaTeX local với Docker và VS Code

Dự án mẫu biên dịch tài liệu LaTeX trên máy của bạn bằng Docker và XeLaTeX, có hỗ trợ tiếng Việt. Tệp nguồn và PDF nằm trong thư mục dự án; không cần cài TeX Live trực tiếp lên máy.

## Chuẩn bị

- Cài [Docker Desktop](https://www.docker.com/products/docker-desktop/) và khởi động Docker Engine. Trên Linux có thể dùng Docker Engine.
- Cài [VS Code](https://code.visualstudio.com/) và extension [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).
- Cài [Git](https://git-scm.com/) để clone và đồng bộ dự án.
- Kiểm tra `docker version`: cần có cả phần Client và Server. Image TeX Live đầy đủ có dung lượng lớn và cần Internet ở lần tải đầu.

## Bắt đầu

1. Clone repository, mở thư mục dự án bằng **File → Open Folder** trong VS Code và tin cậy workspace nếu bạn tin tưởng nội dung.
2. Chạy `docker pull texlive/texlive:latest` trong terminal. Đợi tải hoàn tất.
3. Mở `main.tex`, nhấn `Ctrl+Alt+B` để biên dịch. Kết quả là `main.pdf` bên cạnh tệp nguồn.
4. Nhấn `Ctrl+Alt+V` để xem PDF trong VS Code. Lưu tệp sau khi sửa; LaTeX Workshop có thể tự biên dịch lại.

Cấu hình nằm trong `.vscode/settings.json`. Nếu tạo dự án mới, sao chép thư mục `.vscode` vào gốc dự án. Công cụ chạy trong Docker và gắn thư mục chứa tệp LaTeX chính; giữ hình và các tệp được include trong thư mục đó. Tag `latest` có thể thay đổi theo thời gian; để tái lập kết quả lâu dài, nhóm nên thống nhất một phiên bản image cụ thể.

## Biên dịch và kiểm thử thủ công

Trong PowerShell, từ thư mục dự án:

```powershell
docker run --rm -v "${PWD}:/workdir" -w /workdir texlive/texlive:latest latexmk -g -xelatex -interaction=nonstopmode -file-line-error main.tex
```

Trong Bash trên Linux/macOS:

```bash
docker run --rm -v "$PWD:/workdir" -w /workdir texlive/texlive:latest latexmk -g -xelatex -interaction=nonstopmode -file-line-error main.tex
```

Kiểm thử thành công khi lệnh trả về mã 0, tạo `main.pdf` và PDF hiển thị đúng dòng tiếng Việt cùng công thức. Cờ `-g` buộc biên dịch lại để kiểm thử. Tệp PDF và các tệp phụ được Git bỏ qua.

## Cộng tác qua GitHub

Chủ repository có thể vào **Settings → Collaborators** để mời người khác. Mỗi người clone, sửa, commit, push và pull thay đổi; dùng nhánh và pull request khi cần review. Git không đồng bộ theo từng ký tự như Overleaf. Không commit mật khẩu, token hay tài liệu riêng tư vào repository.

## Khắc phục sự cố

- **Không kết nối Docker:** mở Docker Desktop, đợi Engine chạy và thử `docker version`.
- **Image chưa có:** chạy lại `docker pull texlive/texlive:latest` và kiểm tra mạng, dung lượng đĩa.
- **Build thất bại:** mở bảng Output → LaTeX Workshop, tìm lỗi đầu tiên; kiểm tra đường dẫn hình và tệp được include. Có thể chạy lệnh thủ công ở trên để đọc log.
- **Không thấy lệnh build:** kiểm tra extension LaTeX Workshop đã cài và mở đúng thư mục chứa `.vscode`.

Hướng dẫn dành cho các coding agent nằm ở [AGENTS.md](AGENTS.md).
