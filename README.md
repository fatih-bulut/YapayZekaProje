
# Laboratuvar Numune Karışımı Optimizasyonu (Senaryo 7)

Bu proje, bir biyoteknoloji firması için en verimli test çözeltisini oluşturmak amacıyla **Genetik Algoritma (Genetic Algorithm)** kullanarak reaktif oranlarını optimize eden bir yapay zeka uygulamasıdır.

## 📋 Proje Tanımı

**Amaç:** İki farklı reaktifin ($x_1$ ve $x_2$) karışım oranlarını belirleyerek, test hassasiyetini maksimize etmektir. Problem, belirli laboratuvar kısıtlarına uyarak en yüksek verimi sağlayan karışım oranlarını bulmayı hedefler.

### Matematiksel Model

Projede kullanılan amaç fonksiyonu ve kısıtlar şunlardır:

  * **Amaç Fonksiyonu (Test Hassasiyeti Puanı):**
    $$y = 3x_1 + 2x_2 + x_1x_2 - 0.5x_2^2$$

  * **Değişkenler:**

      * $x_1$: Reaktif A oranı (%) $\rightarrow [10, 80]$
      * $x_2$: Reaktif B oranı (%) $\rightarrow [10, 80]$

  * **Kısıtlar:**

    1.  $x_1 + x_2 \le 100$ (Toplam karışım %100'ü geçemez)
    2.  $x_1 \ge 25$ (Reaktif A en az %25 olmalıdır)

-----

## ⚙️ Kurulum ve Gereksinimler

Bu projeyi kendi bilgisayarınızda çalıştırmak için aşağıdaki adımları izleyebilirsiniz.

### 1\. Gereksinimler

Proje **Python 3** dilinde yazılmıştır ve aşağıdaki kütüphanelere ihtiyaç duyar:

  * `numpy` (Matematiksel işlemler için)
  * `matplotlib` (Sonuçların görselleştirilmesi için)

### 2\. Kurulum

Gerekli kütüphaneleri yüklemek için terminal veya komut satırında şu komutu çalıştırın:

```bash
pip install numpy matplotlib
```

### 3\. Çalıştırma

Projeyi bir Jupyter Notebook ortamında (Jupyter Lab, Google Colab veya VS Code) açarak hücreleri sırasıyla çalıştırabilirsiniz.

```bash
jupyter notebook YapayZekaProje.ipynb
```

-----

## 🚀 Çalışma Adımları (Algoritma Mantığı)

Proje, evrimsel hesaplama yöntemlerinden biri olan Genetik Algoritma üzerine kurulmuştur. İşleyiş adımları şu şekildedir:

1.  **Parametrelerin Belirlenmesi:** Popülasyon büyüklüğü (100), nesil sayısı (100), mutasyon oranı (0.1) gibi hiperparametreler tanımlanır.
2.  **Popülasyon Oluşturma:** Belirlenen $x_1$ ve $x_2$ sınırları içerisinde rastgele bireyler (çözüm adayları) üretilir.
3.  **Uygunluk (Fitness) Hesaplama:** Her birey amaç fonksiyonuna sokulur. Eğer birey kısıtları ($x_1+x_2 \le 100$ vb.) sağlamıyorsa, **Ceza Yöntemi (Penalty)** uygulanarak puanı düşürülür (-99999).
4.  **Seçilim (Tournament Selection):** Rastgele seçilen bireyler arasından en iyi puana sahip olanlar ebeveyn olarak seçilir.
5.  **Çaprazlama (Crossover):** Seçilen ebeveynlerin genleri karıştırılarak yeni bireyler üretilir.
6.  **Mutasyon:** Gen havuzunda çeşitliliği sağlamak ve yerel maksimumlara takılmamak için rastgele küçük değişiklikler yapılır.
7.  **Optimizasyon Döngüsü:** Bu işlemler belirlenen nesil sayısı boyunca tekrar eder ve en iyi çözüm saklanır.

-----

## 📊 Sonuçlar

Algoritma çalıştırıldığında aşağıdakileri çıktılar:

1.  **En İyi Çözüm Değerleri:** $x_1$ ve $x_2$ için bulunan optimal yüzdeler.
2.  **Maksimum Skor:** Elde edilen en yüksek test hassasiyeti.
3.  **Kısıt Kontrolü:** Bulunan çözümün kurallara uyup uymadığı.
4.  **Yakınsama Grafiği:** Nesiller boyunca uygunluk değerinin artışını gösteren bir çizgi grafiği (`matplotlib` ile).

-----

## 👤 Yazar Bilgisi

  * **Adı Soyadı:** Fazlı Fatih Bulut
  * **Okul Numarası:** 2312729007
  * **Ders:** Yapay Zeka Sistemleri
