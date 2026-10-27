# PyTorch 샘플 노트북

PyTorch 기초부터 전이학습, 시퀀스 모델까지 단계별로 보여주는 Jupyter 노트북 모음입니다.

## 섹션

| # | 노트북 | 내용 |
|---|--------|------|
| 01 | [01_tensor_basics](01_tensor_basics/01_tensor_basics.ipynb) | 텐서 생성, 연산, 브로드캐스팅, 인덱싱, NumPy 변환, device |
| 02 | [02_autograd](02_autograd/02_autograd.ipynb) | 자동 미분, 계산 그래프, 수동 경사하강 |
| 03 | [03_linear_regression](03_linear_regression/03_linear_regression.ipynb) | `nn.Module`, 손실함수, 옵티마이저, 학습 루프 |
| 04 | [04_dataset_dataloader](04_dataset_dataloader/04_dataset_dataloader.ipynb) | 커스텀 `Dataset`, `DataLoader`, transform |
| 05 | [05_mnist_cnn](05_mnist_cnn/05_mnist_cnn.ipynb) | CNN으로 MNIST 분류, 모델 저장/불러오기 |
| 06 | [06_transfer_learning](06_transfer_learning/06_transfer_learning.ipynb) | FashionMNIST 일부 클래스로 사전학습한 CNN을 나머지 클래스에 전이 (freeze vs fine-tuning) |
| 07 | [07_sequence_models](07_sequence_models/07_sequence_models.ipynb) | 문자 단위 LSTM과 Transformer로 텍스트 생성 |

## 폴더 규칙

- 섹션마다 `NN_<topic>/` 폴더에 노트북 하나가 있습니다.
- 섹션이 쓰는 데이터는 그 섹션의 `data/` 폴더에만 저장합니다. 노트북은 상대경로 `data/`를 참조하므로 섹션별로 독립 실행됩니다.
- 작은 합성 데이터는 커밋되어 있고, 없으면 노트북이 다시 생성합니다.
- 다운로드 데이터(`data/downloads/`)와 학습된 모델(`data/*.pt`)은 git에서 제외됩니다.

## 환경 설정

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

GPU가 있으면 노트북이 자동으로 CUDA를 사용하고, 없으면 CPU에서 실행됩니다. 05~06은 첫 실행 때 인터넷에서 데이터셋(MNIST, FashionMNIST)을 내려받습니다.

## 명령줄에서 실행

```bash
# 노트북 하나 (nbconvert는 노트북이 있는 폴더를 작업 디렉터리로 사용)
jupyter nbconvert --to notebook --execute --inplace 03_linear_regression/03_linear_regression.ipynb

# 전체
jupyter nbconvert --to notebook --execute --inplace [0-9][0-9]_*/*.ipynb
```
