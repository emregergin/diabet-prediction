# 🩺 Diyabet Tahmin Projesi

Merhabalar, bu repo Pima Indians Diabetes Database'i ([Dataset](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)) kullanarak bir kişinin diyabet hastası olup olmadığını tahmin eden bir makine öğrenmesi projesidir.

Bu projede sadece modeli kurmadım, aynı zamanda veriyi analiz etme, temizleme, hazırlama ve en iyi parametreleri bulma gibi adımları da detaylıca uygulamaya çalıştım. Model olarak AdaBoost Classifier kullanmayı seçtim ve en iyi performans için GridSearchCV ile hiperparametre optimizasyonu yaptım.

## 📈 Projenin Aşamaları
Aşağıdaki adımları izleyerek projeyi geliştirmeye çalıştım:

1. 📊 Keşifsel Veri Analizi (EDA)
İlk olarak veri setini yükleyip genel yapısını anlamak için head(), info(), describe() gibi temel fonksiyonları kullandım.

Glucose, BloodPressure, SkinThickness gibi bazı sütunlarda fazlaca 0 değerleri olduğunu fark ettim. Bu değerler biyolojik olarak imkansız olduğundan dolayı bunların aslında eksik veri olduğunu anladım.

Veri setindeki değişkenlerin dağılımlarını ve Outcome (hedef değişken) ile olan ilişkilerini daha iyi anlamak için histplot, boxplot gibi çeşitli grafikler kullandım.

2. 🧹 Veri Ön İşleme (Data Preprocessing)
İlk olarak anormal olan 0 değerlerini eğitim setindeki (X_train) o sütunun medyan değeri ile doldurdum. Test setinde veri sızıntısı (data leakage) olmaması için test setindeki (X_test) 0'ları da yine eğitim setinden hesapladığım medyanlarla değiştirdim.

Sonrasında modeli eğitmek ve test etmek için veri setini %80 eğitim, %20 test olarak ayırdım (train_test_split).

En son modelin daha stabil eğitilmesi için özelliklerimi StandardScaler ile ölçeklendirdim .

3. 🚀 Model Geliştirme ve Optimizasyon 
İlk olarak AdaBoostClassifier modelini varsayılan parametrelerle eğittim ve yaklaşık %75.3'lük bir doğruluk (accuracy) elde ettim .

Sonrasında modelin performansını artırmak için GridSearchCV kullanarak n_estimators ve learning_rate gibi en kritik hiperparametreler için en iyi değerleri bulmaya çalıştım.

En sonunda ise GridSearchCV sonucunda bulunan en iyi parametreler (learning_rate=1, n_estimators=150) ile modelimi yeniden eğittim ve test verisi üzerinde %76'ya yakın bir doğruluk skoru elde ettim .

## 🛠️ Kurulum

Projeyi kendi bilgisayarınızda çalıştırmak isterseniz:

1.  **Repository'yi Klonlayın:**
    ```bash
    git clone [https://github.com/emregergin/diabet-prediction](https://github.com/emregergin/diabet-prediction)
    cd diabet-prediction
    ```

2.  **Gerekli Kütüphaneleri Yükleyin:**
    Projede kullanılan kütüphaneleri `requirements.txt` dosyası aracılığıyla kolayca yükleyebilirsiniz.
    ```bash
    pip install -r requirements.txt
    ```
    - `numpy`
    - `pandas`
    - `matplotlib`
    - `seaborn`
    - `scikit-learn`

## 🚀 Kullanım

Projenin tüm adımlarını ve analizleri görmek için `diabet-prediction.ipynb` adlı Jupyter Notebook dosyasında hücreleri teker teker çalıştırabilirsiniz.
