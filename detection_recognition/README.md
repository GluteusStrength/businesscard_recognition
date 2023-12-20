# Business Card Recognition

This directory contains code for business card recognition, including object detection model training, data augmentation and text recognition.

## 파일 구조

- `train.ipynb`:  YOLOv5 모델 학습.
- `Data Augmentation.ipynb`: 데이터 증강 기법 구현.
- `Recognition.ipynb`: YOLO를 통한 Detection 후 Text Recognition 단계 구현.
- `EigenCAM_YOLOv5.ipynb`: 추가적으로 모델이 제대로 확인을 하는지 EigenCAM을 통하여 activation map을 확인하는 파일.

## Detection

### 1. train.ipynb

#### 1.1. Clone YOLOv5

ultralytics의 yolov5를 clone한다. 다음의 공식사이트에서 clone을 진행합니다.
<br/> (https://github.com/ultralytics/yolov5)

#### 1.2. Data Preparation

학습을 시키기 전 선행 작업으로는 이미지 파일을 적절하게 구성해야 합니다.
<br/> 원하는 데이터셋 저장 디렉터리를 생성하고 하위 디렉터리로 다음과 같이 구상하는 것이 좋습니다.
1. 원하는 저장 디렉터리의 하위 폴더로 images, labels 생성
2. images, labels 모두 각각 train, valid, test 폴더를 생성하여 데이터셋을 각각에 넣어줍니다.
<br/> ※ 이때 image와 label의 정보의 파일명은 맞춰주는 것이 좋습니다.
#### 1.3. 바운딩 박스 확인

학습 전에 `draw_bbox` 함수를 사용하여 올바른 바운딩 박스 형성을 확인합니다.
- `filenames_image`: 이미지 파일 경로를 저장. 적절하게 이미지가 저장된 파일의 경로를 설정하면 됩니다.
- `filenames_label`: label의 저장 경로가 저장됩니다. 앞서 이미지와 라벨 정보의 이름을 동일하게 취하게 되면 쉽게 뒤의 파일의 확장자명만 바꿔서 진행할 수 있게 구성했습니다.
- `classes`: label 정보의 클래스명.

#### 1.4. YAML 파일 생성

디렉터리, 클래스 수 및 클래스 이름을 지정하는 YAML 파일을 생성합니다.
<br> 추후에 학습 시 yaml 파일을 통해 데이터를 불러들이게 됩니다. 
  - `train`: train 이미지가 담겨있는 directory
  - `val`: valid 이미지가 담겨있는 directory
  - `nc`: number of classes
  - `names`: class의 이름

#### 1.5. YOLO 학습

YOLOv5의 `train.py`를 사용하여 학습을 시작합니다.
<br> 주요 argument
- --weights '가중치가 저장된 경로 입력'
- --data '앞서 지정한 yaml 파일'
- --img 이미지 입력 크기
- --batch 배치 사이즈
- --epochs 총 학습 에폭

### 2. Data Augmentation.ipynb

#### 2.1. 증강 기법

네 가지 데이터 증강 기법을 구현합니다.
1. 자르기
2. 노이즈
3. 회전
4. 명도/채도 조절

#### 2.2. 사용법

구현된 데이터 증강 기법을 사용하는 방법을 설명합니다.
- `Crop`
  -  make_crop 함수 실행
  -  make_crop 함수에는 bounding box 재정립하는 것이 들어있다.
-  `Noise`
    - make_noise 실행
    - 기본적으로 Gaussian Noise를 삽입
- `Rotation`
  - data_augmentation 함수 안에 들어있다.
<br> ※ data_augmentation 함수 셀 아래의 반복문 셀에서 tqdm(range(n))에서 n을 조정하여 증강 기법을 다양하게 사용할 수 있습니다. 그리고 이 때, data_augmentation에서도 `if num == k` 부분을 적당히 조정할 필요가 있을 수도 있습니다.
### 3.2. EigenCAM_YOLOv5.ipynb[추가 작업]

EigenCAM을 통해 activation map을 확인하는 파일입니다. 
<br> 주의할 점
- model은 torch.hub.load를 통해 불러옵니다. 이때 학습 시켰던 model의 체크포인트 파일을 활용하고자 한다면 `path = your checkpoint file path`
- target_layers의 경우 model의 특정 layer를 지정하는 부분입니다.
- 그 외에는 image_url에 확인하고자 하는 이미지 파일의 경로를 설정해주고 나머지 부분은 실행하면 됩니다.
 
### 3. Recognition.ipynb

#### 3.1. 객체 검출 및 텍스트 인식

YOLO 검출과 텍스트 인식을 결합합니다.
