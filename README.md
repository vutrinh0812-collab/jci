# 🏥 JCI Quiz – Sổ Tay Câu Hỏi JCI Phiên Bản 8

Web app học quiz tiêu chuẩn JCI cho nhân viên y tế. **270 câu hỏi** trên **21 chủ đề**.

---

## 🚀 Hướng dẫn Deploy lên Vercel (3 cách)

### ⭐ Cách 1: Drag & Drop (Dễ nhất – Không cần tài khoản GitHub)

1. Vào https://vercel.com/signup → đăng ký bằng email (hoặc Google)
2. Sau khi đăng nhập, vào https://vercel.com/new
3. Cuộn xuống dưới, tìm phần **"Deploy a third-party Git repository"** → bấm vào ô **"Browse"** hoặc kéo thả thư mục
4. **Nén toàn bộ thư mục này thành file .zip** (chuột phải → Compress)
5. Kéo file `.zip` vào trang Vercel
6. Bấm **"Deploy"** → đợi 30 giây
7. Vercel sẽ cấp cho bạn một URL kiểu `https://jci-quiz-xxx.vercel.app`
8. Mở URL đó trên iPhone/Android → chạy được!

### Cách 2: GitHub + Vercel (Tốt nhất để update sau này)

1. **Tạo GitHub repository:**
   - Vào https://github.com/new → tạo repo mới (đặt tên `jci-quiz` hoặc tên gì cũng được)
   - Upload toàn bộ file trong thư mục này vào repo
2. **Kết nối với Vercel:**
   - Vào https://vercel.com/new
   - Bấm **"Import Git Repository"** → chọn repo vừa tạo
   - Vercel tự nhận diện là static site → bấm **"Deploy"**
3. **Update câu hỏi sau này:** chỉnh `questions.json` trên GitHub → Vercel tự deploy lại

### Cách 3: Vercel CLI (Cho người biết dòng lệnh)

```bash
# Cài Vercel CLI
npm install -g vercel

# Vào thư mục project
cd jci-quiz-vercel

# Deploy
vercel

# Theo hướng dẫn (login, chọn scope, đặt tên project)
# Deploy production
vercel --prod
```

---

## 📱 Sau khi deploy: Cài vào màn hình iPhone/Android

App này có **PWA manifest**, nhân viên có thể "Cài đặt" như app thật:

### Trên iPhone (Safari):
1. Mở URL trên Safari
2. Bấm nút **Chia sẻ** (hình mũi tên đi lên) ở dưới
3. Cuộn xuống → bấm **"Thêm vào Màn hình chính"**
4. Đặt tên (mặc định "JCI Quiz") → bấm **"Thêm"**
5. App icon xuất hiện trên home screen như app thường ✓

### Trên Android (Chrome):
1. Mở URL trên Chrome
2. Bấm menu **⋮** (3 chấm)
3. Bấm **"Cài đặt ứng dụng"** hoặc **"Thêm vào màn hình chính"**

---

## 📂 Cấu trúc Project

```
jci-quiz-vercel/
├── index.html         ← App chính
├── questions.json     ← Bộ câu hỏi (270 câu, 21 chủ đề)
├── manifest.json      ← Cấu hình PWA (icon, theme)
├── vercel.json        ← Cấu hình deploy Vercel
└── README.md          ← File này
```

---

## ✏️ Cập nhật câu hỏi

1. Mở file `questions.json` bằng bất kỳ text editor nào (VS Code, Notepad++, hoặc Notepad)
2. Thêm/sửa câu hỏi theo cấu trúc có sẵn
3. Save và upload lại lên Vercel (hoặc push lên GitHub nếu dùng Cách 2)

### Schema JSON:

```json
{
  "title": "...",
  "version": "...",
  "topics": [
    {
      "id": "tên_chủ_đề",
      "name": "Tên hiển thị",
      "icon": "🏥",
      "questions": [
        {
          "id": "q_unique_id",
          "type": "mcq | true_false | fill_blank | matching",
          "question": "Nội dung câu hỏi?",
          "options": ["A. ...", "B. ...", "C. ...", "D. ..."],
          "answer": "A",
          "explanation": "Giải thích chi tiết...",
          "reference": "JCI Standard XYZ"
        }
      ]
    }
  ]
}
```

---

## 🆘 Khắc phục lỗi

| Vấn đề | Cách xử lý |
|---|---|
| URL Vercel không mở được | Đợi 1-2 phút sau deploy, hoặc thử mở incognito |
| Hiển thị "Không thể tải dữ liệu" | Kiểm tra `questions.json` có nằm cùng thư mục `index.html` không |
| iPhone vẫn không load | Cập nhật iOS lên 12+ và dùng Safari (không phải app Chrome) |
| Câu hỏi không cập nhật | Reload trang (Ctrl+F5 hoặc kéo xuống refresh trên mobile) |

---

## 📊 Thống kê

- **270 câu hỏi** từ tài liệu FAQ JCI BV TMHH 2026
- **21 chủ đề** chuyên ngành
- **25 câu KHÓ** (9.3%) đánh dấu `[KHÓ]` để thử thách
- **4 dạng câu**: Trắc nghiệm 4 đáp án, Đúng/Sai, Điền chỗ trống, Ghép cặp
- **Chế độ Random 30**: 30 câu ngẫu nhiên từ tất cả chủ đề

---

## 📄 License

Tài liệu nội bộ Bệnh viện Truyền máu Huyết học TPHCM – Chỉ sử dụng trong mục đích đào tạo nội bộ.
