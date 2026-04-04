# COLEDSK06 - Khóa học Khoa học Dữ liệu với Python

## Mục đích

Đây là repository chứa tài liệu bài giảng (slides PDF + Jupyter notebooks + datasets) của một khóa học về **Khoa học Dữ liệu (Data Science)** sử dụng Python. Mỗi thư mục `weekXX/` tương ứng với một buổi học.

**Mục tiêu sử dụng AI:** Người dùng muốn AI đọc hiểu nội dung các bài giảng rồi **dạy lại** kiến thức từng tuần một cách dễ hiểu.

## Cấu trúc khóa học

### Phần 1: Nền tảng Python (Week 1–6)

| Tuần | Chủ đề | File chính |
|------|--------|------------|
| Week 1 | Giới thiệu Python - Hello World | `hello.ipynb`, `hello.py` |
| Week 2 | Biến, kiểu dữ liệu, phép toán, nhập/xuất | `demo_variable.ipynb`, `demo_operations.ipynb`, `demo_input_output.ipynb` |
| Week 3 | Cấu trúc điều kiện (if/elif/else) và vòng lặp (for, while) | `demo_if.ipynb`, `demo_for.ipynb`, `demo_while.ipynb` |
| Week 4 | Hàm (function) | `demo_function.ipynb`, `auto_vending.py` |
| Week 5 | Cấu trúc dữ liệu: List, Tuple, Set, Dictionary | `demo_list.ipynb`, `demo_tuple.ipynb`, `dem_set.ipynb`, `demo_dictionary.ipynb` |
| Week 6 | Lập trình hướng đối tượng (OOP): Class, kế thừa | `demo_class.ipynb`, `demo_inheritance.ipynb` |

### Phần 2: Xử lý & Phân tích dữ liệu (Week 7–14)

| Tuần | Chủ đề | File chính |
|------|--------|------------|
| Week 7 | Pandas - Xử lý dữ liệu dạng bảng | `demo_pandas.ipynb` |
| Week 8 | Trực quan hóa dữ liệu (Matplotlib, Seaborn) | `demo_vis.ipynb` |
| Week 9 | Thống kê mô tả & khám phá dữ liệu | `xs_mota.ipynb` |
| Week 12 | Kỹ thuật lấy mẫu (Sampling) | `demo_sample.ipynb` |
| Week 13 | Khoảng tin cậy & Kiểm định giả thuyết | `demo_bai13.ipynb` |
| Week 14 | Phân tích tương quan (Correlation) | `demo_corr.ipynb` |

### Phần 3: Machine Learning cổ điển (Week 16–22)

| Tuần | Chủ đề | File chính |
|------|--------|------------|
| Week 16 | Hồi quy tuyến tính (Linear Regression) | `demo_regression.ipynb` |
| Week 17 | Cây quyết định (Decision Tree) | `decisiontree.ipynb` |
| Week 18 | Pruning & Random Forest | `demo_prunning.ipynb` |
| Week 19 | K-Means Clustering | `demo_kmeans.ipynb` |
| Week 20 | Hệ thống gợi ý (Recommendation Systems) | `movie_contentbased.ipynb`, `item_based_cf.ipynb` |
| Week 21-22 | Khai phá luật kết hợp (Apriori, FP-Growth) & TF-IDF | `demo_apriory.ipynb`, `demo_fpgrowth.ipynb`, `demo_tf_idf_cbf.ipynb` |

### Phần 4: Deep Learning & Tổng hợp (Week 23–27)

| Tuần | Chủ đề | File chính |
|------|--------|------------|
| Week 23 | Giới thiệu Neural Network | `demo_activation.ipynb`, `demo_simple_NN.ipynb` |
| Week 24 | Neural Network cho bài toán hồi quy | `demo_nn2.ipynb`, `demo_nn_house.ipynb` |
| Week 25 | Neural Network cho bài toán phân loại | `demo_nn_wine.ipynb` |
| Week 26 | Tiền xử lý dữ liệu (Data Preprocessing) | `demo_pre_process.ipynb` |
| Week 27 | Project tổng hợp: Dự đoán giá nhà | `house_pricing.ipynb` |

## Hướng dẫn cho AI

- Khi người dùng yêu cầu học một tuần cụ thể, hãy **đọc file PDF (slides)** và **notebook (.ipynb)** của tuần đó để nắm nội dung.
- Giải thích kiến thức **bằng tiếng Việt**, dễ hiểu, có ví dụ minh họa từ code trong notebook.
- Nếu người dùng muốn ôn tập, hãy đặt câu hỏi kiểm tra kiến thức.
- Thứ tự học nên theo tuần từ thấp đến cao vì kiến thức có tính kế thừa.

## Git Remote

- Repo này được push lên GitHub tại: `https://github.com/phamngockcdav/datascience_cole`
- Branch chính: `main`
- Khi cần push, chạy: `git push origin main`

## Lưu ý

- Week 10, 11, 15 không có trong repo (có thể là tuần nghỉ hoặc ôn tập).
- Một số tuần có file PDF slides bài giảng, một số chỉ có notebook.
- Dữ liệu mẫu (CSV) đi kèm trong cùng thư mục với notebook.
- File `week20/books/Books.csv` (~70MB) vượt mức khuyến nghị 50MB của GitHub. Nếu cần thêm file lớn hơn 100MB, sử dụng Git LFS.
