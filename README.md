# DealHot — Web săn deal mỗi ngày

Web tĩnh hiển thị lưới deal ("DEAL HOT HÔM NAY") kiểu danhgiavui.com, kèm **trang quản trị** để cập nhật link tiếp thị và mã giảm giá — sửa trên trang quản trị là tự commit lên GitHub, web live lại sau 1–2 phút.

## Cấu trúc

| File | Mô tả |
|---|---|
| `index.html` | Trang chủ: lưới deal, lọc theo danh mục (`#/<slug>`), ô tìm kiếm, nút copy mã giảm giá |
| `deals.json` | Toàn bộ dữ liệu: `site` (tên/tagline), `categories` (slug → tiêu đề), `deals[]` |
| `admin.html` | Trang quản trị (thêm/sửa/xóa deal, đổi danh mục, đẩy lên GitHub qua API) |
| `gioi-thieu.html` | Trang giới thiệu tĩnh |
| `.nojekyll` | Tắt Jekyll để GitHub Pages phục vụ file nguyên bản |

## Bật GitHub Pages (làm 1 lần)

Repo → **Settings** → **Pages** → Source: **Deploy from a branch** → Branch: **main**, thư mục **/(root)** → **Save**.
Web sẽ live tại `https://<owner>.github.io/dealhot/`.

## Dùng trang quản trị (làm 1 lần)

Mở `https://<owner>.github.io/dealhot/admin.html`:

1. Nhập **owner**, **repo**, **branch** (`main`) và **token** → bấm "Lưu cấu hình".
2. Tạo token: GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token → chỉ chọn repo này → quyền **Contents**: Read and write.
3. Bấm **"Tải dữ liệu từ GitHub"**, sửa deal, rồi bấm **"Lưu lên GitHub"**.

Token chỉ nằm trong localStorage của trình duyệt bạn, không gửi đi đâu ngoài `api.github.com`.

## Trường dữ liệu mỗi deal

- `label`: chữ trên thanh đỏ (vd "Săn Deal Shopee")
- `name`: tên hiện trong ô vuông khi không có ảnh
- `category`: slug danh mục (tự lên menu điều hướng)
- `color`: màu nền ô vuông (vd `#EE4D2D`, hoặc gradient CSS)
- `image`: link ảnh (để trống = ô màu + chữ)
- `url`: link tiếp thị (affiliate)
- `coupon`: mã giảm giá (để trống = không hiện nút copy)
- `order`: thứ tự hiển thị · `active`: true/false · `note`: ghi chú nội bộ
