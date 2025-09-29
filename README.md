# PyTorch ile Uçtan Uca Bilgisayarlı Görü Projesi: Sınıflandırma, Tespit ve Takip

## Proje Özeti

Bu proje, bir bilgisayarlı görü (computer vision) hattının üç temel aşamasını da içeren bütünsel bir çalışmadır: **Görüntü Sınıflandırma**, **Nesne Tespiti** ve **Nesne Takibi**. Proje, PyTorch ve OpenCV kütüphaneleri kullanılarak geliştirilmiştir ve görevler mantıksal olarak iki ayrı Jupyter Notebook'a bölünmüştür.

1.  **Görev 1 - Görüntü Sınıflandırma:** CIFAR-10 veri seti kullanılarak sıfırdan bir Evrişimli Sinir Ağı (CNN) modeli oluşturulmuş, eğitilmiş ve değerlendirilmiştir.
2.  **Görev 2 - Nesne Tespiti:** PASCAL VOC veri seti üzerinde, önceden eğitilmiş bir Faster R-CNN modeli, araç tespiti görevi için yeniden eğitilmiş (fine-tuning) ve özelleştirilmiştir.
3.  **Görev 3 - Nesne Takibi:** Eğitilen nesne tespit modelinin çıktıları, bir video akışındaki araçları tutarlı bir şekilde takip etmek için SORT (Simple Online and Realtime Tracking) algoritması ile entegre edilmiştir.

---

## Proje Klasör Yapısı

- `models/`: Eğitilmiş model ağırlıklarını içerir (`cifar10_classifier.pth` ve `pascal_object_detector.pth`).
- `output/`: Sonuç olarak üretilen takip videosunu içerir (`street.mp4`).
- `src/`: Projenin kaynak kodlarını barındırır.
  - `task-1.ipynb`: Görev 1'i (Sınıflandırma) içeren notebook.
  - `task-2-3.ipynb`: Görev 2 (Tespit) ve Görev 3'ü (Takip) içeren notebook.
  - `sort.py`: SORT takip algoritmasının implementasyonu.
- `README.md`: Bu bilgilendirme dosyası.
- `report.pdf`: Projenin teknik detaylarını, sonuçlarını ve analizlerini içeren kapsamlı rapor.

---

## Kurulum ve Gereksinimler

```bash
pip install torch torchvision
pip install opencv-python matplotlib pandas
pip install filterpy
```
Proje, Kaggle Notebook ortamında, bir NVIDIA GPU (P100) kullanılarak geliştirilmiş ve test edilmiştir.

---

## Nasıl Çalıştırılır?

Projenin çıktılarını baştan sona oluşturmak için notebook'lar aşağıdaki sırayla çalıştırılmalıdır:

1.  **Önce `task-1.ipynb` Çalıştırılır:**
    * Bu notebook, Görev 1'i gerçekleştirir.
    * CIFAR-10 veri setini otomatik olarak indirir.
    * CNN modelini eğitir ve `models/cifar10_classifier.pth` dosyasını oluşturur.

2.  **Sonra `task-2-3.ipynb` Çalıştırılır:**
    * Bu notebook, Görev 2 ve 3'ü gerçekleştirir.
    * "Add Data" menüsünden `PASCAL VOC 2012` ve bir `video` veri setinin eklenmesini gerektirir.
    * Faster R-CNN modelini eğitir ve `models/pascal_object_detector.pth` dosyasını oluşturur.
    * `sort.py` dosyasını oluşturur.
    * Son olarak, eğitilen modeli kullanarak video üzerinde nesne takibi yapar ve `output/street.mp4` dosyasını oluşturur.