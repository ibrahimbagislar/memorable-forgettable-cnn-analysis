# CNN ile Memorable ve Forgettable Görüntü Sınıflandırması

Bu proje, görsellerin **memorable** ya da **forgettable** olarak sınıflandırılması üzerine hazırlanmış bir CNN analizidir. Çalışmada Kaggle'daki *Forgetable Images vs Memorable Images* veri seti kullanıldı.

Amaç sadece bir model eğitmek değil; görüntü kontrastını değiştiren yöntemlerin CNN başarısını nasıl etkilediğini görmekti. Bu yüzden aynı veri üzerinde dört farklı görüntü sürümü karşılaştırıldı:

- original grayscale images
- HE: Histogram Equalization
- AHE: Adaptive Histogram Equalization
- CLAHE: Contrast Limited Adaptive Histogram Equalization

## Veri Seti

Veri seti: [Forgetable Images vs Memorable Images](https://www.kaggle.com/datasets/pidual2/forgetable-images-vs-memorable-images)

Notebook çalıştırıldığında veri seti `kagglehub` ile indirilmeye çalışır. Kaggle Notebook ortamında çalıştırılıyorsa veri seti `/kaggle/input` altında da otomatik aranır.

Bu çalıştırmada veri setinde toplam **69.195** etiketlenebilir görüntü bulundu:

| Sınıf | Görüntü Sayısı |
|---|---:|
| memorable | 47.302 |
| forgettable | 21.893 |

Model eğitiminde sınıf dengesizliğini azaltmak için dengeli bir alt küme kullanıldı.

## Notebook Ne Yapıyor?

Notebook şu adımları içeriyor:

1. Veri setini okur ve etiketleri dosya yollarından çıkarır.
2. Görüntü boyutu, parlaklık, kontrast ve sınıf dağılımı için keşifsel veri analizi yapar.
3. HE, AHE ve CLAHE preprocessing yöntemlerini uygular.
4. İki farklı CNN modeli kurar.
5. Original, HE, AHE ve CLAHE image versions üzerinde modelleri karşılaştırır.
6. Accuracy, precision, recall, F1-score ve confusion matrix ile sonuçları yorumlar.

## Sonuçlar

Bu çalıştırmada en iyi sonuç **original images + CNN-1** kombinasyonunda elde edildi.

| Metrik | Değer |
|---|---:|
| Accuracy | 0.8077 |
| Precision | 0.7381 |
| Recall | 0.9538 |
| F1-score | 0.8322 |

CLAHE, kontrast uygulanmış görüntüler içinde en dengeli sonuçlardan birini verdi; ancak bu deneyde original images CNN-1 için daha başarılı oldu. Bu da her preprocessing yönteminin her veri setinde performansı artırmayabileceğini gösteriyor.

## Proje Yapısı

```text
ibrahim-memorability-cnn-analysis/
├── memorable_forgettable_cnn_analysis.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Nasıl Çalıştırılır?

1. Repository'yi klonlayın.
2. Notebook'u Google Colab veya Kaggle Notebook üzerinde açın.
3. Gerekli paketleri kurun:

```bash
pip install -r requirements.txt
```

4. Notebook hücrelerini sırayla çalıştırın.

Kaggle veya Colab ortamında çalıştırmak daha rahat olur; çünkü veri seti büyük.

## Notlar

Veri seti dosyaları repoya eklenmedi. Veri seti büyük olduğu için notebook içinde indirme ve yol bulma mantığı kullanıldı.

Bu proje final sınavı şablonundan temizlenmiş, GitHub'da paylaşılabilir hale getirilmiş sürümdür.
