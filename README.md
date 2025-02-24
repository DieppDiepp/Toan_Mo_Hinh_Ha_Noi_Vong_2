# 🏆 Cuộc Thi Toán Mô Hình 2024 - Vòng 2  
🧪 **Dự án: Math Model Challenge - Sparkle Phase 2**  
📍 **Toán Mô Hình Hà Nội - Nghiên cứu & Ứng dụng Toán học**  
🥉 **Giải Ba Bảng Đại Học - Vòng 2**  

<img width="339" alt="toanmonhinh" src="https://github.com/user-attachments/assets/5bfe9bda-9361-486d-9e41-a38efe2ce580" />

---
## 📌 Giới thiệu  
Dự án này được thực hiện trong khuôn khổ **Cuộc Thi Toán Mô Hình 2024 (Bảng Đại Học - Vòng 2)** với mục tiêu:  
- **Xây dựng mô hình toán học mô phỏng tương tác giữa hormone insulin và glucose** trong cơ thể.  
- **Cá nhân hóa mô hình dựa trên dữ liệu bệnh nhân thực tế**.  
- **Phân tích và dự báo mối quan hệ giữa đường huyết và thời gian bữa ăn**.  

📄 **Tài liệu kèm theo**:  
- 📁 **[`MMC_De_Thi_Phase2.pdf`](./MMC_De_Thi_Phase2.pdf)** - Đề thi chính thức.  
- 📁 **[`BANG_B_TMH_24028_TMH_V2.pdf`](./BANG_B_TMH_24028_TMH_V2.pdf)** - Báo cáo của đội thi **Sparkle**.  

---

## 🏗 Bố cục báo cáo  

### 1️⃣ **Mô hình toán học**  
#### **Cơ sở xây dựng**  
- **Sử dụng phương trình vi phân (ODEs)** để mô tả tương tác giữa **glucose ($G$), insulin ($I$), glucagon ($H$)**.  
- **Hai loại mô hình chính**:  
  1. **Mô hình tuyến tính (Linear ODEs)**.  
  2. **Mô hình dựa trên Sigmoid (Sigmoid-based ODEs)** để linh hoạt hơn.  

Các phương trình vi phân tổng thể:  

$$
\frac{dG}{dt} = \frac{dG_{food}}{dt} + g_{out}G + g_i I + g_h H
$$  

$$
\frac{dI}{dt} = i_g (G_b - G) + i_b (I_b - I)
$$  

$$
\frac{dH}{dt} = h_g (G_b - G) + h_b (H_i - H)
$$  

📄 **Chi tiết phương pháp trong file `1_Model_01.ipynb`**.  

---

### 2️⃣ **Thiết lập mô hình toán học**  

#### 🔹 **Mô hình 1: Tuyến tính**  
- Hàm mô tả tốc độ hấp thụ glucose từ thực phẩm:  

$$
\frac{dG_{food}(t)}{dt} = 
\begin{cases}
\alpha (G_{food\_max} - G_{food}(t)), & t \geq t_{eat} \\
0, & t < t_{eat}
\end{cases}
$$

#### 🔹 **Mô hình 2: Phi tuyến tính sử dụng Sigmoid**  
- Dùng **hàm Sigmoid** để mô tả quá trình hấp thụ glucose:  

$$
G_{food}(t) =
\begin{cases}
0, & t < t_0 \\
\frac{G_{\max}}{1 + e^{-\alpha (t - t_0)}}, & t_0 \leq t < t_1 \\
\frac{G_{\max}}{1 + e^{-\alpha (t - t_0)}} \cdot e^{-\beta (t - t_1)}, & t \geq t_1
\end{cases}
$$

📄 **Chi tiết phương pháp trong file `2_Model_02.ipynb`**.  

---

### 3️⃣ **Ứng dụng mô hình & Cá nhân hóa dự đoán**  
- **Bệnh nhân thực tế được mô hình hóa** với dữ liệu từ cảm biến đường huyết.  
- **Phân tích quan hệ giữa mức glucose và thời gian bữa ăn**.  
- **So sánh kết quả dự đoán giữa hai mô hình**.  

📂 **File kết quả**: `3_Glucose_Insulin_Glucagon_Analytics.ipynb`  

---

### 4️⃣ **Đánh giá & Hướng cải tiến**  
#### ✅ **Ưu điểm**  
- **Mô phỏng chính xác xu hướng đường huyết theo thời gian**.  
- **Biểu diễn tốt tác động của insulin và glucagon**.  
- **Dễ dàng mở rộng để phân tích nhiều bệnh nhân khác nhau**.  

#### ❌ **Nhược điểm & Hướng phát triển**  
- **Tối ưu hóa tham số để phù hợp với từng bệnh nhân**.  
- **Kết hợp Machine Learning để cải thiện dự đoán đường huyết**.  
- **Xây dựng hệ thống trực quan hóa kết quả (App/Web)**.  

---

## 📂 **Các tệp tin quan trọng**  
### 📊 **Mô hình toán học & Mã nguồn**  
- 📁 **`1_Model_01.ipynb`** - Mô hình tuyến tính (Linear ODEs).  
- 📁 **`2_Model_02.ipynb`** - Mô hình phi tuyến tính dùng Sigmoid.  
- 📁 **`3_Glucose_Insulin_Glucagon_Analytics.ipynb`** - Ứng dụng phân tích dữ liệu thực tế.  
- 📁 **`4_AccuracyOfModel.ipynb`** - Kiểm tra độ chính xác mô hình.  

### 📄 **Dữ liệu đầu vào**  
- 📁 **`GlucoseMonitorRecordings.tsv`** - Dữ liệu đường huyết theo thời gian.  
- 📁 **`NutritionFacts_StandardizedMeals.tsv`** - Thành phần dinh dưỡng bữa ăn.  

---

## 📚 **Tài liệu tham khảo**  
1. **Nghiên cứu về tương tác giữa glucose & insulin**: [Zierler, Kenneth (1999)](https://journals.physiology.org/doi/full/10.1152/ajpendo.1999.276.3.E409)  
2. **Mô hình Vi phân glucose-insulin-glucagon**: [Leiden University Paper](https://www.universiteitleiden.nl/binaries/content/assets/science/mi/scripties/bachelor/2016-2017/veld_corinne_in_t_analysis_of_glucose-insulin-glucagon_interaction_models.pdf)  
3. **Chỉ số đường huyết & ảnh hưởng**: [Wikipedia](https://en.wikipedia.org/wiki/Glycemic_index)  
4. **Kiểm soát mức insulin bình thường**: [New Health Advisor](https://www.newhealthadvisor.org/Normal-Insulin-Levels.html)  
5. **Video giảng dạy kiểm soát đường huyết**: [YouTube](https://www.youtube.com/watch?v=OHrX3X3LGzI)  

---

## 🎉 **Lời cảm ơn**  
🔥 **Đội Sparkle** vinh dự **đạt giải Ba Cuộc Thi Toán Mô Hình 2024 (Bảng Đại Học - Vòng 2)!**  
🙌 Xin chân thành cảm ơn **BTC Toán Mô Hình Hà Nội** đã tạo cơ hội để nhóm áp dụng **toán học, mô hình hóa sinh lý học và khoa học dữ liệu** vào bài toán thực tiễn.  

🛠 **Mọi đóng góp & phản hồi, vui lòng gửi về nhóm Sparkle. Cảm ơn! 🚀**  
