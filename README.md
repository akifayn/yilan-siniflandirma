# Zehirli Yılan Sınıflandırma (Venomous Snake Classification)

Binary görüntü sınıflandırma projesi — zehirli ve zehirsiz yılanları Transfer Learning ile ayırt eder.

[![Notebook'u Görüntüle](https://img.shields.io/badge/Notebook-nbviewer-orange)](https://nbviewer.org/github/akifayn/yilan-siniflandirma/blob/main/Zehirli_Yilan_Siniflandirma.ipynb)

## Hazırlayanlar

| Numara | İsim |
|--------|------|
| 214210040 | Muhammet Akif Ayan |
| 214210093 | Oğuzhan Yalçın |
| 214210095 | Erkan Yiğit |

## Proje Özeti

Bu proje, üç farklı Transfer Learning modelini karşılaştırarak zehirli/zehirsiz yılan sınıflandırması yapmayı amaçlar.

### Kullanılan Modeller

| Model | Epochs | Optimizer | Test Accuracy |
|-------|--------|-----------|---------------|
| ResNet50 | 44/50 | Adam | %56 |
| VGG16 | 16/50 | Adam | %79 |
| **MobileNetV2** | **50/50** | **Adam** | **%87** |

**En iyi model: MobileNetV2 — %87 test doğruluğu**

## Veri Seti

- **Toplam eğitim:** 1775 görüntü (Non-Venomous: 715, Venomous: 1060)
- **Toplam test:** 269 görüntü (Non-Venomous: 128, Venomous: 141)
- **Görüntü boyutu:** 224x224x3

> Veri seti boyutu nedeniyle GitHub'a yüklenmemiştir. `Snake Images/` klasörünü ayrıca temin edin.

## Kurulum

```bash
# Repo'yu klonla
git clone <repo-url>
cd "Yılan Sınıflandırma"

# Sanal ortam oluştur
python -m venv venv
venv\Scripts\activate      # Windows
# source venv/bin/activate  # Linux/Mac

# Kütüphaneleri yükle
pip install -r requirements.txt
```

## Kullanım

1. `Snake Images/` klasörünü proje dizinine koy (`train/` ve `test/` alt klasörleriyle)
2. Jupyter Notebook'u aç:
```bash
jupyter notebook Zehirli_Yilan_Siniflandirma.ipynb
```
3. Hücreleri sırayla çalıştır

## Klasör Yapısı

```
Yılan Sınıflandırma/
├── Zehirli_Yilan_Siniflandirma.ipynb   # Ana notebook
├── Zehirli_Yilan_Siniflandirma_GUNCEL.pdf  # Son eğitim raporu
├── requirements.txt
├── README.md
└── Snake Images/                        # Veri seti (yüklenmedi)
    ├── train/
    │   ├── Non Venomous/
    │   └── Venomous/
    └── test/
        ├── Non Venomous/
        └── Venomous/
```

## Teknik Detaylar

- **Framework:** TensorFlow / Keras
- **Görev:** Binary sınıflandırma (sigmoid çıkış)
- **Veri artırma:** Rotation, flip, zoom, shift
- **Callback:** EarlyStopping + ReduceLROnPlateau
- **Sınıf dengeleme:** compute_class_weight (balanced)
