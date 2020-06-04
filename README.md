# PyTorch ImageNet VGG16

---

## Enviroment	

OS : Ubuntu 18.04 LTS / GPU : RTX 2060 SUPER <br>

---

|       Model       |   Lr    | batch_size | batch_norm | Optim | Loss(1epoch) |
| :---------------: | :-----: | :--------: | :--------: | :---: | :----------: |
|      model1       | 0.00001 |     16     |     O      | Adam  |     6.7      |
| **model1(copy1)** |  0.001  |     16     |     O      | Adam  |     6.9      |
| **model1(copy2)** |  0.001  |     16     |     X      | Adam  |     6.9      |
| **model1(copy3)** |  0.001  |     16     |     X      |  SGD  |    6.908     |
|      model2       |  0.001  |     16     |     O      | Adam  |    6.911     |
|      model3       |  0.001  |     16     |     O      | Adam  |     6.90     |
|      model4       |  0.045  |     16     |     O      |  SGD  |     6.90     |
|     **Git1**      |  0.001  |     16     |     O      |  SGD  |     4.56     |
|  **Git1(copy)**   |  0.001  |     16     |     O      | Adam  |     6.90     |
|     **Git2**      |  0.001  |     8      |     O      |  SGD  |    4.578     |
|     **Git3**      |  0.001  |     16     |     X      |  SGD  |     6.9      |
|   ~~_model5_~~    |  0.001  |     8      |     X      | Adam  |              |
|   ~~_model6_~~    |  0.001  |     8      |     X      |  SGD  |              |
|   **Original1**   |  0.001  |     16     |     O      |  SGD  |     5.96     |
|   **Original2**   |  0.001  |     16     |     X      |  SGD  |     6.90     |
|      Result1      |  0.001  |     16     |     O      |  SGD  |     6.90     |
|      Result2      |  0.001  |     16     |     O      |  SGD  |     6.90     |
|      Result3      |  0.001  |     16     |     O      |  SGD  |     6.7      |

model : 기존 코드<br>Git : 기존코드3 + Original7<br>Result  = 기존코드7 + Original3

_model2_,_modelf3_ _VGG모델을 변경_<br>

---

### model1

epoch : 1 / loss : 6.7

---

### model1(copy1)

os : Windows / GTX 1080 Ti

epoch : 1 / loss : 6.9

---

### model1(copy2)

os : Windows / GTX 1080 Ti

epoch : 1 / loss : 6.9

---

### model1(copy3)

os : Windows / GTX 1080 Ti

epoch : 1 / loss : 6.908

---

### model2

epoch : 1 / loss : 6.9110 / Acc : 0.10%<br>epoch : 2 / loss : 6.9086 / Acc : 0.10%

---

### model3

epoch : 1 / loss : 6.907 / Acc : 0.23%<br>epoch : 2 / loss : 6.905 / Acc : 0.47%<br>epoch : 3 / loss : 6.903 / Acc : 0.65%

---

### model4

epoch : 1 / loss : 6.907 / Acc : 0.14%<br>epoch : 2 / loss : 6.907 / Acc : 0.18%<br>epoch : 3 / loss : 6.908 / Acc : 0.13%

---

### Git1

epoch : 1 / loss : 4.5598

---

### Git1(copy)

epoch : 1 / loss : 6.90

---

### Git2

epoch : 1 / loss : 5.7879

---

### Git3

os : Windows / GTX 1080 Ti

epoch : 1 / loss : 6.9

---

### ~~model5~~

---

### ~~model6~~

---

### Original1

epoch : 1 / loss : 5.96

epoch : 2 / loss : 4.88 (1/4 학습)

---

### Original2

epoch : 1 / loss : 6.9080

epoch : 2 / loss : 6.9077 (1/4 학습)

---

### Result1

transformNormalize

ImageFolder

Dropout

initalize_weights

epoch : 1 / loss : 6.9

---

### Result2

transformNormalize

ImageFolder

Dropout

initalize_weights

VGG

epoch : 1 / loss : 6.9080

---

### Result3

transformNormalize

ImageFolder

Dropout

initalize_weights

VGG

AverageMeter

epoch : 1 / loss : 6.7

---

