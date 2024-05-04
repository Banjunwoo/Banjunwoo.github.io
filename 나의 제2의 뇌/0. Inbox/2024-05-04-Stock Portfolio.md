---
use_math: true
layout: single
---


$$
R_{p,t}=w_1R_{1,t}+w_2R_{1,t}
$$
$when R = 수익률, w=투자비중$

>평균수익률
>왜 평균을 데이터의 대푯값으로? 편차가 작으면 작을수록 평균이 잘 표현되기 때문, 하나의 값이라는 개별데이터를 잘 대표함

$\bar{R_{p}}= w_{1}\bar{R_1}+w_{2}\bar{R_1}$

고든's Rule
$$P_0=\frac{D_1}{(r-g)}$$


### Sample Variacne

숫자가 100개가 있는데 랜덤하게 10개씩, 제곱합 하고 나누기 10 하면은 안 되고 나누기 9를 해야 모분산에 비슷하다.

$$ s^2=\dfrac{\sum\limits^n_{i=1}(x_i-x)^2}{n-1}$$
> note that Sample Standard deviation = s

평균절대편차 < S

## Algebraic identity

$$
V(X)=E(X^2)-(E(X))^2
$$
$$
\sum\limits^n_{i=1}(X_i-\bar{X}^{2})=E(X^2)-n\bar{X}^2
$$

## Correlation Coefficients
$$
\rho=\dfrac{\sum\limits^n_{i=1}(X_i-\bar{X})(Y_i-\bar{Y})}{(n-1)s_xs_y}
$$
$$
$$
### 수익률분산

$$\sigma^2_p=w_1^2\sigma_1^2+w^2_2\sigma^2_2+2w_1w_2\sigma_{1,2}
=w_1^2\sigma_1^2+w^2_2\sigma^2_2+2w_1w_2\rho_1\rho_2\sigma_1\sigma_2$$


여기서 $\sigma_{1,2}$ 가 0이라면, 두 주식은 독립적
독립적이라면, 포트폴리오의 분산은 작아짐
