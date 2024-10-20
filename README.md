# YOLOv7 Object Detection

YOLOv7 modelini kullanarak görüntülerde nesne tespiti yapmanıza olanak tanır. Proje, PyTorch framework'ü üzerine inşa edilmiştir ve görüntü veya video verileri üzerinde nesne tespiti gerçekleştirir.

## İçindekiler
- [Gereksinimler](#gereksinimler)
- [Kurulum](#kurulum)
- [Kullanım](#kullanım)
- [Argümanlar](#argümanlar)
- [Sonuçlar](#sonuçlar)

## Gereksinimler

Bu projeyi çalıştırmak için aşağıdaki yazılımlara ve paketlere ihtiyaç vardır:

- Python 3.7 veya üzeri
- PyTorch
- OpenCV
- CUDA (Eğer GPU ile çalıştırılacaksa)
  
Ek olarak, proje aşağıdaki Python kütüphanelerine de ihtiyaç duyar:

```bash
pip install torch opencv-python numpy
```

## Kurulum

1. Bu projeyi yerel makinenize klonlayın:

```bash
git clone https://github.com/simgekarabuga/object-detection.git
```

2. Gerekli Python bağımlılıklarını yükleyin:

```bash
pip install -r requirements.txt
```

3. [YOLOv7](https://github.com/WongKinYiu/yolov7) model dosyasını indirin ve projenin kök dizinine yerleştirin:

```bash
wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt
```

## Kullanım

Komut satırından aşağıdaki komutla nesne tespiti yapabilirsiniz:

```bash
python detect.py --weights yolov7.pt --source inference/images --img-size 640 --conf-thres 0.25
```

Bu komut, `inference/images` dizinindeki görüntüler üzerinde nesne tespiti yapacak ve sonuçları varsayılan olarak `runs/detect/exp` dizinine kaydedecektir.

### Webcam ile Tespit

Webcam üzerinden gerçek zamanlı nesne tespiti yapmak için:

```bash
python detect.py --weights yolov7.pt --source 0
```

`0`, varsayılan olarak sistemdeki ilk kamerayı kullanır.

### Video ile Tespit

Bir video dosyasında nesne tespiti yapmak için:

```bash
python detect.py --weights yolov7.pt --source path/to/video.mp4
```

### Video Akışı ile Tespit

Bir RTSP veya HTTP akışı üzerinde nesne tespiti yapmak için:

```bash
python detect.py --weights yolov7.pt --source rtsp://your_stream_url
```

## Argümanlar

- `--weights`: Kullanılacak model dosyasının yolu.
- `--source`: Görüntü veya video kaynağı (dizin, dosya, webcam veya URL).
- `--img-size`: Giriş görüntüsünün boyutu (piksel cinsinden).
- `--conf-thres`: Nesne tespiti için minimum güven eşiği.
- `--iou-thres`: Non-Maximum Suppression (NMS) için IoU (Intersection over Union) eşiği.
- `--device`: CUDA cihazını belirtir (örn. `0` veya `cpu`).
- `--save-txt`: Tespit edilen nesneleri bir metin dosyasına kaydeder.
- `--save-conf`: Metin dosyasına güven skorlarını da kaydeder.
- `--view-img`: Tespit edilen nesnelerle birlikte sonuçları görüntüler.
- `--augment`: İyileştirilmiş tespit modunu etkinleştirir.

## Sonuçlar

Sonuçlar, proje dizini içinde `runs/detect/exp` dizinine kaydedilir. Tespit edilen nesnelerin olduğu görüntüler bu dizine kaydedilir ve `--save-txt` argümanı kullanıldıysa, nesnelerin koordinatları metin dosyalarına kaydedilir.

## Resimler
![Project Image](https://github.com/user-attachments/assets/289ec14a-b35f-4cb6-8ff1-6c0a5925d956)
