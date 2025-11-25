# makine_ogrenmesi
Cafe Sales Prediction Project
# Proje Özeti

Bu proje, kafe satış verilerini kullanarak müşterinin ödeme yöntemini tahmin eden bir makine öğrenmesi modeli oluşturur.

# Veri İşleme

ERROR, UNKNOWN ve boş değerler NaN ile değiştirildi.

Eksik Quantity değerleri silindi:

data = data.dropna(subset=['Quantity'])

Kategorik değişkenler OneHotEncoder ile dönüştürüldü.

# Model

Model: RandomForestClassifier

Pipeline yapısı kullanıldı.

Ortalama doğruluk: %87

# Kullanılan Kütüphaneler

pandas

numpy

scikit-learn

# Tahmin Fonksiyonu
def predict_payment(item, quantity, price, location, order_type):
    df = pd.DataFrame([{
        "Item": item,
        "Quantity": quantity,
        "Price Per Unit": price,
        "Location": location
    }])
    return model.predict(df)[0]

# Örnek Kullanım
predict_payment("Coffee", 20, "Takeaway")

# Sonuç

Temizlenmiş veriler üzerinden çalışan model, satış özelliklerine göre müşterinin ödeme yöntemini tahmin edebilmektedir.
