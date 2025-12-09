# Predict Payment Method
Cafe Sales Prediction Project
# Proje Özeti

Bu proje, kafe satış verilerini kullanarak müşterinin ödeme yöntemini tahmin eden bir makine öğrenmesi modeli oluşturur.

# Veri Temizleme

- Bütün sütunlardaki ERROR, UNKNOWN ve boş değerler NaN ile değiştirildi.

- Quantity, PricePerUnit, TotalSpent özellikleri string değerden numeric değere çevrildi.(Bu bir itemin fiyatından adetine göre ne kadar kazandığımızı belirlemeye katkı sağlar)
PricePerUnit*Quantity=TotalSpent

- İtem sütununa göre NaN olan Price Per Unit değerleri dolduruldu.
<img width="984" height="165" alt="image" src="https://github.com/user-attachments/assets/c3f14af9-11b8-4023-b27a-36c1047b4861" />

- İtem sütünundaki NaN değerler için Price Per Unit sütunu kontrol edilir ve Price Per Unit değerlerine göre hangi item değerinin denk geldiği bulunur böylece item sütunundaki nan değerler kaldırılmış olur.Fakat aynı olan Price Per Unit değerleri için bu işlem yapılamaz. Örnek olarak Sandwich ve Smoothie itemi'nin Price Per Unit değeri 6'dır bu yüzden 6 değerini gördüğümüzde kesinlikle Sandwich ya da Smoothie diyemeyiz. 
<img width="973" height="180" alt="image" src="https://github.com/user-attachments/assets/a65c6ebb-019b-49d7-8641-9a2d74327dd6" />

- Quantity sütunundaki NaN değerler için medyan(ortanca değer) kullanılarak değer ataması yapılır. Bütün itemlerin Quantity medyanı hesaplanır ve çıkan sonuca göre NaN olan Quantity verilerine atama yapılır. -->Coffee itemi için kod örneği aşağıda yer almaktadır.
<img width="739" height="86" alt="image" src="https://github.com/user-attachments/assets/3d30c1fc-67a7-43e4-9aa8-af857b0b20f2" />


- Total Spent = Price Per Unit * Quantity (Price Per Unit ve Total Spent sütunlarının kalan NaN değerleri için hesaplama yapılır ve NaN değerler doldurulur)
<img width="981" height="121" alt="image" src="https://github.com/user-attachments/assets/d016f155-d73f-4192-9586-d64948dc3c59" />

- Price Per Unit sütununa göre NaN item değerlerini doldur.
<img width="990" height="116" alt="image" src="https://github.com/user-attachments/assets/48c565b2-ee09-436f-abc4-0f16260c9a6e" />


- Item sütununda kalan NaN değerler için itemlerin oranına bakılır.
-->İlk olarak orana bakılır. Örnek olarak fiyatı 3 olan ve item verisi NaN olmayanların total verideki oranı bulunur.
<img width="1002" height="149" alt="image" src="https://github.com/user-attachments/assets/b5dbba35-46d6-4ed2-ae6b-9cf7d9ef8aa0" />
-->Ardından bu verilere göre NaN olan item değerlerine atam yapılır.
<img width="1012" height="165" alt="image" src="https://github.com/user-attachments/assets/a27d8cd0-41af-4602-ae8f-54bce77e0ed3" />
-->Bu işlem bütün itemler için yapılır.

- Total Spent Bazlı Payment Method Grafiği
<img width="990" height="547" alt="image" src="https://github.com/user-attachments/assets/71004db5-5402-4472-84fe-1b2a441d9683" />
Grafikte görüldüğü üzere bazı Total Spent değerlerinde cash bazılarında credit card bazılarında ise digital wallet dikkat çekmiştir. Biz de buna göre tahmin yapmaya çalışacağız.

- İtem Bazlı Location Grafiği 
<img width="1005" height="590" alt="image" src="https://github.com/user-attachments/assets/696748a0-8f31-4a4d-ae7c-ba096f8508e3" />
Aynı şekilde oranlara bakılarak NaN location değerleri dolduruldu.
<img width="987" height="358" alt="image" src="https://github.com/user-attachments/assets/75c066bd-2a63-43f4-a7f6-a0e4e533442a" />

- Date sütunundaki NaN değerlerin silinmesi.
<img width="991" height="45" alt="image" src="https://github.com/user-attachments/assets/2baef389-c8fb-4e72-a704-9f5f9518ae87" />

- Veride NaN değer kalmadı yani tahmin edilmeye uygun bir veri hazırlandı.
<img width="980" height="209" alt="image" src="https://github.com/user-attachments/assets/3782b126-06d1-429c-88e9-46f3d05b5157" />

- Train-Test ve RandomForest Modeli oluşturuldu.
<img width="976" height="241" alt="image" src="https://github.com/user-attachments/assets/5fd204e8-cecb-49c7-8927-51160a344748" />

- Tahmin işlemi test edildi.
<img width="988" height="382" alt="image" src="https://github.com/user-attachments/assets/72695f1f-e35e-403c-b6ea-b356b482122f" />


# Örnek Kullanım
predict_payment("Coffee", 20, "Takeaway")


Temizlenmiş veriler üzerinden çalışan model, satış özelliklerine göre müşterinin ödeme yöntemini tahmin edebilmektedir.
