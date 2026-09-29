# Assignment 2 최종 답안 + 개념 정리

> Claude와 Codex가 각자 독립적으로 푼 뒤 비교해서 정리한 최종본.
> 각 문제는 **① 핵심 개념 → ② 풀이(단계마다 "왜") → ③ 최종 답 → ④ 체크포인트** 순서.
> 공식은 강의노트(Lec 2~7)에 있는 것을 우선 사용했고, 출처를 `[Lec n p.m]`으로 표시했다.

## 0. 먼저 잡고 갈 큰 그림 [Lec 2 p.4, Lec 3 p.3]

고체역학 문제는 거의 항상 세 종류의 식으로 푼다.

| 식의 종류 | 내용 | 이 과제에서 |
|---|---|---|
| **평형** (힘 → 응력) | 자른 면의 응력 합력 = 외력 | 2.3, 2.4 (얇은 용기) |
| **적합/기하** (변위 → 변형률) | 변형률 = 변위의 기울기 | 2.1, 2.2 |
| **구성식** (응력 ↔ 변형률) | Hooke 법칙 | 2.8 |

그리고 "한 점의 응력 상태"를 다루는 도구:

- Cauchy 공식 $\vec t = \sigma\hat n$ → 어떤 면에 작용하는 힘 (2.5)
- 주응력 = 고유값, 주방향 = 고유벡터 (2.7)
- Mohr 원 → 최대 전단응력 (2.3, 2.6)
- 불변량 $I_1, I_2, I_3$ → 좌표와 무관한 양 (2.7, 2.8, 2.9)

---

## Problem 2.1 — 변위로부터 변형률 구하기

### ① 핵심 개념

- **변형률은 "변형 전후의 길이·각도 비교"로 정의된다** [Lec 2 p.7].
  - 수직변형률 ε: 길이 변화율 $\varepsilon = \dfrac{L'-L}{L}$ (공학 변형률)
  - 전단변형률 γ: 원래 직각이던 두 선분 사이 각의 **감소량** (full angle change)
- **미소변형 가정**: 변위의 기울기($\partial u/\partial x$ 등)가 1보다 훨씬 작다 → 제곱항은 버린다. 이걸 버리지 않으면 Green–Lagrange 변형률(비선형)이 된다 [Lec 2 p.10].
- **Taylor 전개**: 가까운 점의 변위는 $u(x+dx) \approx u(x) + \dfrac{\partial u}{\partial x}dx$. 즉 "변위의 차이 = 기울기 × 거리".

### ② 풀이

**Step 1. 이웃한 점의 변위를 쓴다.**
점 A(x,y,z)의 변위가 (u,v,w)이면, x방향으로 dx 떨어진 점 B의 변위는

$$u_B = u + \frac{\partial u}{\partial x}dx,\quad v_B = v + \frac{\partial v}{\partial x}dx,\quad w_B = w + \frac{\partial w}{\partial x}dx$$

> 왜? 변형률은 "두 점이 **서로** 얼마나 다르게 움직였나"로 생긴다. 똑같이 움직이면(강체 병진) 변형이 없다.

**Step 2. 변형 후 길이를 구한다 → ε_x**

A'B' 벡터 $= \left(dx + \frac{\partial u}{\partial x}dx,\ \frac{\partial v}{\partial x}dx,\ \frac{\partial w}{\partial x}dx\right)$

$$\overline{A'B'}^2 = (1+\varepsilon_x)^2dx^2 = \left[\left(1+\frac{\partial u}{\partial x}\right)^2 + \left(\frac{\partial v}{\partial x}\right)^2 + \left(\frac{\partial w}{\partial x}\right)^2\right]dx^2$$

$$2\varepsilon_x + \varepsilon_x^2 = 2\frac{\partial u}{\partial x} + \underbrace{\left(\frac{\partial u}{\partial x}\right)^2 + \left(\frac{\partial v}{\partial x}\right)^2 + \left(\frac{\partial w}{\partial x}\right)^2}_{\text{미소변형 → 무시}}$$

$$\Rightarrow\ \varepsilon_x = \frac{\partial u}{\partial x}$$

> 해석: x방향 선분의 길이 변화에는 **x방향 변위의 x방향 변화율**만 1차로 기여한다. v, w는 선분을 "기울게" 할 뿐 길이는 2차로만 바꾼다.

y방향(dy), z방향(dz) 선분에도 똑같이 → $\varepsilon_y = \partial v/\partial y$, $\varepsilon_z = \partial w/\partial z$.

**Step 3. 직각의 변화 → γ_xy** [Lec 2 p.8, p.11]

xy평면에서:

- x방향 변 AB가 y쪽으로 기우는 각: $\theta_1 \approx \dfrac{\partial v}{\partial x}$ (x로 갈수록 v가 변하는 만큼 기움)
- y방향 변 AD가 x쪽으로 기우는 각: $\theta_2 \approx \dfrac{\partial u}{\partial y}$

$$\gamma_{xy} = \theta_1 + \theta_2 = \frac{\partial v}{\partial x}\left(1+\frac{\partial u}{\partial x}\right)^{-1} + \frac{\partial u}{\partial y}\left(1+\frac{\partial v}{\partial y}\right)^{-1} \approx \frac{\partial v}{\partial x} + \frac{\partial u}{\partial y}$$

($\tan\theta \approx \theta$, $(1+x)^{-1} \approx 1 - x + \cdots$에서 고차항 무시)

yz, zx 평면도 같은 방식.

### ③ 최종 답

$$\boxed{\varepsilon_x = \frac{\partial u}{\partial x},\ \ \varepsilon_y = \frac{\partial v}{\partial y},\ \ \varepsilon_z = \frac{\partial w}{\partial z},\qquad \gamma_{xy} = \frac{\partial v}{\partial x} + \frac{\partial u}{\partial y},\ \ \gamma_{yz} = \frac{\partial w}{\partial y} + \frac{\partial v}{\partial z},\ \ \gamma_{zx} = \frac{\partial u}{\partial z} + \frac{\partial w}{\partial x}}$$

### ④ 체크포인트

- **γ vs e (텐서 전단변형률)**: $e_{xy} = \frac12\gamma_{xy}$ [Lec 2 p.8–9]. Mohr 원(변형률)에서 세로축이 γ/2인 이유가 이것 [Lec 6 p.2].
- Codex는 같은 결과를 "변형 후 두 접선벡터의 내적 = cos(π/2 − γ) ≈ γ"로 유도했다. 결론은 같고, 방법만 다르다.

---

## Problem 2.2 — 극좌표(축대칭)에서의 변형률

### ① 핵심 개념

- 2.1과 **똑같은 정의**(길이 변화율, 직각 변화)를 극좌표 요소 $dr \times r\,d\theta$에 적용하는 문제.
- 극좌표의 특이점: **반경방향으로만 움직여도 원주방향 길이가 변한다.** 원이 커지면 둘레가 늘어나니까. 이것이 $\varepsilon_\theta = u/r$ 항의 정체다.
- **대칭성 논증**: 회전대칭인 문제에서는 +θ쪽과 −θ쪽을 구별할 이유가 없다 → 한쪽으로 기우는 전단이 없다.

### ② 풀이

**Step 1. ε_r — 반경방향 변 (길이 dr)**

- 안쪽 끝(반지름 r) 변위: $u(r)$
- 바깥 끝(반지름 r+dr) 변위: $u(r) + \dfrac{du}{dr}dr$

$$\varepsilon_r = \frac{\left(dr + \frac{du}{dr}dr\right) - dr}{dr} = \frac{du}{dr}$$

> 1D 막대의 $\varepsilon = du/dx$ [Lec 2 p.7]와 완전히 같은 논리.

**Step 2. ε_θ — 원주방향 변 (길이 r dθ)**

두 끝점이 모두 반지름 r에 있으므로 **똑같이 u만큼** 바깥으로 이동 → 반지름 r+u, 중심각 dθ인 호가 된다.

$$\varepsilon_\theta = \frac{(r+u)\,d\theta - r\,d\theta}{r\,d\theta} = \frac{u}{r}$$

> 핵심: 원주방향 변위는 없는데도 원주방향 변형률이 생긴다. "곡선 좌표에서는 변위 성분과 변형률 성분이 1:1 대응하지 않는다."

**Step 3. γ_rθ — 직각이 유지되는가?**

- 반경방향 변: 두 점이 같은 반경선 위에서 반경방향으로만 이동 → 여전히 반경선 위
- 원주방향 변: 두 점이 같은 양 u만큼 이동 → 여전히 중심 O인 원호 위

반경선과 동심원은 항상 직교 → 직각 유지 → $\gamma_{r\theta} = 0$.

### ③ 최종 답

$$\boxed{\varepsilon_r = \frac{du}{dr},\qquad \varepsilon_\theta = \frac{u}{r},\qquad \gamma_{r\theta} = 0}$$

### ④ 체크포인트

- **평면변형률** = $\varepsilon_z = \gamma_{rz} = \gamma_{\theta z} = 0$. 이것이 $\sigma_z = 0$을 뜻하지는 않는다 (Codex 지적). 평면**응력**($\sigma_z = 0$)과 헷갈리지 말 것 [Lec 6 p.2].
- 두꺼운 원통, 회전 원판 문제에서 이 식을 다시 쓰게 된다.

---

## Problem 2.3 — 얇은 원통 (내압 p + 축력 F)

### ① 핵심 개념

- **자유물체도(FBD) + 힘 평형**으로 응력을 구한다 [Lec 2 p.2–3]. "잘라서, 잘린 면의 응력 합력이 외력과 평형."
- **투영면적 원리**: 곡면에 작용하는 균일 압력의 한 방향 합력 = 압력 × (그 방향에 수직인 투영면적). 반원통의 경우 $p \times 2rL$.
- **얇은 벽 근사** ($t/r \ll 1$): 벽 두께 방향 응력 변화를 무시하고 평균 응력(막응력)으로 본다.
- **주응력과 3D Mohr 원** [Lec 5 p.6]: 전단응력이 없으면 좌표축이 곧 주방향이다. 최대 전단응력은 **세 원 중 가장 큰 원의 반지름**이다. σ_r = 0도 세 번째 주응력으로 반드시 포함해야 한다.

### ② 풀이

**(a) Step 1. 원주응력 σ_θ** — 지름면으로 잘라 반원통(길이 L)을 FBD로

- 내압 합력: $p \times (2r)L$ (투영면적)
- 잘린 벽 두 곳의 저항력: $2 \times \sigma_\theta \times tL$

$$2\sigma_\theta tL = p(2rL) \ \Rightarrow\ \sigma_\theta = \frac{pr}{t}$$

**Step 2. 축응력 σ_z** — 축에 수직으로 자르기

벽 단면적 $= \pi[(r+t)^2 - r^2] = 2\pi rt + \pi t^2 \approx 2\pi rt$

$$\sigma_z(2\pi rt) = F\ \Rightarrow\ \sigma_z = \frac{F}{2\pi rt}$$

> ⚠ 해석: 문제에서 $\sigma_z = F/(2\pi rt)$를 주었으므로 **F = 벽이 받는 전체 축력**으로 본다. 만약 끝이 막힌 원통에 외력 $F_{ext}$가 따로 걸리면 $F = F_{ext} + p\pi r^2$로 먼저 바꿔야 한다. (F = 0, 막힌 원통이면 유명한 $\sigma_z = pr/2t$가 나온다.)

**Step 3. 반경응력 σ_r**

내면 $-p$ → 외면 0. 크기는 최대 p. $\dfrac{p}{pr/t} = \dfrac{t}{r} \ll 1$ → $\sigma_r \approx 0$.

**(b), (c) Step 4. 주응력으로 정리**

$$A = \sigma_\theta = \frac{pr}{t} > 0,\qquad B = \sigma_z = \frac{F}{2\pi rt},\qquad \sigma_r = 0$$

- 최대 수직응력 크기: $N = \max(A, |B|)$
- 최대 전단응력: $T = \dfrac{\max(0,A,B) - \min(0,A,B)}{2}$ (가장 큰 Mohr 원의 반지름)

B의 범위에 따라 경우를 나눈다 (Codex 표 채택):

| B의 범위 | 최대 주응력 | 최소 주응력 | N | T | T/N |
|---|---|---|---|---|---|
| $B \ge A$ | B | 0 | B | B/2 | 1/2 |
| $0 \le B \le A$ | A | 0 | A | A/2 | 1/2 |
| $-A \le B < 0$ | A | B | A | (A−B)/2 | 1/2 초과 ~ 1 |
| $B < -A$ | A | B | −B | (A−B)/2 | 1/2 초과 ~ 1 |

> 표의 핵심: **인장(B ≥ 0)이면 σ_r = 0이 최소 주응력이 되어 T = N/2가 자동으로 된다.** 압축이 들어와야 원이 0의 반대편으로 넘어가 T가 커진다.

**(b) T = N**: 표에서 T/N = 1은 $B = -A$에서만 가능.

$$\frac{F}{2\pi rt} = -\frac{pr}{t}\ \Rightarrow\ F = -2\pi r^2p$$

그림으로: σ_θ = +pr/t, σ_z = −pr/t → Mohr 원 중심이 원점, 반지름 pr/t = 최대 수직응력. (Lec 6 p.10의 **순수 비틀림**과 같은 모양의 원이다: τ_max = σ_max.)

**(c) T = N/2**: 표의 처음 두 행 → $B \ge 0$.

### ③ 최종 답

$$\boxed{\text{(a) } \sigma_r \approx 0,\ \ \sigma_\theta = \frac{pr}{t},\ \ \sigma_z = \frac{F}{2\pi rt}}$$

$$\boxed{\text{(b) } F = -2\pi r^2 p\ \ (\text{크기 } 2\pi r^2p\text{의 압축력})}\qquad \boxed{\text{(c) } F \ge 0\ \ (\text{모든 인장 축력, 특정 비례식 없음})}$$

### ④ 체크포인트

- **가장 흔한 실수: 2D Mohr 원만 그리는 것.** σ_θ와 σ_z만 보면 (c)에서 "|A − B|/2 = max/2"처럼 틀린 식이 나온다. σ_r = 0을 넣은 3D 원 세 개를 봐야 한다.
- (c)의 답이 "식"이 아니라 "범위"라서 이상해 보이지만, 표로 보면 자연스러운 결과다.
- 참고: p = 0이면 (b)는 F = 0에서만, (c)는 모든 F에서 성립한다 (Codex 추가 분석).

---

## Problem 2.4 — 얇은 구 (내압 p)

### ① 핵심 개념

- **대칭성 → 주방향**: 형상과 하중이 어떤 대칭 변환에 불변이면 응력도 그 변환에 불변이어야 한다. 전단응력은 방향성을 가지므로, 대칭이 "방향 구별"을 허용하지 않으면 0이 된다.
- **주평면의 정의** [Lec 4 p.6]: 전단응력이 없는 면, $\vec t = \sigma_p \hat n$ (힘이 면에 수직).
- 2.3과 같은 **FBD + 투영면적 원리**.

### ② 풀이

**(a) Step 1. 회전대칭**

벽의 한 점에서 반경축(r)을 중심으로 구를 아무리 돌려도 구와 내압은 그대로다.
→ 접평면 안의 모든 방향이 동등하다.
→ θ방향과 φ방향 응력이 달라서도, $\tau_{\theta\phi}$가 있어서도 안 된다. 둘 다 특정 방향을 "구별"하기 때문이다.
→ $\sigma_\theta = \sigma_\phi$, $\tau_{\theta\phi} = 0$

**Step 2. 거울대칭**

반경선을 포함하는 평면(예: r–θ면)에 대해 거울에 비춰도 구와 하중은 그대로다. 그런데 $\tau_{r\phi}$는 거울 반사에서 부호가 바뀐다. 불변이려면 $\tau_{r\phi} = -\tau_{r\phi} = 0$. 같은 논리로 $\tau_{r\theta} = 0$.

→ 응력행렬이 (r, θ, φ)에서 대각 → **r, θ, φ가 주방향**

**(b) Step 3. 반구 FBD**

- 내압 합력: $p \times \pi r^2$ (투영면적 = 원판)
- 잘린 벽(원환, 면적 ≈ $2\pi rt$)의 응력 합력: $\sigma_\theta \times 2\pi rt$

$$\sigma_\theta(2\pi rt) = p\pi r^2\ \Rightarrow\ \sigma_\theta = \frac{pr}{2t}$$

(a)에서 $\sigma_\phi = \sigma_\theta$. σ_r은 원통과 같은 이유로 ≈ 0.

### ③ 최종 답

$$\boxed{\text{(a) } \tau_{r\theta} = \tau_{\theta\phi} = \tau_{\phi r} = 0 \Rightarrow r, \theta, \phi \text{ 가 주방향}\qquad \text{(b) } \sigma_r \approx 0,\ \ \sigma_\theta = \sigma_\phi = \frac{pr}{2t}}$$

### ④ 체크포인트

- **구는 원통의 절반 응력**: 원통 σ_θ = pr/t vs 구 pr/2t. 같은 압력이면 구형 탱크가 더 얇아도 된다 (LNG 탱크가 구형인 이유).
- 접선 주응력이 **중복**(σ_θ = σ_φ)이므로 접평면 안의 임의의 두 직교 방향이 모두 주방향이다. 접평면 Mohr 원은 한 점으로 줄어든다 (Codex 추가).

---

## Problem 2.5 — 자유 경계의 응력 조건

### ① 핵심 개념

- **Cauchy 공식** [Lec 4 p.4]: 법선이 $\hat n$인 면에 작용하는 단위면적당 힘 $\vec t = \sigma\hat n$.
  - 뜻: "한 점의 응력행렬을 알면, 그 점을 지나는 **어떤 면**의 힘이든 계산된다."
- **자유 경계(stress-free)** = 그 면에 외력이 없음 → $\vec t = \vec 0$ (두 성분 모두).
- 법선벡터 = 방향코사인 (단위벡터).

### ② 풀이

**Step 1. 법선벡터 구하기**

AB는 수평과 α를 이루며 오른쪽 아래로 내려간다 → AB 방향 $(\cos\alpha, -\sin\alpha)$.
이에 수직이면서 위-오른쪽(자유면 바깥)을 향하는 단위벡터:

$$\hat n = \begin{bmatrix} \sin\alpha \\ \cos\alpha \end{bmatrix}$$

검산: 내적 $\sin\alpha\cos\alpha - \cos\alpha\sin\alpha = 0$ ✓, 크기 1 ✓

**Step 2. Cauchy 공식 대입**

$$\vec t = \begin{bmatrix} \sigma_x & \tau_{xy} \\ \tau_{xy} & \sigma_y \end{bmatrix}\begin{bmatrix} \sin\alpha \\ \cos\alpha \end{bmatrix} = \begin{bmatrix} \sigma_x\sin\alpha + \tau_{xy}\cos\alpha \\ \tau_{xy}\sin\alpha + \sigma_y\cos\alpha \end{bmatrix} = \vec 0$$

### ③ 최종 답

$$\boxed{\sigma_x\sin\alpha + \tau_{xy}\cos\alpha = 0,\qquad \tau_{xy}\sin\alpha + \sigma_y\cos\alpha = 0}$$

동치 표현 (면의 수직·전단 성분, Lec 3 응력변환식과 같은 꼴):

$$\sigma_n = \sigma_x\sin^2\alpha + \sigma_y\cos^2\alpha + 2\tau_{xy}\sin\alpha\cos\alpha = 0,\qquad \tau_n = (\sigma_x - \sigma_y)\sin\alpha\cos\alpha + \tau_{xy}(\cos^2\alpha - \sin^2\alpha) = 0$$

### ④ 체크포인트

- 두 식에서 $\sigma_x\sigma_y = \tau_{xy}^2$, 즉 $\det\sigma = 0$ → **자유 경계면은 주응력이 0인 주평면이다** (Lec 4 p.6 고유값 관점).
- 경계에 **평행한** 방향의 수직응력은 0이 아니어도 된다 (Codex 지적). 자유 경계라고 모든 응력이 0인 게 아니다.
- α의 정의(어느 쪽 각인지)에 따라 sin/cos이 바뀐다. 시험에서는 법선벡터를 먼저 명확히 쓰는 게 안전하다.

---

## Problem 2.6 — 3D Mohr 원 (σ₁ = 50, σ₂ = 0, σ₃ = −30 MPa)

### ① 핵심 개념 [Lec 5 p.6–7]

- 주응력 3개 → **Mohr 원 3개**: 각 원은 "두 주방향이 만드는 평면 안에서 면을 돌릴 때"의 (σ, τ) 궤적.
- 원 (i, j): 중심 $\dfrac{\sigma_i + \sigma_j}{2}$, 반지름 $\dfrac{|\sigma_i - \sigma_j|}{2}$
- 절대 최대 전단응력 = **가장 큰 원의 반지름** = $\dfrac{\sigma_1 - \sigma_3}{2}$
- 임의 방향 면의 (σ, τ)는 큰 원 안, 작은 두 원 밖의 영역에 있다.

### ② 풀이

| 원 | 중심 | 반지름 |
|---|---|---|
| 1–3 (큰 원) | (50 − 30)/2 = 10 | (50 + 30)/2 = **40** |
| 1–2 | 25 | 25 |
| 2–3 | −15 | 15 |

**스케치**: σ축에 −30, 0, 50을 찍는다. [−30, 50]을 지름으로 하는 큰 원을 그리고, 그 안에 [−30, 0]과 [0, 50]을 지름으로 하는 두 작은 원을 원점에서 서로 접하게 그린다. (τ축은 아래가 + — 강의노트 관례)

**"면내(in-plane)"의 해석**: σ₂ = 0은 **평면응력의 면외방향**으로 보는 것이 표준이다 [Lec 5 p.7 "Plane stress case"]. 그러면 면내 주응력은 50과 −30이고, 면내 Mohr 원 = 1–3 원이다.

$$\tau_{max}^{\text{in-plane}} = \frac{50 - (-30)}{2} = 40\ \text{MPa}$$

작용면: 두 주방향에서 45° 돌린 면, 그 면의 수직응력 = 중심 = 10 MPa.

### ③ 최종 답

$$\boxed{\tau_{max}^{\text{in-plane}} = 40\ \text{MPa}\ \ (= \text{절대 최대 전단응력})}$$

> 답안 작성 팁: 세 원의 반지름 **40, 25, 15**를 모두 적고 "면내(σ₁–σ₃ 평면) = 40 MPa"로 결론. Codex는 σ₁–σ₂ 평면을 면내로 보는 해석(25 MPa)도 제시했다. 이렇게 두 해석을 모두 보여주면 채점 기준이 어느 쪽이든 안전하다.

### ④ 체크포인트

- Lec 5 p.7 그림의 가운데 경우(σ₂ < 0 < σ₁)와 같은 모양이다: 부호가 반대인 두 주응력이 면내에 있으면 면내 최대 전단 = 절대 최대 전단.
- 반대로 두 면내 주응력이 **같은 부호**면(Lec 5 p.7 왼쪽·오른쪽 그림) 절대 최대 전단이 면외 원에서 나와 면내 값보다 크다. 2.3(c)가 바로 이 상황이다.

---

## Problem 2.7 — 3D 주응력과 방향코사인

### ① 핵심 개념 [Lec 4 p.6, Lec 5 p.3–4, p.9–10]

- **주응력 = 응력행렬의 고유값, 주방향 = 고유벡터**: $\sigma\vec x = \sigma_p\vec x$
  - 물리적 의미: 그 방향이 법선인 면에서는 힘이 면에 수직($\vec t \parallel \hat n$)이고 전단이 0.
- 0이 아닌 해가 있으려면 $\det(\sigma - \sigma_p I) = 0$ → 특성방정식 $\sigma_p^3 - I_1\sigma_p^2 + I_2\sigma_p - I_3 = 0$
- **불변량** $I_1, I_2, I_3$: 좌표를 돌려도 변하지 않는다 → 검산 도구로 쓸 수 있다 (합 = I₁, 곱 = I₃).
- 방향 구하기: $(\sigma - \sigma_1 I)\vec x = 0$ → $\vec x$는 행벡터들에 모두 수직 → **두 행의 외적** [Lec 5 p.10].

### ② 풀이

$$\sigma = \begin{bmatrix} 220 & -80 & 0 \\ -80 & 220 & 40 \\ 0 & 40 & 0 \end{bmatrix}\ \text{MPa}$$

**Step 1. 불변량**

$$I_1 = 220 + 220 + 0 = 440$$

$$I_2 = \sigma_x\sigma_y + \sigma_y\sigma_z + \sigma_z\sigma_x - \tau_{xy}^2 - \tau_{yz}^2 - \tau_{zx}^2 = 48400 + 0 + 0 - 6400 - 1600 - 0 = 40400$$

$$I_3 = \det\sigma = 220(0\cdot 0 - 40^2) - (-80)(-80\cdot 0 - 40\cdot 0) + 0 = -352000$$

**Step 2. 특성방정식**

$$\sigma_p^3 - 440\sigma_p^2 + 40400\sigma_p + 352000 = 0$$

**Step 3. 삼각함수 해법** [Lec 5 p.4]

$$\sqrt{I_1^2 - 3I_2} = \sqrt{193600 - 121200} = \sqrt{72400} = 269.07$$

$$\cos 3\phi = \frac{2I_1^3 - 9I_1I_2 + 27I_3}{2(I_1^2 - 3I_2)^{3/2}} = \frac{170{,}368{,}000 - 159{,}984{,}000 - 9{,}504{,}000}{2(19{,}480{,}870)} = \frac{880{,}000}{38{,}961{,}740} = 0.02259$$

$$\phi = \tfrac13\arccos(0.02259) = 0.5161\ \text{rad}$$

$$\sigma = \frac{440}{3} + \frac23(269.07)\cos\left(\phi + \frac{2\pi k}{3}\right) = 146.67 + 179.38\cos(\cdots)$$

- k = 0: $146.67 + 179.38\cos(0.5161) = 302.7$
- k = 1: $146.67 + 179.38\cos(2.6105) = -8.003$
- k = 2: $146.67 + 179.38\cos(4.7049) = 145.3$

> ⚠ 공식의 k 순서는 크기 순서가 아니다 → **반드시 재정렬** (Lec 5 p.10 "Rearrange").

**Step 4. 검산 (불변량 활용)**

- 합: 302.7 + 145.3 − 8.003 = 440.0 = I₁ ✓
- 곱: 302.7 × 145.3 × (−8.003) ≈ −352000 = I₃ ✓

**Step 5. σ₁의 방향코사인**

$$\sigma - \sigma_1 I = \begin{bmatrix} -82.69 & -80 & 0 \\ -80 & -82.69 & 40 \\ 0 & 40 & -302.69 \end{bmatrix}$$

$$\vec x_1 \sim \vec r_1 \times \vec r_2 = \begin{vmatrix} \hat e_1 & \hat e_2 & \hat e_3 \\ -82.69 & -80 & 0 \\ -80 & -82.69 & 40 \end{vmatrix} = \begin{bmatrix} -80(40) - 0 \\ 0 - (-82.69)(40) \\ (-82.69)^2 - 6400 \end{bmatrix} = \begin{bmatrix} -3200 \\ 3307.5 \\ 437.1 \end{bmatrix}$$

정규화: $|\vec x_1| = 4622.7$, 부호를 뒤집어 첫 성분을 양수로 (같은 면):

$$\hat n_1 = (0.6922,\ -0.7155,\ -0.0946)$$

**Step 6. 검산 (Cauchy 공식)**

$\sigma\hat n_1 = (209.5,\ -216.6,\ -28.62) = 302.7 \times \hat n_1$ ✓ → 이 면에는 전단응력이 없다 = 주평면 ✓

### ③ 최종 답

$$\boxed{\sigma_1 = 302.7\ \text{MPa},\quad \sigma_2 = 145.3\ \text{MPa},\quad \sigma_3 = -8.003\ \text{MPa}}$$

$$\boxed{\hat n_1 = (l, m, n) = (0.6922,\ -0.7155,\ -0.0946)}\quad (\text{방향각 } 46.2^\circ,\ 135.7^\circ,\ 95.4^\circ)$$

Claude, Codex, 수치 검산 모두 일치.

### ④ 체크포인트

- 외적에 쓴 두 행이 평행하면 영벡터가 나온다 → 다른 두 행을 골라라.
- $-\hat n_1$도 같은 면이다 (법선 부호만 반대).
- 참고: $\hat n_2 = (0.7184, 0.6707, 0.1846)$, $\hat n_3 = (-0.0687, -0.1957, 0.9783)$. 세 벡터는 서로 직교한다 (대칭행렬의 고유벡터).

---

## Problem 2.8 — 변형에너지 밀도를 불변량으로

### ① 핵심 개념 [Lec 7 p.3–6]

- **변형에너지 밀도** $U_0 = \frac12\sum\sigma_{ij}e_{ij}$: 선형탄성에서 힘-변위 그래프 아래 삼각형 넓이의 단위체적 버전. 여기서 u는 변위가 아니라 에너지다.
- **Hooke 법칙** [Lec 3 p.2]: $e_1 = \frac1E[\sigma_1 - \nu(\sigma_2 + \sigma_3)]$
- **왜 불변량으로?** 에너지는 스칼라라서 좌표에 무관해야 한다 → 좌표에 무관한 양(불변량)으로 표현될 수밖에 없다.
- 주좌표에서 $I_1 = \sum\sigma_i$, $I_2 = \sum_{i<j}\sigma_i\sigma_j$, 그리고 항등식 $\sum\sigma_i^2 = I_1^2 - 2I_2$.
- $G = \dfrac{E}{2(1+\nu)}$ [Lec 3 p.2]

### ② 풀이

**Step 1. Hooke 법칙 대입** (Lec 7 p.4와 같은 과정)

$$u = \frac12\sum_i\sigma_ie_i = \frac{1}{2E}\left[\sigma_1^2 + \sigma_2^2 + \sigma_3^2 - 2\nu(\sigma_1\sigma_2 + \sigma_2\sigma_3 + \sigma_3\sigma_1)\right]$$

**Step 2. 불변량으로 치환**

$$= \frac{1}{2E}\left[(I_1^2 - 2I_2) - 2\nu I_2\right] = \frac{1}{2E}\left[I_1^2 - 2(1+\nu)I_2\right]$$

**Step 3. G로 정리**

$$\frac{2(1+\nu)}{2E} = \frac{1+\nu}{E} = \frac{1}{2G}\ \Rightarrow\ u = \frac{I_1^2}{2E} - \frac{I_2}{2G}$$

**(b)** I₁ = 0을 대입하면 바로 $u = -I_2/(2G)$.

### ③ 최종 답

$$\boxed{\text{(a) } u = \frac{1}{2E}\left[I_1^2 - 2(1+\nu)I_2\right] = \frac{I_1^2}{2E} - \frac{I_2}{2G}}\qquad \boxed{\text{(b) } I_1 = 0 \Rightarrow u = -\frac{I_2}{2G}}$$

(Claude의 첫째 형태와 Codex의 둘째 형태는 같은 식)

### ④ 체크포인트 — 이 문제가 Lec 7과 연결되는 지점

- **I₁ = 0 ⟺ 정수압 성분 σ̄ = I₁/3 = 0** [Lec 7 p.5] → 부피 변화 에너지가 0이고 **전부 형상 변화(distortion) 에너지**.
- 실제로 Lec 7 p.6의 편차 에너지 $\hat U_0 = \frac{1}{6G}(I_1^2 - 3I_2)$에 I₁ = 0을 넣으면 $-I_2/(2G)$로 정확히 일치한다.
- von Mises 항복조건이 바로 이 편차 에너지가 임계값에 도달하는 조건이다.
- I₁ = 0이면 $I_2 = -\frac12\sum\sigma_i^2 \le 0$ → u ≥ 0 (에너지는 음수가 될 수 없으니 합리적, Codex 지적).

---

## Problem 2.9 — $I_2 \le \frac13 I_1^2$ 증명

### ① 핵심 개념

- **불변량은 좌표에 무관** → 가장 편한 좌표(주좌표)에서 계산해도 된다.
- 부등식 증명의 정석: **차이를 제곱합(음이 아닌 양)으로 표현**하기.
- 물리적 의미: 이 차이는 **편차응력의 크기**와 같다 [Lec 7 p.5: $\sum\hat\sigma_i^2 = \frac23(I_1^2 - 3I_2)$].

### ② 풀이

**Step 1. 주좌표에서 I₁²을 전개**

$$I_1^2 = (\sigma_1 + \sigma_2 + \sigma_3)^2 = \sigma_1^2 + \sigma_2^2 + \sigma_3^2 + 2I_2$$

**Step 2. 차이를 계산**

$$I_2 - \frac{I_1^2}{3} = \frac{3I_2 - \sum\sigma_i^2 - 2I_2}{3} = -\frac13\left[\sigma_1^2 + \sigma_2^2 + \sigma_3^2 - \sigma_1\sigma_2 - \sigma_2\sigma_3 - \sigma_3\sigma_1\right]$$

**Step 3. 완전제곱으로**

$a^2 + b^2 + c^2 - ab - bc - ca = \frac12[(a-b)^2 + (b-c)^2 + (c-a)^2]$ 이므로

$$I_2 - \frac{I_1^2}{3} = -\frac16\left[(\sigma_1 - \sigma_2)^2 + (\sigma_2 - \sigma_3)^2 + (\sigma_3 - \sigma_1)^2\right] \le 0$$

**Step 4. 등호 조건**: 세 제곱이 모두 0 ⟺ σ₁ = σ₂ = σ₃ (정수압/구형 응력 상태)

(Codex 버전: 주좌표를 쓰지 않고 일반 좌표에서 바로 $-\frac16[(\sigma_x-\sigma_y)^2 + \cdots] - (\tau_{xy}^2 + \tau_{yz}^2 + \tau_{zx}^2)$로 정리할 수도 있다. 이 방법은 불변성을 따로 언급할 필요가 없다.)

### ③ 최종 답

$$\boxed{I_2 - \frac{I_1^2}{3} = -\frac16\sum_{i<j}(\sigma_i - \sigma_j)^2 \le 0\ \Rightarrow\ I_2 \le \frac13 I_1^2}$$

등호는 σ₁ = σ₂ = σ₃일 때만 성립한다. 따라서 정수압 상태가 아니면 문제의 엄격한 부등식 $I_2 < \frac13 I_1^2$이 성립한다.

### ④ 체크포인트 — 개념 연결

- 괄호 안 $\sum(\sigma_i - \sigma_j)^2$는 **von Mises 등가응력**의 제곱에 들어있는 바로 그 양이다: $\sigma_E^{VM} = \sqrt{\frac12\sum(\sigma_i - \sigma_j)^2}$ [Lec 7 p.8].
- 그래서 $I_1^2 - 3I_2 = (\sigma_E^{VM})^2 \ge 0$이다. Lec 5 p.4 삼각함수 해의 $\sqrt{I_1^2 - 3I_2}$가 항상 실수인 이유이기도 하다.
- 등호(정수압) = 전단이 없음 = 항복하지 않음 [Lec 6 p.8]. 수학과 물리가 같은 이야기를 한다.

---

## 요약표

| 문제 | 최종 답 | 핵심 개념 |
|---|---|---|
| 2.1 | ε_x = ∂u/∂x …, γ_xy = ∂v/∂x + ∂u/∂y … | 변형률 정의 + 미소변형 |
| 2.2 | ε_r = du/dr, ε_θ = u/r, γ_rθ = 0 | 극좌표에서 반경 이동 → 원주 변형률 |
| 2.3 | σ_θ = pr/t, σ_z = F/2πrt; (b) F = −2πr²p; (c) F ≥ 0 | FBD + 3D Mohr 원 (σ_r = 0 포함) |
| 2.4 | σ_θ = σ_φ = pr/2t, σ_r ≈ 0 | 대칭 → 주방향, 반구 FBD |
| 2.5 | σ_x sinα + τ_xy cosα = 0, τ_xy sinα + σ_y cosα = 0 | Cauchy 공식, 자유 경계 t = 0 |
| 2.6 | 40 MPa (원 반지름 40/25/15) | 3D Mohr 원 |
| 2.7 | 302.7, 145.3, −8.003 MPa; n̂₁ = (0.6922, −0.7155, −0.0946) | 고유값 문제, 불변량, 외적 |
| 2.8 | u = [I₁² − 2(1+ν)I₂]/2E; I₁ = 0 → −I₂/2G | 변형에너지, 편차 에너지 |
| 2.9 | I₂ − I₁²/3 = −(1/6)Σ(σᵢ−σⱼ)² ≤ 0 | 제곱합 증명, von Mises와 연결 |

**Claude vs Codex 비교 결과**: 전 문항 답이 일치한다. 2.6은 "면내" 해석에 따라 40 MPa(표준) 또는 25 MPa(σ₁–σ₂ 평면)가 나오므로, 세 반지름을 모두 적는 것을 권장한다.
