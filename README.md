# 🖌️ Sketch Image Classification Competition

대회는 [upstage](https://stages.ai/)에서 비공개로 진행되었으며 데이터셋과 평가방식은 모두 upstage 제공 방식으로 이뤄져 있습니다.

---

## 📌 대회 개요

스케치는 인간의 상상력과 개념 이해를 반영하는 추상적이고 단순화된 형태의 이미지입니다.  
색상, 질감, 세부적인 형태가 결여되어 있으며, 기본적인 형태와 구조에 초점을 맞춥니다.  
스케치 데이터를 활용해 모델이 객체의 본질을 인식하도록 학습시키고, 창의적인 이미지 처리 능력을 키우는 것이 본 대회의 핵심입니다.

---

## 👥 팀원 소개

<table>
   </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/7c44b0c5-927a-4c65-8d21-8e240bcf1618" width="130px;" alt="강대민"/><br />
      <b>강대민 (T7101)</b><br />
      Train 데이터 분석, <br />ViT 시각화
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/fc431d0d-51d5-4774-b900-67bc6a2bb2b5" width="130px;" alt="김홍주"/><br />
      <b>김홍주 (T7142)</b><br />
      Cutmix & Mixup <br />Augmentation 구현
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/ddebfbe1-317d-4bf7-915c-524e51e5bd69" width="130px;" alt="박나영"/><br />
      <b>박나영 (T7147)</b><br />
      전처리, <br />Augmentation 실험
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/b17ce868-5498-4acf-8831-31829f8f7cbd" width="130px;" alt="서승환"/><br />
      <b>서승환 (T7161)</b><br />
      기본 모델 구축, <br />앙상블 부스팅, <br />오답 이미지 추출 기능 개발
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/d155ec79-8d03-45d4-b703-44a848b9b463" width="130px;" alt="이종서"/><br />
      <b>이종서 (T7171)</b><br />
      제공 데이터 분석, <br />로그 관리
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/9a15231a-b69d-447f-9070-f58b29ccdcec" width="130px;" alt="이한성"/><br />
      <b>이한성 (T7232)</b><br />
      모델 구조 수정, 모듈화, <br />학습 시각화 및 자동화, <br />하이퍼파라미터 튜닝
  </tr>
</table>

---
## 🗂️ Data

- [ImageNet Sketch 데이터셋](https://github.com/HaohanWang/ImageNet-Sketch) 기반
- Upstage에서 선정한 **상위 500개 클래스**, **총 25,035개 이미지**

> 📏 **Evaluation Metric**: `Accuracy`
---

## 🧠 Model

- 사용 모델: [`eva02_large_patch14_448.mim_m38m_ft_in22k_in1k`](https://huggingface.co/timm/eva02_large_patch14_448.mim_m38m_ft_in22k_in1k)
- 단일 모델 기준 가장 우수한 성능

---

## ⚙️ Usage

### 🔧 Installation
```bash
# 1. Clone the repository
git clone https://github.com/your-username/sketch-image-classification.git
cd sketch-image-classification

# 2. Install requirements
pip install -r requirements.txt

# 3. Unzip data
cd data
tar -zxvf data.tar.gz
```

### 🏋️‍♀️ Training
```bash
python train.py \
--traindata_dir ./data/train \
--traindata_info_file ./data/train.csv \
--save_result_path ./train_result \
--log_dir ./logs \
--val_split 0.2 \
--transform_type albumentations \
--batch_size 64 \
--model_type timm \
--model_name eva02_large_patch14_448.mim_m38m_ft_in22k_in1k \
--pretrained True \
--learning_rate 0.001 \
--epochs_per_lr_decay 2 \
--scheduler_gamma 0.1 \
--epochs 5
```

> `hyperparameter`는 자유롭게 조정 가능합니다.

### 🧪 Inference
```bash
python inference.py
```

---

## 📂 Project Structure

```
project_root/
│
├── data/
│   ├── train/
│   └── test/
│
├── src/
│   ├── __init__.py
│   ├── dataset.py
│   ├── transforms.py
│   ├── models.py
│   ├── trainer.py
│   ├── layer_modification/
│   └── utils.py
│
├── main.py
├── train.py
├── inference.py
├── requirements.txt
└── README.md
```

---

## 🧪 Experiment (~24.09.20)

### ✅ Experiment 규칙

1. 실험은 브랜치명 `exp/{실험내용}` 으로 올려주세요.  
2. 결과는 아래 구글 시트에 기록해주세요:  
   [🔗 Google Sheet](https://docs.google.com/spreadsheets/d/1tuTotQ_ALJQyJPzXt2NMeeyWfkm5csweRrYfWxnff8A/edit?usp=sharing)

### 🔖 브랜치 네이밍 규칙

- `main`: 절대 수정 ❌  
- 기능 구현: `feat/{기능명}`  
- 실험: `exp/{실험명}`  
- 수정: `fix/{수정명}`  

