# Assignment 2 풀이 (Claude)

강의노트(Lec 2~7)의 기호와 풀이 방식을 우선 사용했다.

---

## Problem 2.1 — 3D 변형률-변위 관계

**Lec 2 p.10–11 "Rigorous derivation of strains"를 3D로 확장.**

미소요소의 한 점 A(x,y,z)가 변위 **u** = (u, v, w)만큼 이동한다. A에서 x방향으로 dx 떨어진 점 B의 변위는 Taylor 전개(1차)로

$$
u_B = u + \frac{\partial u}{\partial x}dx,\quad v_B = v + \frac{\partial v}{\partial x}dx,\quad w_B = w + \frac{\partial w}{\partial x}dx
$$

**(1) 수직변형률 ε_x**

변형 후 선분 A'B'의 길이:

$$
\overline{A'B'}^2 = \left(dx + \frac{\partial u}{\partial x}dx\right)^2 + \left(\frac{\partial v}{\partial x}dx\right)^2 + \left(\frac{\partial w}{\partial x}dx\right)^2
$$

정의에 의해 $\overline{A'B'} = (1+\varepsilon_x)dx$ 이므로

$$
2\varepsilon_x + \varepsilon_x^2 = 2\frac{\partial u}{\partial x} + \left(\frac{\partial u}{\partial x}\right)^2 + \left(\frac{\partial v}{\partial x}\right)^2 + \left(\frac{\partial w}{\partial x}\right)^2
$$

미소변형 가정($\varepsilon_x^2 \approx 0$, 변위 기울기의 제곱항 무시, 선형 변형률만 고려):

$$
\boxed{\varepsilon_x = \frac{\partial u}{\partial x}}
$$

같은 방법으로 y방향 선분(dy), z방향 선분(dz)에 적용하면

$$
\boxed{\varepsilon_y = \frac{\partial v}{\partial y},\qquad \varepsilon_z = \frac{\partial w}{\partial z}}
$$

**(2) 전단변형률 γ_xy**

xy평면에서 처음 직각이던 두 변 AB(x방향), AD(y방향)의 회전각:

- AB가 y쪽으로 기우는 각: $\theta_1 \approx \tan\theta_1 = \dfrac{\frac{\partial v}{\partial x}dx}{dx + \frac{\partial u}{\partial x}dx} = \dfrac{\partial v}{\partial x}\left(1+\dfrac{\partial u}{\partial x}\right)^{-1}$
- AD가 x쪽으로 기우는 각: $\theta_2 \approx \tan\theta_2 = \dfrac{\frac{\partial u}{\partial y}dy}{dy + \frac{\partial v}{\partial y}dy} = \dfrac{\partial u}{\partial y}\left(1+\dfrac{\partial v}{\partial y}\right)^{-1}$

공학 전단변형률 = 직각의 감소량(full angle change):

$$
\gamma_{xy} = \theta_1 + \theta_2 = \frac{\partial v}{\partial x}\left(1 - \frac{\partial u}{\partial x} + \cdots\right) + \frac{\partial u}{\partial y}\left(1 - \frac{\partial v}{\partial y} + \cdots\right)
$$

고차항 무시:

$$
\boxed{\gamma_{xy} = \frac{\partial v}{\partial x} + \frac{\partial u}{\partial y}}
$$

yz평면(y→z 변: w와 v), zx평면(z→x 변: u와 w)에서 똑같이 하면

$$
\boxed{\gamma_{yz} = \frac{\partial w}{\partial y} + \frac{\partial v}{\partial z},\qquad \gamma_{zx} = \frac{\partial u}{\partial z} + \frac{\partial w}{\partial x}}
$$

(참고: 텐서 표기로 $\varepsilon_{ij} = \frac12\left(\frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i}\right)$, $\gamma_{ij} = 2\varepsilon_{ij}$ — Lec 4 p.2)

---

## Problem 2.2 — 축대칭 반경방향 변위의 변형률

반지름 r, 각 θ 위치의 미소면적 요소 $dr \times r\,d\theta$ (꼭짓점 A, B=A+dr, D=A+r dθ)를 생각한다. 변위는 반경방향 성분 u(r)만 있고 θ에 무관하다.

**(1) ε_r (반경방향 변 AB)**

- A(반지름 r) → 변위 $u(r)$
- B(반지름 r+dr) → 변위 $u(r+dr) = u + \dfrac{du}{dr}dr$

변형 후 길이: $dr + \dfrac{du}{dr}dr$

$$
\varepsilon_r = \frac{\left(dr + \frac{du}{dr}dr\right) - dr}{dr} \;\Rightarrow\; \boxed{\varepsilon_r = \frac{du}{dr}}
$$

(Lec 2 p.7의 $\varepsilon_x = du/dx$와 같은 형태)

**(2) ε_θ (원주방향 변 AD)**

원호 AD의 두 끝점은 같은 반지름 r에 있으므로 똑같이 u만큼 반경방향으로 이동한다. 따라서 호는 반지름 r+u, 같은 중심각 dθ의 호가 된다.

$$
\varepsilon_\theta = \frac{(r+u)\,d\theta - r\,d\theta}{r\,d\theta} \;\Rightarrow\; \boxed{\varepsilon_\theta = \frac{u}{r}}
$$

**(3) γ_rθ**

- 반경방향 변 AB: A, B 모두 같은 반경선 위에서 반경방향으로만 움직이므로, 변형 후에도 같은 반경선 위에 있다.
- 원주방향 변 AD: A, D가 같은 양 u만큼 이동하므로, 변형 후에도 중심이 O인 원호 위에 있다.

반경선과 동심원호는 항상 직교하므로 요소의 직각이 유지된다 (각 변화 없음).

$$
\boxed{\gamma_{r\theta} = 0}
$$

(대칭 논리: 회전대칭이라 요소가 +θ쪽이나 −θ쪽으로 기울 이유가 없다.)

---

## Problem 2.3 — 얇은 원통 (내압 p + 축력 F)

**(a) 응력 유도 (자유물체도 + 힘 평형, Lec 2 방식)**

*원주응력 σ_θ*: 길이 L인 원통을 지름면으로 잘라 반쪽을 자유물체로 본다.
- 내압이 투영면적 $2rL$에 작용하는 합력: $p(2rL)$
- 잘린 두 벽 단면(각 $tL$)의 σ_θ에 의한 저항력: $2\sigma_\theta tL$

$$
\sum F = 2\sigma_\theta tL - p(2rL) = 0 \;\Rightarrow\; \boxed{\sigma_\theta = \frac{pr}{t}}
$$

*축응력 σ_z*: 축에 수직으로 자르면 벽 단면적은 $2\pi r t$ (얇은 벽, $t \ll r$). 이 단면이 축력 F를 받는다.

$$
\sum F_z = \sigma_z(2\pi r t) - F = 0 \;\Rightarrow\; \boxed{\sigma_z = \frac{F}{2\pi r t}}
$$

(문제에서 주어진 식에 맞추어 F를 벽이 받는 전체 축력으로 본다. 즉 끝판에 작용하는 압력의 합력 $p\pi r^2$은 F에 포함되거나 별도로 없는 것으로 가정.)

*반경응력 σ_r*: 내면에서 $\sigma_r = -p$, 외면에서 $\sigma_r = 0$이므로 $|\sigma_r| \le p$.

$$
\frac{|\sigma_r|}{\sigma_\theta} \le \frac{p}{pr/t} = \frac{t}{r} \ll 1 \;\Rightarrow\; \boxed{\sigma_r \approx 0}
$$

**주응력 정리**: 전단응력이 없으므로 (r, θ, z)가 주방향이고,
$a \equiv \sigma_\theta = \dfrac{pr}{t} > 0$, $b \equiv \sigma_z = \dfrac{F}{2\pi rt}$, $\sigma_r = 0$.

- 최대 수직응력 크기: $|\sigma|_{max} = \max(a, |b|)$
- 최대 전단응력 (Lec 5 p.6, 3D Mohr 원): $|\tau_{max}| = \dfrac12\max\left(|a-b|,\ a,\ |b|\right)$

**(b) $|\tau_{max}| = |\sigma|_{max}$ 조건**

$$
\max(|a-b|, a, |b|) = 2\max(a, |b|)
$$

그런데 $|a-b| \le a + |b| \le 2\max(a,|b|)$ 이고 $a, |b| < 2\max(a,|b|)$ 이므로 등호는 **b < 0 (a와 부호 반대) 이면서 |b| = a** 일 때만 성립한다.

$$
\frac{F}{2\pi r t} = -\frac{pr}{t} \;\Rightarrow\; \boxed{F = -2\pi r^2 p}
$$

즉 크기 $2\pi r^2 p$의 **압축** 축력. 이때 $\sigma_\theta = pr/t$, $\sigma_z = -pr/t$, Mohr 원(θ–z)의 반지름 = $pr/t$ = 최대 수직응력.

**(c) $|\tau_{max}| = \frac12|\sigma|_{max}$ 조건**

$$
\max(|a-b|, a, |b|) = \max(a, |b|) \iff |a-b| \le \max(a, |b|)
$$

- $b \ge 0$ (인장, F ≥ 0): a, b 모두 양수이므로 $|a-b| \le \max(a,b)$ 항상 성립 → 조건 만족. 최대 전단은 σ_r = 0을 포함한 가장 큰 Mohr 원에서 $\max(a,b)/2$.
- $b < 0$ (압축): $|a-b| = a + |b| > \max(a,|b|)$ → 불가.

$$
\boxed{F \ge 0\ \ \text{(인장 축력이면 크기에 관계없이 항상 성립)}}
$$

---

## Problem 2.4 — 얇은 구 (내압 p)

**(a) r, θ, φ가 주방향인 이유 (대칭)**

- 구와 하중(균일 내압)은 벽의 임의의 점에서, 그 점을 지나는 반경선을 축으로 한 **어떤 회전에도 불변**이다. 그러므로 그 점의 접평면 안에서는 모든 방향이 동등하다. 접평면에서 수직응력이 방향에 따라 달라지거나 전단응력 $\tau_{\theta\phi}$가 있으면 이 회전대칭이 깨진다 → $\tau_{\theta\phi} = 0$, $\sigma_\theta = \sigma_\phi$.
- 반경선을 포함하는 평면(예: r–θ 평면)에 대한 **거울대칭**에서도 형상과 하중이 불변이다. $\tau_{r\phi}$는 이 반사에서 부호가 바뀌어야 하므로 0, 같은 논리로 $\tau_{r\theta} = 0$.

모든 전단응력이 0 → 응력행렬이 (r, θ, φ) 좌표에서 대각 → **r, θ, φ가 주방향** (Lec 4 p.6: 주평면에는 전단응력 없음, $\vec t = \sigma_p \hat n$).

**(b) 주응력 크기**

구를 중심을 지나는 평면으로 잘라 반구 하나를 자유물체로 본다.
- 내압의 합력 (투영면적 $\pi r^2$): $p\,\pi r^2$
- 잘린 벽 단면(원환, 면적 ≈ $2\pi r t$)의 응력 합력: $\sigma_\theta (2\pi r t)$

$$
\sigma_\theta(2\pi r t) = p\pi r^2 \;\Rightarrow\; \boxed{\sigma_\theta = \frac{pr}{2t}}
$$

(a)의 결과 $\sigma_\phi = \sigma_\theta$ (또는 다른 방향으로 잘라도 같은 식) →

$$
\boxed{\sigma_\phi = \frac{pr}{2t}}
$$

σ_r은 원통과 같이 $-p \le \sigma_r \le 0$ 이므로 $|\sigma_r|/\sigma_\theta \le 2t/r \ll 1$ →

$$
\boxed{\sigma_r \approx 0}
$$

---

## Problem 2.5 — 자유 경계의 조건 (Cauchy 공식)

경계 AB는 수평과 α의 각을 이루며 오른쪽 아래로 내려간다. AB 방향 단위벡터는 $(\cos\alpha, -\sin\alpha)$이고, 그림처럼 바깥쪽(위-오른쪽)을 향하는 단위법선은

$$
\hat n = \begin{bmatrix} \sin\alpha \\ \cos\alpha \end{bmatrix}
$$

(검산: $\hat n \cdot (\cos\alpha, -\sin\alpha) = 0$, $|\hat n| = 1$)

Cauchy 공식 (Lec 4 p.4) $\vec t = \sigma \hat n$:

$$
\begin{bmatrix} t_x \\ t_y \end{bmatrix} = \begin{bmatrix} \sigma_x & \tau_{xy} \\ \tau_{xy} & \sigma_y \end{bmatrix}\begin{bmatrix} \sin\alpha \\ \cos\alpha \end{bmatrix} = \vec 0
$$

$$
\boxed{\ \sigma_x \sin\alpha + \tau_{xy}\cos\alpha = 0,\qquad \tau_{xy}\sin\alpha + \sigma_y \cos\alpha = 0\ }
$$

동치 표현: $\sigma_x = -\tau_{xy}\cot\alpha$, $\sigma_y = -\tau_{xy}\tan\alpha$.
(두 식에서 $\sigma_x\sigma_y = \tau_{xy}^2$, 즉 $\det\sigma = 0$ — AB면은 주응력 0인 주평면이다.)

---

## Problem 2.6 — Mohr 원 (σ₁ = 50, σ₂ = 0, σ₃ = −30 MPa)

3D Mohr 원 (Lec 5 p.6): 세 원의 중심과 반지름

| 원 | 중심 | 반지름 |
|---|---|---|
| σ₁–σ₃ (큰 원) | (50 + (−30))/2 = 10 | (50 − (−30))/2 = **40** |
| σ₁–σ₂ | (50 + 0)/2 = 25 | 25 |
| σ₂–σ₃ | (0 + (−30))/2 = −15 | 15 |

스케치: σ축 위에 −30, 0, 50을 찍고, [−30, 50]을 지름으로 하는 큰 원 안에 [0, 50], [−30, 0]을 지름으로 하는 두 작은 원이 서로 원점에서 접하도록 그린다. (τ축은 강의노트처럼 아래쪽이 +)

σ₂ = 0이 면외방향(평면응력)이므로 면내 주응력은 σ₁ = 50, σ₃ = −30이고,

$$
\boxed{\tau_{max}^{\text{in-plane}} = \frac{\sigma_1 - \sigma_3}{2} = \frac{50-(-30)}{2} = 40\ \text{MPa}}
$$

작용면: σ₁, σ₃ 주방향에서 45° 회전한 면, 그 면의 수직응력 = 중심값 10 MPa. 이 값은 절대 최대 전단응력과도 같다 (가장 큰 원).

---

## Problem 2.7 — 3D 주응력과 방향코사인

$$
\sigma = \begin{bmatrix} 220 & -80 & 0 \\ -80 & 220 & 40 \\ 0 & 40 & 0 \end{bmatrix}\ \text{MPa}
$$

**(a) 불변량 (Lec 5 p.3)**

$$
I_1 = 220 + 220 + 0 = 440
$$

$$
I_2 = (220)(220) + (220)(0) + (0)(220) - (-80)^2 - 40^2 - 0^2 = 48400 - 6400 - 1600 = 40400
$$

$$
I_3 = \sigma_x\sigma_y\sigma_z - \sigma_x\tau_{yz}^2 - \sigma_y\tau_{zx}^2 - \sigma_z\tau_{xy}^2 + 2\tau_{xy}\tau_{yz}\tau_{zx} = 0 - 220(1600) - 0 - 0 + 0 = -352000
$$

특성방정식: $\sigma_p^3 - 440\sigma_p^2 + 40400\sigma_p + 352000 = 0$

**삼각함수 해 (Lec 5 p.4)**

$$
\sqrt{I_1^2 - 3I_2} = \sqrt{193600 - 121200} = \sqrt{72400} = 269.07
$$

$$
\phi = \frac13\arccos\left(\frac{2I_1^3 - 9I_1I_2 + 27I_3}{2(I_1^2-3I_2)^{3/2}}\right) = \frac13\arccos\left(\frac{170368000 - 159984000 - 9504000}{2(72400)^{3/2}}\right) = \frac13\arccos(0.02259) = 0.5161\ \text{rad}
$$

$$
\sigma_1 = \tfrac{440}{3} + \tfrac23(269.07)\cos(0.5161) = 146.67 + 156.02 = 302.7\ \text{MPa}
$$

$$
\sigma_{(2)} = 146.67 + 179.38\cos(0.5161 + 2\pi/3) = -8.003\ \text{MPa}
$$

$$
\sigma_{(3)} = 146.67 + 179.38\cos(0.5161 + 4\pi/3) = 145.3\ \text{MPa}
$$

크기순으로 정렬:

$$
\boxed{\sigma_1 = 302.7\ \text{MPa},\quad \sigma_2 = 145.3\ \text{MPa},\quad \sigma_3 = -8.003\ \text{MPa}}
$$

검산: 합 = 440.0 = I₁ ✓, 곱 = −352000 = I₃ ✓

**(b) σ₁의 방향코사인 (Lec 5 p.10 외적 방법)**

$$
(\sigma - \sigma_1 I) = \begin{bmatrix} -82.69 & -80 & 0 \\ -80 & -82.69 & 40 \\ 0 & 40 & -302.69 \end{bmatrix}
$$

첫째, 둘째 행벡터 $\vec r_1, \vec r_2$에 모두 수직인 벡터:

$$
\vec x_1 \sim \vec r_1 \times \vec r_2 = \begin{vmatrix} \hat e_1 & \hat e_2 & \hat e_3 \\ -82.69 & -80 & 0 \\ -80 & -82.69 & 40 \end{vmatrix} = \begin{bmatrix} (-80)(40) - 0 \\ 0 - (-82.69)(40) \\ (-82.69)^2 - (-80)(-80) \end{bmatrix} = \begin{bmatrix} -3200 \\ 3307.5 \\ 437.1 \end{bmatrix}
$$

$|\vec x_1| = 4622.6$ 으로 정규화 (부호는 반대로 잡아도 같은 면):

$$
\boxed{\hat n_1 = (l_1, m_1, n_1) = (0.6922,\ -0.7155,\ -0.0946)}
$$

검산: $l^2 + m^2 + n^2 = 1$ ✓, $\sigma\hat n_1 = 302.7\,\hat n_1$ ✓ (셋째 행: $40(-0.7155) + 0 = -28.62 = 302.7 \times (-0.0946)$)

(참고: $\hat n_2 = (0.7184, 0.6707, 0.1846)$ for σ₂ = 145.3, $\hat n_3 = (-0.0687, -0.1957, 0.9783)$ for σ₃ = −8.003)

---

## Problem 2.8 — 변형에너지 밀도와 불변량

주어진 Hooke 법칙을 대입 (Lec 7 p.4와 같은 과정):

$$
u = \frac12\sum_i \sigma_i e_i = \frac{1}{2E}\left[\sigma_1^2 + \sigma_2^2 + \sigma_3^2 - 2\nu(\sigma_1\sigma_2 + \sigma_2\sigma_3 + \sigma_3\sigma_1)\right]
$$

주좌표에서 $I_1 = \sigma_1 + \sigma_2 + \sigma_3$, $I_2 = \sigma_1\sigma_2 + \sigma_2\sigma_3 + \sigma_3\sigma_1$ 이고

$$
\sigma_1^2 + \sigma_2^2 + \sigma_3^2 = I_1^2 - 2I_2
$$

**(a)**

$$
u = \frac{1}{2E}\left[I_1^2 - 2I_2 - 2\nu I_2\right] \;\Rightarrow\; \boxed{u = \frac{1}{2E}\left[I_1^2 - 2(1+\nu)I_2\right]}
$$

**(b)** $I_1 = 0$ 이면

$$
u = -\frac{(1+\nu)}{E}I_2 = -\frac{I_2}{\;\dfrac{E}{1+\nu}\;} = -\frac{I_2}{2G}\qquad \left(G = \frac{E}{2(1+\nu)} \Rightarrow \frac{E}{1+\nu} = 2G\right)
$$

$$
\boxed{u = -\frac{I_2}{2G}}
$$

(의미: I₁ = 0이면 정수압 성분 σ̄ = I₁/3 = 0이므로 변형에너지가 전부 편차(distortion) 에너지이다. Lec 7 p.6의 $\hat U_0 = \frac{1}{6G}(I_1^2 - 3I_2)$에 I₁ = 0을 넣어도 $-I_2/(2G)$로 일치.)

---

## Problem 2.9 — $I_2 \le \frac13 I_1^2$ 증명

불변량은 좌표에 무관하므로 주좌표에서 계산한다.

$$
I_1^2 = (\sigma_1 + \sigma_2 + \sigma_3)^2 = \sigma_1^2 + \sigma_2^2 + \sigma_3^2 + 2I_2
$$

$$
I_2 - \frac{I_1^2}{3} = \frac{3I_2 - (\sigma_1^2 + \sigma_2^2 + \sigma_3^2) - 2I_2}{3} = -\frac13\left[\sigma_1^2 + \sigma_2^2 + \sigma_3^2 - \sigma_1\sigma_2 - \sigma_2\sigma_3 - \sigma_3\sigma_1\right]
$$

괄호 안을 완전제곱으로 정리하면

$$
\boxed{I_2 - \frac{I_1^2}{3} = -\frac16\left[(\sigma_1 - \sigma_2)^2 + (\sigma_2 - \sigma_3)^2 + (\sigma_3 - \sigma_1)^2\right] \le 0}
$$

따라서 모든 응력상태에서 $I_2 \le \frac13 I_1^2$. 등호는 $\sigma_1 = \sigma_2 = \sigma_3$ (정수압 응력상태, Lec 6 p.8)일 때만 성립하므로, 정수압 상태가 아니면 문제의 부등식 $I_2 < \frac13 I_1^2$이 엄격하게 성립한다.

(강의노트 연결: Lec 7 p.5의 $\sum\hat\sigma_i^2 = \frac23(I_1^2 - 3I_2) \ge 0$ 으로도 바로 보일 수 있다 — 편차응력 제곱합은 음수가 될 수 없다.)
