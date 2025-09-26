# Brain MRI CNN Projesi

Bu repo, *Global AI Hub - Derin Öğrenme Bootcamp* kapsamında geliştirilmiş bir örnek çalışmayı içermektedir.  
Projenin amacı, *Brain MRI görüntülerinden tümör tespiti* yapabilen bir derin öğrenme modeli geliştirmektir.  

Repo *public* olarak paylaşılmıştır.  

---

## 📌 Giriş
- Kullanılan veri seti: [Brain MRI Images for Brain Tumor Detection (Kaggle)](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection/data)  
- Proje kapsamında:
  - *Veri önişleme*: Görüntülerin normalize edilmesi, yeniden boyutlandırılması, etiketlenmesi ve train-validation-test setlerine ayrılması  
  - *Data Augmentation*: Flip, Rotation, Zoom, Color Jitter gibi dönüşümlerle veri artırımı  
  - *Modelleme*: CNN tabanlı model (MobilenetV2 Transfer Learning + Fine-Tuning)  
  - *Değerlendirme*: Accuracy & Loss grafikleri, Confusion Matrix, Classification Report  
  - *Görselleştirme*: Eigen-CAM ile modelin odaklandığı bölgelerin gösterilmesi  
  - *Hiperparametre optimizasyonu*: Dropout oranı, dense layer boyutu, learning rate, batch size, optimizer gibi parametrelerde farklı denemeler  

---

## 📊 Metrikler
Model eğitimi sonucunda elde edilen performans:  

- *Başarı Skoru (Validation)*  
  - Accuracy: ~%86.8  
  - AUC: ~0.95  

- *Confusion Matrix & Classification Report*  
  - Tümörlü (yes) sınıfında yüksek recall (%95.6) → model, tümörlü örnekleri yakalamada oldukça başarılıdır.  
  - Tümörsüz (no) sınıfında precision daha yüksek (%91.6) → yanlış pozitiflerin az olduğunu göstermektedir.  

- *Hiperparametre Denemeleri*  
  | Dropout | Dense Units | LR     | Batch Size | Optimizer | Val_Acc | Val_AUC |
  |---------|-------------|--------|------------|-----------|---------|---------|
  | 0.3     | 128         | 0.0010 | 16         | Adam      | *0.8684* | *0.9583* |
  | 0.5     | 128         | 0.0010 | 32         | Adam      | 0.8684  | 0.9122  |
  | 0.4     | 256         | 0.0005 | 32         | Adam      | 0.7632  | 0.8839  |
  | 0.5     | 256         | 0.0001 | 16         | RMSprop   | 0.6842  | 0.9003  |

- En iyi sonuç: *Adam optimizer + Dropout 0.3 + Dense 128 + LR=0.001 + Batch=16*

---

## 📂 Ekler
- *Eigen-CAM görselleştirme* ile modelin MRI görüntülerinde odaklandığı bölgeler incelenmiştir.  
- Proje Kaggle üzerinde GPU desteği ile çalıştırılmıştır.  

---

## 🚀 Sonuç ve Gelecek Çalışmalar
- Model, küçük veri setinde yüksek başarı elde etmiştir.  
- Gelecekte:  
  - Daha geniş bir MRI veri seti ile performansın artırılması  
  - Modelin *Streamlit* veya benzeri araçlarla deploy edilerek kullanıcı arayüzü eklenmesi  
  - Dinamik veri toplama ve gerçek zamanlı analiz senaryolarına uyarlanması  
  - Daha gelişmiş hiperparametre optimizasyonu (Keras Tuner, Bayesian Optimization)  

Bu proje bootcamp sonrasında da geliştirilmeye uygundur.  

---

## 🔗 Linkler
- 📓 Kaggle Notebook : https://www.kaggle.com/code/sudebaalan/brainmricnn-ipynb

