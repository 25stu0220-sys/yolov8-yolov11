# 🧠 YOLOv11 Object Detection Study

이 저장소는 **YOLOv11**을 학습하고 실습하기 위한 자료를 정리한 곳입니다.  
YOLO는 "You Only Look Once"의 약자로, 이미지나 영상에서 객체를 빠르고 정확하게 탐지하는 **객체 탐지(Object Detection)** 알고리즘입니다.

---

## 🚀 YOLOv11 소개

YOLOv11은 2025년에 공개된 최신 YOLO 시리즈로, 이전 버전인 **YOLOv8**보다 더 향상된 성능과 효율성을 제공합니다.  
특히 **속도, 정확도, 다양한 환경에서의 강건성(robustness)** 면에서 개선되었습니다.

---

## 📊 YOLOv8 vs YOLOv11 비교

| 항목 | YOLOv8 | YOLOv11 |
|------|---------|----------|
| **발표 시기** | 2023년 1월 | 2025년 10월 (예상) |
| **모델 구조** | CSP 기반 백본 + PAN-FPN | 개선된 CSPNet + Dynamic Head |
| **입력 크기** | 640×640 기본 | 자동 크기 조정 지원 (Dynamic Input) |
| **학습 속도** | 빠름 | 더 빠름 (GPU 최적화 강화) |
| **정확도 (mAP)** | 높음 | 약 3~5% 향상 |
| **지원 언어** | Python | Python, C++, ONNX 등 다중 언어 |
| **배포 편의성** | CLI 및 API 지원 | Docker / Edge AI / TensorRT 최적화 |
| **특징** | 실시간 객체 탐지에 최적화 | 경량화 + 대형 모델 모두 지원 |
| **활용 분야** | CCTV, 자율주행, 드론 등 | 모든 산업 응용 가능 (멀티도메인) |

---

## 📘 YOLO 주요 용어 정리

| 용어 | 의미 | 설명 |
|------|------|------|
| **BBox (Bounding Box)** | 경계 상자 | 객체를 감싸는 네모 상자 |
| **Confidence Score** | 신뢰도 점수 | 모델이 객체를 얼마나 확신하는지 나타냄 |
| **IoU (Intersection over Union)** | 교집합 비율 | 예측 박스와 실제 박스의 겹침 정도 |
| **mAP (mean Average Precision)** | 평균 정밀도 | 객체 탐지 성능의 대표적인 평가 지표 |
| **NMS (Non-Maximum Suppression)** | 비최대 억제 | 중복된 박스를 제거하는 과정 |
| **Anchor Box** | 기준 박스 | 다양한 크기의 객체를 잡기 위한 참조 박스 |
| **Epoch** | 학습 반복 횟수 | 전체 데이터를 몇 번 반복 학습했는지 표시 |
| **Batch Size** | 배치 크기 | 한 번에 학습하는 이미지 개수 |
| **Pretrained Weights** | 사전 학습 가중치 | 기존 학습된 모델을 기반으로 사용 |
| **Augmentation** | 데이터 증강 | 이미지 변형으로 학습 데이터 다양화 |

---

## 🧩 설치 및 환경 설정

### 1. 필수 환경
- Python ≥ 3.8  
- PyTorch ≥ 2.0  
- CUDA (GPU 사용 시)

### 2. 설치 방법
```bash
# YOLOv11 설치 (예시)
git clone https://github.com/ultralytics/yolov11.git
cd yolov11
pip install -r requirements.txt
# 🧠 YOLOv11 모델 비교 및 다운로드

아래 표는 YOLOv11의 다양한 모델 버전별 성능 및 사양을 비교한 것입니다.  
파란 글씨 모델명을 클릭하면 각 모델의 가중치(`.pt` 파일)를 다운로드할 수 있습니다.

---

## 📊 YOLOv11 모델 성능 비교

| Model | size (pixels) | mAP<sup>val</sup> 50–95 | Speed (CPU ONNX, ms) | Speed (T4 TensorRT10, ms) | Params (M) | FLOPs (B) |
|:------|:--------------:|:-----------------------:|:---------------------:|:---------------------------:|:-----------:|:----------:|
| [YOLO11n](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11n.pt) | 640 | 39.5 | 56.1 ± 0.8 | 1.5 ± 0.0 | 2.6 | 6.5 |
| [YOLO11s](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11s.pt) | 640 | 47.0 | 90.0 ± 1.2 | 2.5 ± 0.0 | 9.4 | 21.5 |
| [YOLO11m](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11m.pt) | 640 | 51.5 | 183.2 ± 2.0 | 4.7 ± 0.1 | 20.1 | 68.0 |
| [YOLO11l](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11l.pt) | 640 | 53.4 | 238.6 ± 1.4 | 6.2 ± 0.1 | 25.3 | 86.9 |
| [YOLO11x](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11x.pt) | 640 | 54.7 | 462.8 ± 6.7 | 11.3 ± 0.2 | 56.9 | 194.9 |

---

### 📥 사용 방법

모델을 다운로드하려면 위의 표에서 원하는 버전을 클릭하세요.  
예를 들어, YOLOv11n을 다운로드하려면 다음 명령어를 사용할 수 있습니다:

```bash
# YOLOv11n 다운로드
wget https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11n.pt

# 또는 Python 명령어로 사용
yolo predict model=yolo11n.pt source=images/

# 🧠 YOLOv11 모델 비교 및 다운로드

아래 표는 YOLOv11의 다양한 모델 버전별 성능 및 사양을 비교한 것입니다.  
파란 글씨 모델명을 클릭하면 각 모델의 가중치(`.pt` 파일)를 다운로드할 수 있습니다.

---

## 📊 YOLOv11 모델 성능 비교

| Model | size (pixels) | mAP<sup>val</sup> 50–95 | Speed (CPU ONNX, ms) | Speed (T4 TensorRT10, ms) | Params (M) | FLOPs (B) |
|:------|:--------------:|:-----------------------:|:---------------------:|:---------------------------:|:-----------:|:----------:|
| [YOLO11n](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11n.pt) | 640 | 39.5 | 56.1 ± 0.8 | 1.5 ± 0.0 | 2.6 | 6.5 |
| [YOLO11s](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11s.pt) | 640 | 47.0 | 90.0 ± 1.2 | 2.5 ± 0.0 | 9.4 | 21.5 |
| [YOLO11m](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11m.pt) | 640 | 51.5 | 183.2 ± 2.0 | 4.7 ± 0.1 | 20.1 | 68.0 |
| [YOLO11l](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11l.pt) | 640 | 53.4 | 238.6 ± 1.4 | 6.2 ± 0.1 | 25.3 | 86.9 |
| [YOLO11x](https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11x.pt) | 640 | 54.7 | 462.8 ± 6.7 | 11.3 ± 0.2 | 56.9 | 194.9 |

---

### 📥 사용 방법

모델을 다운로드하려면 위의 표에서 원하는 버전을 클릭하세요.  
예를 들어, YOLOv11n을 다운로드하려면 다음 명령어를 사용할 수 있습니다:

```bash
# YOLOv11n 다운로드
wget https://github.com/ultralytics/assets/releases/download/v0.0.0/yolo11n.pt

# 또는 Python 명령어로 사용
yolo predict model=yolo11n.pt source=images/
