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
