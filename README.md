# makine_ogrenmesi
Cafe Sales Prediction Project
# Proje Özeti

Bu proje, kafe satış verilerini kullanarak müşterinin ödeme yöntemini tahmin eden bir makine öğrenmesi modeli oluşturur.

# Veri Temizleme

Bütün sütunlardaki ERROR, UNKNOWN ve boş değerler NaN ile değiştirildi.

Quantity, PricePerUnit, TotalSpent özellikleri string değerden numeric değere çevrildi.(Bu bir itemin fiyatından adetine göre ne kadar kazandığımızı belirlemeye katkı sağlar)
PricePerUnit*Quantity=TotalSpent


İtem sütünundaki NaN değerler için Price Per Unit sütunu kontrol edilir ve Price Per Unit değerlerine göre hangi item değerinin denk geldiği bulunur böylece item sütunundaki nan değerler kaldırılmış olur.Fakat aynı olan Price Per Unit değerleri için bu işlem yapılamaz. Örnek olarak Sandwich ve Smoothie itemi'nin Price Per Unit değeri 6'dır bu yüzden 6 değerini gördüğümüzde kesinlikle Sandwich ya da Smoothie diyemeyiz. 
<img width="973" height="180" alt="image" src="https://github.com/user-attachments/assets/a65c6ebb-019b-49d7-8641-9a2d74327dd6" />

Quantity sütunundaki NaN değerler için medyan(ortanca değer) kullanılarak değer ataması yapılır. Bütün itemlerin Quantity medyanı hesaplanır ve çıkan sonuca göre NaN olan Quantity verilerine atama yapılır. -->Coffee itemi için kod örneği aşağıda yer almaktadır.
<img width="739" height="86" alt="image" src="https://github.com/user-attachments/assets/3d30c1fc-67a7-43e4-9aa8-af857b0b20f2" />

Item sütununda kalan NaN değerler için itemlerin oranına bakılır.
-->İlk olarak orana bakılır. Örnek olarak fiyatı 3 olan ve item verisi NaN olmayanların total verideki oranı bulunur.
<img width="799" height="149" alt="image" src="https://github.com/user-attachments/assets/8f56f22b-03cb-4c7a-adbe-4403a42727b1" />
-->Ardından bu verilere göre NaN olan item değerlerine atam yapılır.
<img width="983" height="165" alt="image" src="https://github.com/user-attachments/assets/341db676-6884-4a16-9197-70afd825704a" />
-->Bu işlem bütün itemler için yapılır.

Total Spent = Price Per Unit * Quantity (Price Per Unit ve Total Spent sütunlarının kalan NaN değerleri için hesaplama yapılır ve NaN değerler doldurulur)
<img width="981" height="121" alt="image" src="https://github.com/user-attachments/assets/d016f155-d73f-4192-9586-d64948dc3c59" />

Price Per Unit sütununa göre NaN item değerlerini doldur.
<img width="990" height="116" alt="image" src="https://github.com/user-attachments/assets/48c565b2-ee09-436f-abc4-0f16260c9a6e" />


Diğer sütunlardaki veriler aynı şekilde dolduruldu.

Kategorik değişkenler OneHotEncoder ile dönüştürüldü.

# Model

Model: RandomForestClassifier

Pipeline yapısı kullanıldı.

Ortalama doğruluk: %87

# Kullanılan Kütüphaneler

pandas

numpy

scikit-learn


# Örnek Kullanım
predict_payment("Coffee", 20, "Takeaway")

# Sonuç

Temizlenmiş veriler üzerinden çalışan model, satış özelliklerine göre müşterinin ödeme yöntemini tahmin edebilmektedir.
