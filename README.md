# PyTorch ImageNet VGG16

---

## none_avg_pool

### #1번

```python
        self.classifier = nn.Sequential(
            nn.Linear(512 * 7 * 7, 4096),
            nn.ReLU(True),
            nn.Dropout(),
            nn.Linear(4096, 4096),
            nn.ReLU(True),
            nn.Dropout(),
            nn.Linear(4096, 1000),
        )

    def forward(self, x):
        x = self.features(x)
        x = x.view(x.size(0), -1)
        x = self.classifier(x)
        return x
```

#### Epoch : 1 / Loss : 6.9131 / Time : 13.3H

### #2번

```python
        self.classifier = nn.Linear(7*7*512, 1000)

    def forward(self, x):
        x = self.features(x)
        x = x.view(x.size(0), -1)
        x = self.classifier(x)
        return x
```

#### Epoch : 1 / Loss : 6.3114 / Time : 14.4H

1번은 시간이 줄고, loss가 2번보다 높은 이유는 `nn.Dropuot()`역할 때문에 계산량은 줄었지만 loss가 더디게 떨어진다

---

## avg_pool

### #1-1번

```python
        self.classifier = nn.Sequential(
            nn.Linear(512, 4096),
            nn.ReLU(True),
            nn.Dropout(),
            nn.Linear(4096, 4096),
            nn.ReLU(True),
            nn.Dropout(),
            nn.Linear(4096, 1000),
        )
    
        self.avg_pool = nn.AvgPool2d(7)
    
    def forward(self, x):
        x = self.features(x)
        x = self.avg_pool(x)
        x = x.view(x.size(0),-1)
        x = self.classifier(x)
        
        return x
```

#### Epoch : 1 / Loss : 5.4063 / Time : 14.4H

### #2-1번

```python
        self.avg_pool = nn.AvgPool2d(7)
        self.classifier = nn.Linear(512, 4096)
    
    
    def forward(self, x):
        x = self.features(x)
        x = self.avg_pool(x)
        x = x.view(x.size(0),-1)
        x = self.classifier(x)
        
        return x
```

#### Epoch : 1 / Loss :4.9422 / Time : 14.4H



nn.Sequential<br>non_avg_pool, avg_pool

|   6.9131   |   5.4063   |
| :--------: | :--------: |
| **6.3114** | **4.9422** |

nnLinear<br>non_avg_pool, avg_pool

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

