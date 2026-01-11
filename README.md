# Phân tích Lịch Giảng (TdyTimetable2026)

Một công cụ trực quan hóa và phân tích lịch giảng dành cho giảng viên — thiết kế ban đầu cho Trường ĐHYD, Đại học Huế. Ứng dụng viết bằng TypeScript + React, dùng Vite để phát triển và build. Mục tiêu: bóc tách dữ liệu lịch từ file HTML xuất ra từ hệ thống, phát hiện xung đột/trùng lịch, hiển thị lịch tuần/kì, và cung cấp các thống kê trực quan.

Phiên bản hiện tại: v0.009 (xem changelog chi tiết trong component AboutView).

---

## Tính năng chính
- Bóc tách dữ liệu lịch từ file HTML xuất từ hệ thống.
- Chế độ xem: Tuần (dọc/ngang), Kì, Tổng quan, Thống kê.
- Tự động phát hiện và đánh dấu xung đột/trùng lịch.
- Thống kê trực quan: biểu đồ phân bố tiết, top giảng đường, bảng tổng hợp theo môn, bảng nhóm lớp chi tiết.
- Tùy chỉnh quy chuẩn thời gian (LT = 45 phút, TH = 60 phút).
- Hỗ trợ export Google Calendar (.ics).
- Giao diện hỗ trợ Dark Mode và tối ưu cho Mobile (sidebar ẩn, nút Menu).

---

## Demo nhanh (public index.html)
Bạn có thể mở file index.html trực tiếp để xem giao diện tĩnh / khung HTML (ứng dụng chính sử dụng importmap để load React từ CDN):
- Raw GitHub: https://raw.githubusercontent.com/Rinaheart/TdyTimetable2026/c93b10975a92618647533b565c01785d6bfc4e78/index.html  
- Public preview (raw.githack): https://raw.githack.com/Rinaheart/TdyTimetable2026/c93b10975a92618647533b565c01785d6bfc4e78/index.html

Lưu ý: để chạy đầy đủ tính năng (TypeScript + logic trong components/services), khuyến nghị chạy qua Vite (npm run dev).

---

## Cài đặt & chạy (local)
Yêu cầu: Node.js

1. Clone repository:
   - git clone https://github.com/Rinaheart/TdyTimetable2026.git
2. Cài đặt dependencies:
   - npm install
3. (Tùy chọn) Tạo `.env.local` và đặt biến `GEMINI_API_KEY` nếu bạn dùng tích hợp API nào đó.
4. Chạy dev server:
   - npm run dev
5. Mở trình duyệt tới địa chỉ mà Vite hiển thị (mặc định: http://localhost:5173)

Scripts có sẵn (package.json):
- npm run dev — chạy Vite dev server  
- npm run build — build cho production  
- npm run preview — preview build production

---

## Cấu trúc chính của repo
- index.html — entry HTML (importmap + Tailwind)
- src / root TSX:
  - App.tsx — entry React (UI container)
  - index.tsx — mount React
- components/ — các view & UI components chính:
  - AboutView.tsx — thông tin & changelog
  - OverviewView.tsx, WeeklyView.tsx, SemesterView.tsx, StatisticsView.tsx
  - UploadZone.tsx, FilterBar.tsx, Header.tsx, Sidebar.tsx, SettingsView.tsx
- services/ — logic xử lý, bóc tách dữ liệu lịch
- constants.tsx, types.ts — cấu hình và kiểu dữ liệu
- vite.config.ts, tsconfig.json, package.json — cấu hình dự án

(Tham khảo mã nguồn trực tiếp trong thư mục components/ để xem chi tiết từng tính năng.)

---

## Ghi chú cho phát triển
- Môi trường dev dùng Vite + React (TypeScript). Một số thư viện (react, react-dom, lucide-react, recharts) có thể được nạp qua importmap trong index.html để preview nhanh mà không cần build — tuy nhiên để sử dụng toàn bộ logic TypeScript, nên chạy thông thường qua Vite.
- Kiểm tra `services/` để hiểu cách bóc tách và parse dữ liệu HTML đầu vào.
- Biến môi trường GEMINI_API_KEY chỉ cần nếu project tích hợp API bên ngoài; nếu không dùng, bỏ qua.

---

## Liên hệ & đóng góp
- Nếu muốn báo lỗi hoặc đóng góp: mở issue hoặc PR trên repository.
- Thông tin tác giả: © 2026 TdyPhan

---

Cảm ơn bạn đã sử dụng TdyTimetable2026 — nếu cần, tôi có thể:
- Đưa file README này lên repository (commit) — nếu bạn muốn, hãy xác nhận và cung cấp branch/commit message.
- Hỗ trợ tạo GitHub Pages hoặc CNAME để public index.html dưới domain tĩnh.
