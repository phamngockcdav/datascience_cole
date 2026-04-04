# Bài Giảng Tuần 16: Hồi Quy (Regression)

---

## 1. Tổng quan

### Hồi quy là gì?

**Hồi quy (Regression)** là một kỹ thuật trong Machine Learning giúp ta **dự đoán một con số** dựa trên các thông tin đã biết.

**Ví dụ đời thường:**
- Bạn học **10 tiếng** cho kỳ thi → điểm sẽ khoảng **bao nhiêu**?
- Chi **50 triệu** cho quảng cáo → doanh số bán hàng sẽ **bao nhiêu**?
- Một căn nhà có **3 phòng ngủ, diện tích 80m²** → giá sẽ **bao nhiêu**?

> **Nói đơn giản:** Hồi quy giống như việc bạn nhìn vào dữ liệu quá khứ để "đoán" tương lai. Giống như bạn thấy bạn mình học 5 tiếng được 50 điểm, học 8 tiếng được 80 điểm → bạn "đoán" học 10 tiếng sẽ được khoảng 100 điểm.

### Tại sao cần học hồi quy?

Hồi quy là **nền tảng** của Machine Learning. Hầu hết các bài toán dự đoán đều bắt đầu từ đây. Trong khóa học này, tuần 16 là bước đầu tiên bạn bước vào thế giới Machine Learning!

---

## 2. Lý thuyết cốt lõi

### 2.1. Hồi quy tuyến tính đơn (Simple Linear Regression)

#### Ý tưởng

Hãy tưởng tượng bạn vẽ các điểm trên giấy (trục X là số giờ học, trục Y là điểm thi). Hồi quy tuyến tính là **vẽ một đường thẳng** đi qua các điểm đó sao cho đường thẳng nằm "gần nhất" với tất cả các điểm.

```
Điểm thi (Y)
100 |                    *  /
 80 |               *  /
 60 |          *  /
 40 |     *  /
 20 |  * /
  0 |/___________________
    0   5   10  15  20
         Giờ học (X)
```

#### Công thức

```
Y = a × X + b
```

Trong đó:
- **Y** = giá trị cần dự đoán (ví dụ: điểm thi)
- **X** = thông tin đầu vào (ví dụ: số giờ học)
- **a** = **hệ số góc** (slope) → cho biết X tăng 1 đơn vị thì Y tăng bao nhiêu
- **b** = **hệ số chặn** (intercept) → giá trị của Y khi X = 0

**Ví dụ cụ thể từ notebook:**

Trong bài, mô hình học được: `a = 5.06`, `b = -0.13`

→ Công thức: **Điểm = 5.06 × Giờ_học - 0.13**

Nghĩa là:
- Mỗi giờ học thêm → điểm tăng khoảng **5 điểm**
- Học 10 giờ → Điểm ≈ 5.06 × 10 - 0.13 ≈ **50.5 điểm**
- Học 15 giờ → Điểm ≈ 5.06 × 15 - 0.13 ≈ **75.8 điểm**

#### Máy tính "học" như thế nào?

Máy tính tìm a và b sao cho **tổng sai số** giữa điểm dự đoán và điểm thực tế là **nhỏ nhất**. Phương pháp này gọi là **Bình phương tối thiểu (Least Squares)**.

Hãy tưởng tượng: bạn kéo một sợi dây thun qua các điểm trên giấy. Sợi dây tự nhiên sẽ nằm ở vị trí mà tổng khoảng cách đến tất cả các điểm là nhỏ nhất → đó chính là đường hồi quy!

---

### 2.2. Hồi quy tuyến tính bội (Multiple Linear Regression)

#### Ý tưởng

Trong thực tế, kết quả thường phụ thuộc vào **nhiều yếu tố**, không chỉ một. Ví dụ:

> Doanh số bán hàng phụ thuộc vào: chi phí **quảng cáo** + chi phí **PR** + chi phí **online marketing**

#### Công thức

```
Y = a₁×X₁ + a₂×X₂ + ... + aₙ×Xₙ + b
```

**Ví dụ từ notebook:**

```
Doanh_So = 2.20 × PR + 0.68 × Online + 80.67 × High + ... + b
```

Mỗi hệ số a cho biết **mức đóng góp** của từng yếu tố vào kết quả.

#### Xử lý biến phân loại (Categorical Variables)

Trong dữ liệu `data_multiple_reg.csv`, cột `Quang_Cao` có giá trị dạng chữ: "High", "Low", "Medium-High", "Medium-Low". Máy tính không hiểu chữ, nên ta cần **mã hóa** thành số.

**Kỹ thuật One-Hot Encoding:**

| Quang_Cao | → High | Low | Medium-High | Medium-Low |
|-----------|--------|-----|-------------|------------|
| High      | 1      | 0   | 0           | 0          |
| Low       | 0      | 1   | 0           | 0          |
| Medium-High | 0    | 0   | 1           | 0          |

Giống như: thay vì nói "tôi thích màu đỏ", bạn điền vào bảng khảo sát:
- Đỏ: ✓ | Xanh: ✗ | Vàng: ✗

---

### 2.3. Hồi quy Logistic (Logistic Regression)

#### Ý tưởng

Khác với hồi quy tuyến tính (dự đoán con số), hồi quy logistic dự đoán **phân loại** — thường là **Có/Không**, **Tốt/Xấu**, **0/1**.

**Ví dụ đời thường:**
- Khách hàng đánh giá dịch vụ xe: **Tốt** hay **Xấu**?
- Email này là **spam** hay **không spam**?
- Sinh viên có **đậu** hay **rớt**?

#### Tại sao không dùng hồi quy tuyến tính?

Hồi quy tuyến tính cho ra số bất kỳ (-∞ đến +∞), nhưng ta cần kết quả nằm trong **0 đến 1** (xác suất). Hồi quy logistic dùng **hàm Sigmoid** để "ép" kết quả vào khoảng 0-1.

```
Xác suất
1.0 |          ___________
    |        /
0.5 |------/-------------
    |    /
0.0 |___/
    |________________________
           Giá trị đầu vào
```

- Nếu xác suất > 0.5 → Dự đoán: **Tốt** (1)
- Nếu xác suất ≤ 0.5 → Dự đoán: **Xấu** (0)

#### Ví dụ từ notebook:

Dữ liệu `data_logistic_reg.csv` dự đoán đánh giá khách hàng (Tốt/Xấu) dựa trên:
- **Chat_Luong_Tai_Xe** (chất lượng tài xế, thang điểm 1-5)
- **Thoi_Gian_vs_Du_Kien** (thời gian so với dự kiến)

---

### 2.4. Đánh giá mô hình

Làm sao biết mô hình dự đoán **tốt hay dở**? Ta dùng các chỉ số đánh giá.

#### Cho hồi quy tuyến tính:

| Chỉ số | Ý nghĩa | Giá trị tốt |
|--------|----------|-------------|
| **R² (R-squared)** | Mô hình giải thích được bao nhiêu % sự biến thiên của dữ liệu | Càng gần **1** càng tốt |
| **MSE (Mean Squared Error)** | Trung bình bình phương sai số | Càng **nhỏ** càng tốt |

**Ví dụ:** R² = 0.88 nghĩa là mô hình giải thích được **88%** sự thay đổi của điểm thi dựa trên số giờ học. 12% còn lại do các yếu tố khác (sức khỏe, tâm trạng, độ khó đề...).

#### Cho hồi quy logistic:

| Chỉ số | Ý nghĩa đơn giản |
|--------|-------------------|
| **Accuracy** | Tổng thể, mô hình đúng bao nhiêu %? |
| **Precision** | Trong những cái mô hình nói "Tốt" → thực sự tốt bao nhiêu %? |
| **Recall** | Trong tất cả cái thực sự "Tốt" → mô hình tìm ra được bao nhiêu %? |
| **F1-Score** | Trung bình hài hòa của Precision và Recall |

**Ví dụ từ notebook:** Accuracy = 0.80 → mô hình đoán đúng **80%** trường hợp.

---

### 2.5. Chia dữ liệu: Train/Test Split

Trước khi huấn luyện, ta chia dữ liệu thành 2 phần:

```
Toàn bộ dữ liệu (100%)
├── Tập huấn luyện (Training set): 80-90% → Dùng để "dạy" mô hình
└── Tập kiểm tra (Test set): 10-20% → Dùng để "kiểm tra" mô hình
```

**Tại sao phải chia?** Giống như bạn học bài (training) rồi phải làm bài kiểm tra (test) bằng đề MỚI — để xem bạn thực sự hiểu bài hay chỉ học vẹt!

---

## 3. Liên hệ với Code

### 3.1. Hồi quy đơn — Dự đoán điểm từ giờ học

**`demo_regression.ipynb` → Cell 1-2:** Tạo dữ liệu giả lập

```python
hours = np.random.randint(1, 20, 100)   # Tạo 100 số ngẫu nhiên (1-19) = số giờ học
grades = 5 * hours + np.random.normal(0, 5, 100)  # Điểm = 5 × giờ + nhiễu ngẫu nhiên
```
- `np.random.normal(0, 5, 100)`: thêm "nhiễu" (noise) để giống thực tế — không ai học cùng số giờ mà được cùng điểm!

**Cell 4:** Chia dữ liệu

```python
hours_train = hours[:80]      # 80 mẫu đầu để huấn luyện
hours_test = hours[80:]       # 20 mẫu sau để kiểm tra
```

**Cell 5:** Huấn luyện mô hình (QUAN TRỌNG)

```python
from sklearn.linear_model import LinearRegression

grade_predictor = LinearRegression()   # Tạo mô hình
grade_predictor.fit(hours_train.reshape(-1, 1), grades_train)  # Huấn luyện

a = grade_predictor.coef_[0]     # Lấy hệ số a = 5.06
b = grade_predictor.intercept_   # Lấy hệ số b = -0.13
```
- `.fit()` = "dạy" mô hình bằng dữ liệu training
- `.reshape(-1, 1)` = chuyển mảng 1 chiều thành 2 chiều (sklearn yêu cầu)
- `.coef_` = hệ số góc (a)
- `.intercept_` = hệ số chặn (b)

**Cell 7:** Đánh giá

```python
r2 = grade_predictor.score(hours_test.reshape(-1, 1), grades_test)
# R² = 0.88 → mô hình giải thích 88% — khá tốt!

mse = np.mean((grades_test - grade_test_pred) ** 2)
# MSE = 58.5 → sai số trung bình
```

### 3.2. Hồi quy đơn — Dữ liệu thực tế (Doanh số vs Quảng cáo)

**Cell 8-15:** Dùng file `data_simple_reg.csv`

```python
df = pd.read_csv('data_simple_reg.csv')
df.dropna(inplace=True)    # Xóa dòng thiếu dữ liệu
```

```python
# Chia dữ liệu bằng train_test_split (cách chuyên nghiệp hơn)
x_qc_train, x_qc_test, y_ds_train, y_ds_test = train_test_split(
    x_qc, y_ds, test_size=0.1, random_state=42
)
```
- `test_size=0.1`: dành 10% cho test
- `random_state=42`: seed để kết quả lặp lại được

**Kết quả:** a = 3.52, b = 42.86 → Mỗi triệu chi cho quảng cáo → doanh số tăng 3.52 triệu. R² = 0.986 → **rất tốt**!

### 3.3. Hồi quy bội + One-Hot Encoding

**Cell 20-28:** Dùng file `data_multiple_reg.csv`

```python
# Mã hóa biến phân loại
qc_encoded = pd.get_dummies(df['Quang_Cao'])

# Ghép lại thành bảng đầu vào
x = pd.concat([qc_encoded, df[['PR', 'Online']]], axis=1)
```
- `pd.get_dummies()`: tự động chuyển "High", "Low"... thành cột 0/1
- `pd.concat()`: ghép các cột lại với nhau

**Kết quả:** Sau khi thêm biến phân loại, R² tăng từ 0.62 → **0.92** — cải thiện rất lớn!

### 3.4. Hồi quy Logistic

**Cell 30-35:** Dùng file `data_logistic_reg.csv`

```python
from sklearn.preprocessing import LabelEncoder
encoder = LabelEncoder()
df['Danh_Gia'] = encoder.fit_transform(df['Danh_Gia'])  # "Tốt"→1, "Xấu"→0
```

```python
from sklearn.linear_model import LogisticRegression
model = LogisticRegression()
model.fit(x_train, y_train)
```

```python
accuracy = accuracy_score(y_test, y_pred)   # 0.80 = đúng 80%
precision = precision_score(y_test, y_pred) # 0.81
recall = recall_score(y_test, y_pred)       # 0.82
f1 = f1_score(y_test, y_pred)              # 0.82
```

---

## 4. Ví dụ thực tế bổ sung

### Ví dụ 1: Dự đoán tiền điện hàng tháng

Bạn muốn dự đoán tiền điện dựa trên số giờ dùng điều hòa.

| Giờ dùng (X) | Tiền điện (Y) |
|--------------|--------------|
| 50 | 500,000đ |
| 100 | 900,000đ |
| 150 | 1,400,000đ |
| 200 | 1,800,000đ |

→ Mô hình: **Y = 8,667 × X + 66,667**
→ Dự đoán: Nếu dùng 120 giờ → Tiền ≈ 8,667 × 120 + 66,667 ≈ **1,107,000đ**

### Ví dụ 2: Dự đoán khách hàng có mua hàng không (Logistic)

Một cửa hàng online muốn biết khách có mua hàng không dựa trên:
- Thời gian lướt web (phút)
- Số sản phẩm đã xem

| Thời gian | Sản phẩm xem | Mua? |
|-----------|-------------|------|
| 2 phút | 1 | Không |
| 15 phút | 5 | Có |
| 30 phút | 10 | Có |
| 5 phút | 2 | Không |

→ Dùng Logistic Regression để dự đoán xác suất mua hàng!

---

## 5. Tóm tắt & Ghi nhớ

### 7 điểm chính cần nhớ:

1. **Hồi quy tuyến tính đơn** dự đoán Y từ **1 biến X** theo công thức `Y = aX + b`
2. **Hồi quy tuyến tính bội** dự đoán Y từ **nhiều biến X** theo công thức `Y = a₁X₁ + a₂X₂ + ... + b`
3. **Hồi quy logistic** dùng để **phân loại** (Có/Không, 0/1), không phải dự đoán số
4. **One-Hot Encoding** (`pd.get_dummies()`) dùng để chuyển dữ liệu dạng chữ thành số
5. **Train/Test Split** luôn chia dữ liệu trước khi huấn luyện để đánh giá khách quan
6. **R²** đo mức độ giải thích của mô hình (0-1, càng gần 1 càng tốt)
7. **Accuracy, Precision, Recall, F1** đo chất lượng mô hình phân loại

### So sánh với kiến thức trước:

| Tuần | Nội dung | Liên hệ |
|------|----------|---------|
| Week 7 (Pandas) | Đọc, xử lý dữ liệu | → Chuẩn bị dữ liệu đầu vào cho mô hình |
| Week 8 (Visualization) | Vẽ biểu đồ | → Trực quan hóa mối quan hệ X-Y trước khi hồi quy |
| Week 9 (Thống kê) | Thống kê mô tả | → Hiểu phân bố dữ liệu trước khi xây mô hình |
| Week 14 (Tương quan) | Hệ số tương quan | → Nếu X và Y có tương quan mạnh → hồi quy sẽ cho kết quả tốt |
| **Week 16** | **Hồi quy** | **→ Bước đầu tiên vào Machine Learning!** |

### Quy trình tổng quát xây dựng mô hình:

```
Dữ liệu thô → Tiền xử lý → Chia Train/Test → Huấn luyện → Dự đoán → Đánh giá
   (CSV)      (dropna,       (train_test_    (.fit())    (.predict())  (R², MSE,
               get_dummies)   split)                                   Accuracy)
```

---

> **Bạn có câu hỏi gì không?** Hãy hỏi bất cứ điều gì bạn chưa hiểu nhé! Đừng ngại, không có câu hỏi nào là ngớ ngẩn cả. 😊
