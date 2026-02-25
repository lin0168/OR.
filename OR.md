

**ថ្ងៃពុធ ទី 11 ខែកុម្ភៈ ឆ្នាំ 2026**

> **ឈ្មោះសមាជិកក្រុម:**
> 1. រី ស្រីណែត (7)
> 1. រុន មួយហោង (10)
> 2. រ៉ន សុធារ៉ា (4)
> 3. វុន វិច្ឆរ៉ា (28)
> 4. ស៊ា សុលីន (36)

**ថ្នាក់:** **3D**

---

## លំហាត់ទី ២២
---
# 22. a. Determine the regression equation.

**តាង (Let):**
*   $Y$ = Daily Sales
*   $X_1$ = Store Area
*   $X_2$ = Parking Spaces
*   $X_3$ = Income

**តាមរូបមន្ត (Formula):**
MLR: $\hat{y} = b_0 + b_1X_1 + b_2X_2 + b_3X_3$

---

### តាមតារាងយើងគណនាបាន (Calculations from table):


| Summation | Value | Summation | Value |
| :--- | :--- | :--- | :--- |
| $\sum X_1$ | 8,220 | $\sum X_2$ | 92 |
| $\sum X_3$ | 743 | $\sum X_1 Y$ | 14,863,465 |
| $\sum X_2 Y$ | 166,729 | $\sum X_3 Y$ | 1,342,368 |
| $\sum Y$ | 28,920 | $\sum X_1 X_2$ | 47,976 |
| $\sum X_2 X_3$ | 4,243 | $\sum X_1^2$ | 4,931,152 |
| $\sum X_2^2$ | 564 | $\sum X_3^2$ | 34,607 |
| $\sum X_1 X_3$ | 381,669 | $n$ | 15 |

---

### Matrix Formulation

**តាង $X$ (Matrix $X$):**
$$X = \begin{bmatrix} 1 & 532 & 6 & 44 \\ 1 & 478 & 4 & 51 \\ 1 & 530 & 7 & 45 \\ \vdots & \vdots & \vdots & \vdots \\ 1 & 482 & 7 & 43 \end{bmatrix}$$

**រករាង $(X^T X)$ (Normal Equation Matrix):**
$$(X^T X) = \begin{bmatrix} n & \sum X_1 & \sum X_2 & \sum X_3 \\ \sum X_1 & \sum X_1^2 & \sum X_1 X_2 & \sum X_1 X_3 \\ \sum X_2 & \sum X_1 X_2 & \sum X_2^2 & \sum X_2 X_3 \\ \sum X_3 & \sum X_1 X_3 & \sum X_2 X_3 & \sum X_3^2 \end{bmatrix}$$

**ជំនួសតម្លៃ (Substituting values):**
$$(X^T X) = \begin{bmatrix} 15 & 8,220 & 92 & 743 \\ 8,220 & 4,931,152 & 47,976 & 381,669 \\ 92 & 47,976 & 564 & 4,243 \\ 743 & 381,669 & 4,243 & 34,607 \end{bmatrix}$$
**ការគណនាសមីការ Multiple Linear Regression (MLR)**

**នោះម៉ាទ្រីសច្រាសនៃ $(X^T X)^{-1}$ គឺ៖**

$$(X^T X)^{-1} = \begin{bmatrix} 88.5827 & -8.78177 & -6.549371 & -0.845196 \\ -0.08781 & 1.480315 & -5.06807 & 0.000351 \\ -0.65493 & -5.06807 & 3.751051 & 1.00397 \\ -0.84519 & 2.515805 & 1.00397 & 0.016111 \end{bmatrix}$$

---

**ម្យ៉ាងទៀត $X^T Y$ គឺ៖**

$$X^T Y = \begin{bmatrix} \sum Y \\ \sum X_1 Y \\ \sum X_2 Y \\ \sum X_3 Y \end{bmatrix} = \begin{bmatrix} 27105 \\ 13988635 \\ 154023 \\ 1264323 \end{bmatrix}$$

---

**តាមរូបមន្ត $\beta = (X^T X)^{-1} (X^T Y)$ យើងទទួលបាន៖**

$$\beta = \begin{bmatrix} 1480.7446116 \\ 0.7314989 \\ 9.9914874 \\ -2.3082627 \end{bmatrix}$$

**នាំឱ្យមេគុណស្មើនឹង៖**
* $b_0 = 1480.7446116$
* $b_1 = 0.7314989$
* $b_2 = 9.9914874$
* $b_3 = -2.3082627$

---

### យើងបានសមីការ (Final Regression Equation)

$$\Rightarrow MLR: \hat{y} = b_0 + b_1 X_1 + b_2 X_2 + b_3 X_3$$

**ដូចនេះ:**
$$\hat{y} = 1480.7446116 + 0.7314989 X_1 + 9.9914874 X_2 - 2.3082627 X_3$$


---
### យើងក៏ធ្វើលំហាត់នេះតាម R Program ផងដែរ 
```R
> x1=c(532,478,530,508,514,556,541,513,532,537,499,510,490,516,482)
> x2=c(6,4,7,7,5,6,4,6,5,5,3,8,4,8,7)
> x3=c(44,51,45,46,44,46,49,52,46,46,48,47,48,45,43)
>
> y=c(1840,1746,1812,1806,1792,1825,1811,1803,1830,1827,1764,1825,1763,1846,1815)
> x=matrix(c(rep (1,15),x1,x2,x3), ncol=4,nrow=15)
> x
      [,1] [,2] [,3] [,4]
 [1,]    1  532    6   44
 [2,]    1  478    4   51
 [3,]    1  530    7   45
 [4,]    1  508    7   46
 [5,]    1  514    5   44
 [6,]    1  556    6   46
 [7,]    1  541    4   49
 [8,]    1  513    6   52
 [9,]    1  532    5   46
[10,]    1  537    5   46
[11,]    1  499    3   48
[12,]    1  510    8   47
[13,]    1  490    4   48
[14,]    1  516    8   45
[15,]    1  482    7   43

> xx=t (x)%*%x
> xx
     [,1] ​  [,2]  [,3]   [,4]
[1,]   15    7738    85    700
[2,] 7738 3998828 43902 360943
[3,]   85   43902   515   3942
[4,]  700  360943  3942  32758

> solve(xx)
             [,1]          [,2]          [,3]          [,4]
[1,]  88.52271857 -8.781773e-02 -6.549371e-01 -0.8451965188
[2,]  -0.08781773  1.480315e-04 -5.068072e-05  0.0002515805
[3,]  -0.65493706 -5.068072e-05  3.751051e-02  0.0100397572
[4,]  -0.84519652  2.515805e-04  1.003976e-02  0.0141111974

> xy=t (x)%*%y
> xy
         [,1]
[1,]    27105
[2,] 13988635
[3,]   154024
[4,]  1264323

> bete=solve(xx)%*%xy
> bete
           [,1]
[1,] 1480.7446116
[2,]    0.7314989
[3,]    9.9914874
[4,]   -2.3082627
```
---

## លំហាត់ទី ២៣
####  A. Determine the regression equation.

**តាង (Let):**
* $Y$ = Gross Profit
* $X_1$ = Number of Employees
* $X_2$ = Consecutive Dividends
* $X_3$ = Beginning Inventory

**តាមរូបមន្ត (Formula):**  
$MLR : \hat{y} = b_0 + b_1 X_1 + b_2 X_2 + b_3 X_3$

**តាមតារាង យើងអាចគណនា (Calculations from table):**
* $n = 16$
* $\sum Y = 51450$
* $\sum X_1 = 5275$
* $\sum X_2 = 882$
* $\sum X_3 = 51989$
* $\sum X_1 Y = 22,758,850$
* $\sum X_2 Y = 3,520,970$
* $\sum X_3 Y = 251,689,300$
* $\sum X_1 X_2 = 374,600$
* $\sum X_2 X_3 = 3,984,674$
* $\sum X_1 X_3 = 26,116,730$
* $\sum X_1^2 = 2,664,575$
* $\sum X_2^2 = 66,870$
* $\sum X_3^2 = 347,290,165$

---

### Matrix Formulation

* **តាង $X$ ជាម៉ាទ្រីស (Matrix X):**
> $$X = \begin{pmatrix} 1 & 140 & 12 & 1800 \\ 1 & 65 & 21 & 320 \\ 1 & 130 & 42 & 820 \\ \vdots & \vdots & \vdots & \vdots \\ 1 & 150 & 24 & 1300 \end{pmatrix}$$

**ម៉ាទ្រីស $(X^T X)$ (Normal Equations Matrix):**

$$(X^T X) = \begin{pmatrix} n & \sum X_1 & \sum X_2 & \sum X_3 \\ \sum X_1 & \sum X_1^2 & \sum X_1 X_2 & \sum X_1 X_3 \\ \sum X_2 & \sum X_1 X_2 & \sum X_2^2 & \sum X_2 X_3 \\ \sum X_3 & \sum X_1 X_3 & \sum X_2 X_3 & \sum X_3^2 \end{pmatrix}$$

**ជំនួសតម្លៃ (Substituting values):**

$$X^T X = \begin{pmatrix} 16 & 5275 & 882 & 51989 \\ 5275 & 2664575 & 374600 & 26116730 \\ 882 & 374600 & 66870 & 3984674 \\ 51989 & 26116730 & 3984674 & 347290165 \end{pmatrix}$$

**នោះម៉ាទ្រីសច្រាសនៃ $(X^T X)^{-1}$ គឺ៖**

$$(X^T X)^{-1} = \begin{pmatrix} 2.453364 & -1.995035 & -2.604604 & 8.160561 \\ -1.995035 & 2.461102 & -6.027668 & -8.605383 \\ -2.604604 & -6.027668 & 1.037929 & -3.476838 \\ 8.160561 & -8.605383 & -3.476838 & 1.211837 \end{pmatrix}$$


**ម្យ៉ាងវិញទៀត (Furthermore):**

$$X^T Y = \begin{pmatrix} \sum y \\ \sum x_1 y \\ \sum x_2 y \\ \sum x_3 y \end{pmatrix} = \begin{pmatrix} 965.2808939 \\ 2.8653231 \\ 6.7537560 \\ 0.2872553 \end{pmatrix}$$


**តាមរូបមន្ត (According to the formula):**  
$$\beta = (X^T X)^{-1} (X^T Y)$$ 
$$\Rightarrow \beta= \begin{pmatrix} 51450 \\ 22758850 \\ 3520970 \\ 251689300 \end{pmatrix}$$

**យើងទទួលបាន :**
* $b_0 = 965.2808939$
* $b_1 = 2.8653231$
* $b_2 = 6.7537560$
* $b_3 = 0.2872553$

**សមីការ MLR (MLR Equation):**
$$\hat{y} = b_0 + b_1 X_1 + b_2 X_2 + b_3 X_3$$
$$\Rightarrow \hat{y} = 965.2808939 + 2.8653231 X_1 + 6.7537560 X_2 + 0.2872553 X_3$$

---

### B. Interpret the Meaning of Slopes

* **$b_1 = 2.8653231$**  
  មានន័យថា ពេលដែល dividends and beginning inventory រក្សានៅថេរ បើចំនួនបុគ្គលិកកើនឡើង 1 នាក់ នោះប្រាក់ចំណេញ (Y) នឹងកើនឡើងប្រហែល 3 ឯកតា។
  <!-- *(Meaning: When dividends and beginning inventory remain constant, if the number of employees increases by 1, then gross profit (Y) will increase by approximately 3 units.)* -->

* **$b_2 = 6.7537560$**  
  មានន័យថា នៅពេលដែលចំនួនបុគ្គលិក និង beginning inventory ថេរ បើ dividends កើនឡើង នោះប្រាក់ចំណេញ (Y) នឹងកើនឡើងប្រហែល 7 ឯកតា។
  <!-- *(Meaning: When the number of employees and beginning inventory are constant, if dividends increase, then gross profit (Y) will increase by approximately 7 units.)* -->
### 23. (Continued)

+ **$b_3 = 0.2872553$**  
  មានន័យថានៅពេលដែលចំនួនបុគ្គលិក និង dividends នៅថេរ ហើយ beginning inventory កើនឡើង 1 ឯកតា នោះប្រាក់ចំណេញនឹងកើនឡើង ប្រហែល 0.287 ឯកតា។  
  *(Meaning: When the number of employees and dividends remain constant, if the beginning inventory increases by 1 unit, the gross profit will increase by approximately 0.287 units.)*

---

#### C. Interpret the meaning of the regression coefficient for $b_0$
**$b_0 = 965.2808939$**  
នៅពេលដែលចំនួនបុគ្គលិក dividends និង beginning inventory ស្មើ 0 នោះ ប្រាក់ចំណេញ នឹងកើនឡើង ប្រហែល 965 ឯកតា។  
*(Meaning: When the number of employees, dividends, and beginning inventory are all 0, the gross profit is approximately 965 units.)*

---

#### D. Prediction
មានសមីការ (Equation): $\hat{y} = 965.28 + 2.865 X_1 + 6.754 X_2 + 0.287 X_3$  
ប្រសិនបើ (Given): $X_1 = 1; X_2 = 2; X_3 = 3$

$$\Rightarrow \hat{y} = 965.28 + 2.865(1) + 6.754(2) + 0.287(3)$$
$$\text{ដូចនេះ (Therefore): } \hat{y} = 982.506$$

---

### C. Coefficient of Determination $r^2$

**តាមរូបមន្ត (Formula):**  
$$r^2 = \frac{SSR}{SST}$$

**ដោយ:**  
$$SST = \sum Y^2 - \frac{(\sum Y)^2}{n} = 16.23$$  
$$SSR = 13.41$$

**គណនាបាន (Calculation):**  
$$r^2 = \frac{13.41}{16.23} = 0.826 \approx 82.6\%$$

**ដូចនេះ (Therefore):**  
$$r^2 \approx 82.6\%$$

---

### D. Delete any independent variable

*   **Income:** $p = 0.012 < 0.05$ (ពិត - Significant)
*   **Size:** $p < 0.001$ (ពិត - Significant)

**ដូចនេះ** មិនលុបអថេរមួយណាឡើយ (Do not delete any variable).

---

### E. Residuals and normality assumption

*   **Jarque-Bera p-value:** $0.872$
*   **Residuals have symmetry:** Good

**ដូចនេះ**  Normality assumption no problem.

---

### F. Fitted values Vs residuals

*   **Residuals:** Good
*   **Funnel shape:** Good (No funnel shape detected)

**ដូចនេះ**  
*   Heteroscedasticity no problem.
*   Model = Good.
*   Family Size = Good.
*   **Assumptions no problem.**


---
### យើងក៏ធ្វើលំហាត់នេះតាម R Program ផងដែរ 
```R
> x1=c(140,65,130,115,390,670,205,40,480,810,120,590,440,280,650,150)
> x2=c(12,21,42,80,120,64,43,14,88,98,44,110,38,24,60,24)
> x3=c(1800 ,320,820,76,3600,8400,508,870,5500,9875,6500,9130,1200,890,1200,1300)
> 
> y=c(2800,1300,1230,1600,4500,5700,3150,640,3400,6700,3700,6440,1280,4160,3870,980)
> x=matrix(c(rep(1,16),x1,x2,x3),ncol=4,nrow=16)
> x
      [,1] [,2] [,3] [,4]
 [1,]    1  140   12 1800
 [2,]    1   65   21  320
 [3,]    1  130   42  820
 [4,]    1  115   80   76
 [5,]    1  390  120 3600
 [6,]    1  670   64 8400
 [7,]    1  205   43  508
 [8,]    1   40   14  870
 [9,]    1  480   88 5500
[10,]    1  810   98 9875
[11,]    1  120   44 6500
[12,]    1  590  110 9130
[13,]    1  440   38 1200
[14,]    1  280   24  890
[15,]    1  650   60 1200
[16,]    1  150   24 1300

> xx=t(x)%*%x
> xx
      [,1]     [,2]    [,3]      [,4]
[1,]    16     5275     882     51989
[2,]  5275  2664575  374600  26116730
[3,]   882   374600   66870   3984674
[4,] 51989 26116730 3984674 347290165

> solve(xx)
              [,1]          [,2]          [,3]          [,4]
[1,]  2.453364e-01 -1.995035e-04 -2.604604e-03  8.160561e-06
[2,] -1.995035e-04  2.461102e-06 -6.027668e-06 -8.605383e-08
[3,] -2.604604e-03 -6.027668e-06  1.037929e-04 -3.476838e-07
[4,]  8.160561e-06 -8.605383e-08 -3.476838e-07  1.211837e-08

> xy=t(x)%*%y
> xy
          [,1]
[1,]     51450
[2,]  22758850
[3,]   3520970
[4,] 251689300
> bete=solve(xx)%*%xy
> bete
            [,1]
[1,] 965.2808939
[2,]   2.8653231
[3,]   6.7537560
[4,]   0.2872553
```
---
## លំហាត់ទី ២៤
```R
> x1=c(190, 121, 161, 161, 179, 99, 114, 202, 184, 90, 181, 143, 132, 127, 153, 145, 174, 177, 188, 153, 150, 173, 163, 150, 139)
> x2=c(14, 15, 14, 14, 14, 14, 15, 14, 13, 14, 14, 15, 14, 14, 14, 14, 15, 15, 15, 15, 16, 13, 14, 15, 14)
> x3=c(53, 49, 44, 39, 53, 46, 42, 49, 37, 43, 48, 54, 44, 37, 50, 50, 52, 47, 49, 53, 58, 42, 46, 50, 45)
> x4=c(230, 370, 397, 181, 378, 304, 285, 551, 370, 135, 332, 217, 490, 220, 270, 279, 329, 274, 433, 333, 148, 390, 142, 343, 373)

> y=c(40.3, 39.6, 40.8, 40.3, 40.0, 38.1, 40.4, 40.7, 40.8, 37.1, 39.9, 40.4, 38.0, 39.0, 39.5, 40.6, 40.3, 40.1, 41.7, 40.1, 40.6, 40.4, 40.9, 40.1, 38.5)
> x=matrix(c(rep(1,25),x1,x2,x3,x4),ncol=5,nrow=25)
> x
      [,1] [,2] [,3] [,4] [,5]
 [1,]    1  190   14   53  230
 [2,]    1  121   15   49  370
 [3,]    1  161   14   44  397
 [4,]    1  161   14   39  181
 [5,]    1  179   14   53  378
 [6,]    1   99   14   46  304
 [7,]    1  114   15   42  285
 [8,]    1  202   14   49  551
 [9,]    1  184   13   37  370
[10,]    1   90   14   43  135
[11,]    1  181   14   48  332
[12,]    1  143   15   54  217
[13,]    1  132   14   44  490
[14,]    1  127   14   37  220
[15,]    1  153   14   50  270
[16,]    1  145   14   50  279
[17,]    1  174   15   52  329
[18,]    1  177   15   47  274
[19,]    1  188   15   49  433
[20,]    1  153   15   53  333
[21,]    1  150   16   58  148
[22,]    1  173   13   42  390
[23,]    1  163   14   46  142
[24,]    1  150   15   50  343
[25,]    1  139   14   45  373

> xx=t(x)%*%x
> xx
     [,1]    [,2]   [,3]   [,4]    [,5]
[1,]   25    3849    358   1180    7774
[2,] 3849  612555  55049 182491 1223026
[3,]  358   55049   5138  16953  110956
[4,] 1180  182491  16953  56392  366416
[5,] 7774 1223026 110956 366416 2684616

> solve(xx)
             [,1]          [,2]          [,3]          [,4]          [,5]
[1,] 25.511713049 -1.564751e-02 -1.8954295019  9.993004e-02 -2.047756e-03
[2,] -0.015647507  6.766347e-05  0.0010314042 -1.657402e-04 -5.520750e-06
[3,] -1.895429502  1.031404e-03  0.1665362812 -1.439384e-02  1.004122e-04
[4,]  0.099930035 -1.657402e-04 -0.0143938389  2.778662e-03  1.782448e-06
[5,] -0.002047756 -5.520750e-06  0.0001004122  1.782448e-06  4.424031e-06

> xy=t(x)%*%y
> xy
         [,1]
[1,]    998.2
[2,] 154206.6
[3,]  14297.5
[4,]  47148.0
[5,] 310708.4

> bete=solve(xx)%*%xy
> bete
             [,1]
[1,] 28.186258525
[2,]  0.031652240
[3,]  0.642266980
[4,] -0.041823083
[5,] -0.001140504

```
---
## លំហាត់ទី ២៥
```R
> income <- c(48157, 48568, 46816, 34876, 35478, 34465, 35026, 38599, 33315)
> age <- c(57.7, 60.7, 47.9, 38.4, 42.8, 35.4, 39.5, 65.6, 27.0)
> pop400 <- c(1,1,1,0,0,0,1,0,0)
> data <- data.frame(income, age, pop400)
> # A.
> cor(age, income)
[1] 0.7214069
> # B.
> model1 <- lm(income ~ age, data = data)
> summary(model1)

Call:
lm(formula = income ~ age, data = data)

Residuals:
   Min     1Q Median     3Q    Max 
 -7926  -2061  -1140   3815   6691 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)   
(Intercept)  22804.7     6255.2   3.646  0.00822 **
age            361.6      131.2   2.756  0.02825 * 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 4774 on 7 degrees of freedom
Multiple R-squared:  0.5204,	Adjusted R-squared:  0.4519 
F-statistic: 7.596 on 1 and 7 DF,  p-value: 0.02825

> # C.
> model1 <- lm(income ~ age, data = data)
> summary(model1)

Call:
lm(formula = income ~ age, data = data)

Residuals:
   Min     1Q Median     3Q    Max 
 -7926  -2061  -1140   3815   6691 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)   
(Intercept)  22804.7     6255.2   3.646  0.00822 **
age            361.6      131.2   2.756  0.02825 * 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 4774 on 7 degrees of freedom
Multiple R-squared:  0.5204,	Adjusted R-squared:  0.4519 
F-statistic: 7.596 on 1 and 7 DF,  p-value: 0.02825

> # D.
> model2 <- lm(income ~ age + pop400, data = data)
> # summary(model2)
> # E.
> summary(model2)

Call:
lm(formula = income ~ age + pop400, data = data)

Residuals:
    Min      1Q  Median      3Q     Max 
-6622.2  -109.1   731.7  1686.0  3063.6 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)   
(Intercept)  24865.3     4551.9   5.463  0.00157 **
age            250.5      102.4   2.445  0.05010 . 
pop400        6887.7     2500.7   2.754  0.03310 * 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 3427 on 6 degrees of freedom
Multiple R-squared:  0.7882,	Adjusted R-squared:  0.7176 
F-statistic: 11.16 on 2 and 6 DF,  p-value: 0.0095

> # F.
> hist(residuals(model2))
> qqnorm(residuals(model2))
> qqline(residuals(model2))
> # g.
> plot(fitted(model2), residuals(model2))
> abline(h = 0)
> 
```
---

## លំហាត់ទី ២៦
##  A. Correlation matrix and Multicollinearity

**តាង:**
* $y = \text{food}$
* $X_1 = \text{Income}$
* $X_2 = \text{Size}$

$\Rightarrow \text{MLR: } \hat{y} = b_0 + b_1 x_1 + b_2 x_2$

**តាមតារាងយើងបាន:**
* $\sum X_1 = 2017.08$
* $\sum X_2 = 90$
* $\sum Y = 121.68$
* $\sum X_1^2 = 197945.47$
* $\sum X_2^2 = 424$
* $\sum X_1 Y = 9955.40$
* $\sum X_1 X_2 = 7078.14$
* $n = 25$
* $\sum X_2 Y = 479.40$

**តាម** $\hat{\beta} = (X^T X)^{-1} (X^T Y)$:

$$
% \begin{pmatrix} 
% b_0 \\ 
% b_1 \\ 
% b_2 
% \end{pmatrix} = 
\ =
\begin{pmatrix} 
n & \sum X_1 & \sum X_2 \\ 
\sum X_1 & \sum X_1^2 & \sum X_1 X_2 \\ 
\sum X_2 & \sum X_1 X_2 & \sum X_2^2 
\end{pmatrix}^{-1} 
\begin{pmatrix} 
\sum Y \\ 
\sum X_1 Y \\ 
\sum X_2 Y 
\end{pmatrix}
$$

$$
= \begin{pmatrix} 
25 & 2017.08 & 90 \\ 
2017.08 & 197945.47 & 7078.14 \\ 
90 & 7078.14 & 424 
\end{pmatrix}^{-1} 
\begin{pmatrix} 
121.68 \\ 
9955.40 \\ 
479.40 
\end{pmatrix}
$$

$$
\hat{\beta} = \begin{pmatrix} 
2.844 \\ 
0.0061 \\ 
0.4248 
\end{pmatrix}
$$

**គេបាន MLR:** $\hat{y} = 2.844 + 0.0061x_1 + 0.4248x_2$

---

## B. Regression equation and interpretation

### + Regression equation:
$$\hat{y} = 2.844 + 0.0061x_1 + 0.4248x_2$$
$$\hat{food} = 2.844 + 0.0061(\text{Income}) + 0.4248(\text{Size})$$

<!-- > **ចំណាំ:** Income and food គិតជាពាន់ដុល្លារ / ឆ្នាំ -->

### + Interpretation:
* **Income:** បើចំណូលកើន $1000/ ឆ្នាំ ចំណាយអាហារកើន $6.10$
* **Size:** បន្ថែមសមាជិកគ្រួសារ 1 នាក់ នោះចំណាយអាហារកើន $425 / ឆ្នាំ។
### C. Coefficient of determination $r^2$

**តាម:** $r^2 = \frac{SSR}{SST}$

ដោយ $SST = \sum Y^2 - \frac{(\sum Y)^2}{n} = 16.23$
$SSR = 13.41$

**គេបាន:** 
$r^2 = \frac{13.41}{16.23} = 0.826 \approx 82.6\%$

**ដូចនេះ:** $r^2 \approx 82.6\%$

---

### D. Delete any independent variable

*   **Income:** $p = 0.012 < 0.05$ (ពិត)
*   **Size:** $p < 0.001$ (ពិត)

$\Rightarrow$ **មិនលុបអថេរមួយណាឡើយ**

---

### E. Residuals and normality assumption

*   Jarque-Bera $p\text{-value} = 0.872$
*   Residuals have symmetry good
$\Rightarrow$ **Normality assumption no problem**

---

### F. Fitted values Vs residuals

*   Residuals = good
*   Funnel shape = good
$\Rightarrow$ **Heteroscedasticity no problem**
*   Model = good
*   Family Size = good

$\Rightarrow$ **Assumptions no problem.**

---
### យើងក៏ធ្វើលំហាត់នេះតាម R Program ផងដែរ 
```R
> x1=c(73.98, 54.90, 94.14, 52.02, 65.70, 53.64, 79.74, 68.58, 165.60, 64.80, 138.42, 125.82, 77.58, 171.36, 82.08, 141.30, 36.90, 56.88, 71.82, 69.48, 54.36, 87.66, 38.16, 43.74, 48.42)
> x2=c(4, 2, 4, 1, 2, 4, 3, 4, 5, 1, 3, 1, 7, 2, 9, 3, 5, 4, 1, 3, 2, 5, 3, 7, 5)

> y=c(5.04, 4.08, 5.76, 3.48, 4.20, 4.80, 4.32, 5.04, 6.12, 3.24, 4.80, 3.24, 6.60, 4.92, 6.60, 5.40, 6.00, 5.40, 3.36, 4.68, 4.32, 5.52, 4.56, 5.40, 4.80)
> x=matrix(c(rep(1,25),x1,x2),ncol=3,nrow=25)
> x
      [,1]   [,2] [,3]
 [1,]    1  73.98    4
 [2,]    1  54.90    2
 [3,]    1  94.14    4
 [4,]    1  52.02    1
 [5,]    1  65.70    2
 [6,]    1  53.64    4
 [7,]    1  79.74    3
 [8,]    1  68.58    4
 [9,]    1 165.60    5
[10,]    1  64.80    1
[11,]    1 138.42    3
[12,]    1 125.82    1
[13,]    1  77.58    7
[14,]    1 171.36    2
[15,]    1  82.08    9
[16,]    1 141.30    3
[17,]    1  36.90    5
[18,]    1  56.88    4
[19,]    1  71.82    1
[20,]    1  69.48    3
[21,]    1  54.36    2
[22,]    1  87.66    5
[23,]    1  38.16    3
[24,]    1  43.74    7
[25,]    1  48.42    5

> xx=t(x)%*%x
> xx
        [,1]      [,2]    [,3]
[1,]   25.00   2017.08   90.00
[2,] 2017.08 197945.47 7078.14
[3,]   90.00   7078.14  424.00
 

> solve(xx)
             [,1]          [,2]          [,3]
[1,]  0.388113857 -2.503489e-03 -4.059010e-02
[2,] -0.002503489  2.868220e-05  5.258823e-05
[3,] -0.040590097  5.258823e-05  1.009642e-02
 
> xy=t(x)%*%y
> xy
         [,1]
[1,]  121.680
[2,] 9955.397
[3,]  479.400

> bete=solve(xx)%*%xy
> bete
          [,1]
[1,] 2.8435747
[2,] 0.0061289
[3,] 0.4247572
```
---
## លំហាត់ទី ២៧
```R
>x1=c(3.245, 3.278, 3.52, 3.74, 3.52, 3.421, 3.41, 3.63, 3.355, 3.08, 3.025, 3.146, 3.465, 3.245, 3.025)
> x2=c(0, 0, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 1, 0, 0)
 
> y=c(31.5, 33, 34.1, 35.4, 34.2, 34, 34.5, 35, 34.7, 32.5, 31.5, 32.2, 34, 32.8, 31.8)
> x=matrix(c(rep(1,15),x1,x2),ncol=3,nrow=15)
> x
      [,1]  [,2] [,3]
 [1,]    1 3.245    0
 [2,]    1 3.278    0
 [3,]    1 3.520    1
 [4,]    1 3.740    1
 [5,]    1 3.520    1
 [6,]    1 3.421    1
 [7,]    1 3.410    1
 [8,]    1 3.630    1
 [9,]    1 3.355    1
[10,]    1 3.080    0
[11,]    1 3.025    0
[12,]    1 3.146    0
[13,]    1 3.465    1
[14,]    1 3.245    0
[15,]    1 3.025    0

> xx=t(x)%*%x
> xx
       [,1]     [,2]   [,3]
[1,] 15.000  50.1050  8.000
[2,] 50.105 168.0292 28.061
[3,]  8.000  28.0610  8.000

> solve(xx)
           [,1]       [,2]       [,3]
[1,]  54.626215 -17.301012  6.0592467
[2,] -17.301012   5.493880 -1.9694578
[3,]   6.059247  -1.969458  0.9738726
 
> xy=t(x)%*%y
> xy
         [,1]
[1,]  501.200
[2,] 1677.761
[3,]  275.900

> bete=solve(xx)%*%xy
> bete
          [,1]
[1,] 23.447375
[2,]  2.774831
[3,]  1.307058
```
---

<link rel="stylesheet" href="style.css">
