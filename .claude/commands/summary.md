Tạo bản tóm tắt nhanh kiến thức từ tuần $ARGUMENTS.

## Quy trình

### Bước 1: Đọc tài liệu
- Nếu $ARGUMENTS chứa dấu "-" (ví dụ: "16-20") → đọc từ tuần 16 đến 20
- Nếu $ARGUMENTS là 1 số (ví dụ: "16") → chỉ tóm tắt tuần 16
- Ưu tiên đọc file `baigiang_week*.ipynb` hoặc `baigiang_week*.md`
- Nếu chưa có, đọc notebook gốc và PDF

### Bước 2: Tạo bản tóm tắt (file markdown)

Tạo file tóm tắt **trong thư mục của tuần đó**:
- 1 tuần (ví dụ 17) → `week17/tomtat_week17.md`
- Nhiều tuần (ví dụ 16-17) → mỗi tuần 1 file: `week16/tomtat_week16.md`, `week17/tomtat_week17.md`

Cấu trúc tóm tắt — **ngắn gọn, dễ lướt mắt**:

#### 1. Bảng tổng hợp (1 dòng/tuần)
| Tuần | Chủ đề | Ý chính | Code quan trọng |
|------|--------|---------|-----------------|
| 16 | Hồi quy | Y = aX + b, R², Logistic | `LinearRegression().fit()` |

#### 2. Công thức & Khái niệm chốt
- Liệt kê dạng bullet, mỗi cái 1-2 dòng MAX
- Công thức dùng ký hiệu đơn giản, kèm 1 câu giải thích
- Ví dụ: `R² = 0.88` → mô hình giải thích 88% dữ liệu

#### 3. Code cheat sheet
- Các lệnh quan trọng nhất, dạng snippet ngắn
- Chỉ code CỐT LÕI, không giải thích dài

#### 4. Sơ đồ kiến thức (Mermaid)
- Dùng mermaid flowchart thể hiện mối quan hệ giữa các khái niệm/tuần
- Giữ đơn giản, tối đa 10-15 node

#### 5. Checklist tự đánh giá
- [ ] Tôi hiểu [khái niệm A]
- [ ] Tôi biết khi nào dùng [phương pháp B]
- [ ] Tôi có thể viết code [tác vụ C]

### Bước 3: Trình bày tóm tắt trong chat
- Hiển thị nội dung tóm tắt trực tiếp trong chat
- Thông báo file đã lưu ở đâu

## Lưu ý
- Tiếng Việt, **cực kỳ ngắn gọn** — mỗi ý tối đa 1-2 câu
- KHÔNG giải thích dài dòng — đây là tóm tắt, không phải bài giảng
- Ưu tiên: bảng > bullet > đoạn văn
- Format markdown vì chỉ cần đọc lướt, không cần chạy code
