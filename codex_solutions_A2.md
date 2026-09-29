# 응용고체역학 과제 2 — 독립 풀이

인장응력을 양(+)으로 하고, 공학적 전단변형률을 사용한다. 수치 답은 유효숫자 4자리로 표시한다. 정확한 정수 계수와 영(0)은 그대로 쓴다. 얇은 벽의 응력은 끝단의 국부효과를 제외한 막응력 근사이다.

## 2.1 미소변형률과 변위의 관계

변위장을 \(\boldsymbol u=(u,v,w)\)라 하자. 처음에 \(x\) 방향으로 떨어진 두 점의 상대 위치는 \((dx,0,0)\)이다. 변형 후 상대 위치는 Taylor 전개에 의해

\[
\bigl((1+u_{,x})dx,\;v_{,x}dx,\;w_{,x}dx\bigr)
\]

가 된다. 따라서 변형 후 길이는

\[
d\ell_x=dx\sqrt{(1+u_{,x})^2+v_{,x}^2+w_{,x}^2}
\simeq(1+u_{,x})dx.
\]

여기서 변위 기울기의 이차 이상 항을 무시하였다. 원래 길이에 대한 길이 변화율을 취하고 \(y,z\) 방향에도 같은 논리를 적용하면

\[
\boxed{\varepsilon_x=\frac{\partial u}{\partial x},\qquad
\varepsilon_y=\frac{\partial v}{\partial y},\qquad
\varepsilon_z=\frac{\partial w}{\partial z}.}
\]

처음에 서로 수직인 \(x,y\) 방향 선분의 변형 후 단위 접선은 일차 정확도로

\[
\boldsymbol a_x\simeq(1,v_{,x},w_{,x}),\qquad
\boldsymbol a_y\simeq(u_{,y},1,w_{,y})
\]

이다. 두 선분 사이 각도를 \(\pi/2-\gamma_{xy}\)라 하면

\[
\cos(\pi/2-\gamma_{xy})\simeq\gamma_{xy}
=\boldsymbol a_x\cdot\boldsymbol a_y
\simeq u_{,y}+v_{,x}.
\]

다른 두 좌표면에서도 동일하게

\[
\boxed{\gamma_{xy}=\frac{\partial v}{\partial x}+\frac{\partial u}{\partial y},\qquad
\gamma_{yz}=\frac{\partial w}{\partial y}+\frac{\partial v}{\partial z},\qquad
\gamma_{zx}=\frac{\partial u}{\partial z}+\frac{\partial w}{\partial x}.}
\]

공학적 전단변형률과 변형률 텐서의 관계는 \(\gamma_{ij}=2\varepsilon_{ij}\;(i\ne j)\)이다. 이 유도는 변위 기울기가 작은 미소변형을 전제로 한다.

## 2.2 축대칭 반경 변위의 평면변형률

변위는 \(\boldsymbol u=u(r)\boldsymbol e_r\)이며 원주 방향 변위는 없다. 원래 변의 길이가 \(dr\), \(r\,d\theta\)인 미소 부채꼴 요소를 생각한다.

반경 방향 변의 변형 후 길이는

\[
[r+dr+u(r+dr)]-[r+u(r)]
\simeq\left(1+\frac{du}{dr}\right)dr.
\]

따라서

\[
\boxed{\varepsilon_r=\frac{du}{dr}.}
\]

원주 방향 변은 각도 \(d\theta\)를 유지하면서 반경만 \(r+u\)로 바뀌므로

\[
\varepsilon_\theta
=\frac{(r+u)d\theta-rd\theta}{rd\theta},\qquad
\boxed{\varepsilon_\theta=\frac{u}{r}.}
\]

축대칭 변형으로 반경선은 반경선으로, 원호는 동심 원호로 바뀐다. 두 방향은 계속 수직이므로 직각의 변화가 없다.

\[
\boxed{\gamma_{r\theta}=0.}
\]

평면변형률 조건에 따라 \(\varepsilon_z=\gamma_{rz}=\gamma_{\theta z}=0\)이다. 평면변형률이라고 해서 \(\sigma_z=0\)인 것은 아니다.

## 2.3 내압과 축력을 받는 얇은 원통

### (a) 응력 성분과 축력의 정의

\(p>0\), \(r>0\), \(t>0\), \(t/r\ll1\)로 둔다. 문제에서 지정한
\(\sigma_z=F/(2\pi rt)\)에 맞추어 **\(F\)는 원통 벽이 전달하는 총 축력**으로 해석한다. 따라서 끝마개에 작용하는 압력 합력 \(p\pi r^2\)를 \(F\)에 다시 더하지 않는다. 만약 별도의 외력 \(F_{\rm ext}\)를 받는 닫힌 원통을 다룬다면 \(F=F_{\rm ext}+p\pi r^2\)로 먼저 환산해야 한다.

길이 \(L\)인 원통을 축을 포함하는 평면으로 절단한다. 반원통에 작용하는 압력 합력은 투영면적을 이용하면 \(p(2rL)\)이다. 두 절단면의 원주응력 합력과 평형을 이루므로

\[
2\sigma_\theta tL=2prL
\quad\Longrightarrow\quad
\boxed{\sigma_\theta=\frac{pr}{t}.}
\]

축에 수직인 벽의 단면적은

\[
\pi[(r+t)^2-r^2]=2\pi rt+\pi t^2\simeq2\pi rt.
\]

따라서 축방향 평형으로부터

\[
\boxed{\sigma_z=\frac{F}{2\pi rt}.}
\]

반경응력은 안쪽 표면에서 \(-p\), 바깥 표면에서 0이다. 즉 실제로 벽 전체에서 정확히 0은 아니지만, 원주응력에 대한 상대 크기가 \(p/(pr/t)=t/r\ll1\)이므로 막응력 근사에서는 무시한다.

\[
\boxed{\sigma_r\simeq0,\qquad\tau_{r\theta}=\tau_{\theta z}=\tau_{zr}=0.}
\]

### (b), (c) 모든 축력 부호에 대한 비교

다음과 같이 놓으면 세 주응력의 집합은 \(\{0,A,B\}\)이다.

\[
A=\frac{pr}{t}>0,\qquad B=\frac{F}{2\pi rt}.
\]

문제의 ‘최대 수직응력의 크기’는 모든 면에서의 수직응력 절댓값의 최댓값으로 정의한다. 주축계에서 \(\sigma_n=\sum_i\sigma_i n_i^2\)이고 \(\sum_i n_i^2=1\)이므로

\[
N=\max|\sigma_n|=\max_i|\sigma_i|=\max(A,|B|),
\qquad T=|\tau_{\max}|=\frac{\max(0,A,B)-\min(0,A,B)}2.
\]

반경 주응력 0을 포함한 경우 분류는 다음과 같다.

| 축응력 범위 | 최대 주응력 | 최소 주응력 | \(N\) | \(T\) |
|---|---:|---:|---:|---:|
| \(B\ge A\) | \(B\) | 0 | \(B\) | \(B/2\) |
| \(0\le B\le A\) | \(A\) | 0 | \(A\) | \(A/2\) |
| \(-A\le B<0\) | \(A\) | \(B\) | \(A\) | \((A-B)/2\) |
| \(B<-A\) | \(A\) | \(B\) | \(-B\) | \((A-B)/2\) |

**(b) \(T=N\).** \(B\ge0\)이면 \(T=N/2\)이고 \(N>0\)이므로 해가 없다. \(-A\le B<0\)에서는

\[
\frac{A-B}{2}=A\quad\Longrightarrow\quad B=-A.
\]

\(B<-A\)에서는 \((A-B)/2=-B\)로부터 역시 \(B=-A\)가 나오지만 이는 해당 열린 구간 밖의 경계이다. 따라서 유일한 해는

\[
\boxed{B=-A\quad\Longleftrightarrow\quad F=-2\pi pr^2.}
\]

즉 원주 인장응력과 같은 크기의 축방향 압축응력이 필요하다. **축력이 인장으로만 제한되면 (b)는 해가 없다.**

**(c) \(T=N/2\).** \(B\ge0\)에서는 표의 처음 두 행에서 항상 성립한다. \(-A\le B<0\)에서는 \(A-B=A\)로부터 \(B=0\)이 요구되어 엄밀한 압축 범위에는 해가 없다. \(B<-A\)에서는 \(A-B=-B\)가 \(A=0\)을 요구하여 \(p>0\)과 모순된다.

\[
\boxed{p>0:\quad F\ge0\text{인 모든 축력에서 성립한다.}}
\]

따라서 (c)는 \(F\)와 \(p\) 사이의 특정 비례식을 요구하지 않는다. \(F>0\)의 인장력 및 \(F=0\) 모두 가능하며 압축력은 불가능하다.

**영압력 예외:** \(p=0\)이면 주응력은 \(\{0,0,B\}\)이고 \(T=|B|/2\), \(N=|B|\)이다. 따라서 (b)는 \(F=0\)에서만, (c)는 모든 실수 \(F\)에서 성립한다. 영응력 상태에서는 두 등식 모두 \(0=0\)이다. 위 결론은 \(\sigma_r=0\)인 막응력 근사에 대한 결과이다.

## 2.4 내압을 받는 얇은 구

### (a) 주방향

구의 중심에서 해당 점으로 향하는 반경 방향을 \(\boldsymbol e_r\)라 하자. 균일 내압과 구의 형상은 이 반경축 주위의 임의 회전에 대해 불변이다. 따라서 반경과 접평면을 연결하는 전단응력은 없어야 하고, 접평면의 두 방향을 구별하는 응력도 존재할 수 없다. 즉

\[
\boldsymbol\sigma
=\sigma_r\boldsymbol e_r\otimes\boldsymbol e_r
+\sigma_t\bigl(\boldsymbol e_\theta\otimes\boldsymbol e_\theta
+\boldsymbol e_\phi\otimes\boldsymbol e_\phi\bigr).
\]

따라서

\[
\boxed{r,\theta,\phi\text{는 주방향이며},\quad
\sigma_\theta=\sigma_\phi,\quad
\tau_{r\theta}=\tau_{\theta\phi}=\tau_{\phi r}=0.}
\]

접선 주응력은 중복되므로 접평면 안의 임의의 서로 수직인 두 방향도 주방향이다.

### (b) 반구의 평형

구를 두 반구로 자르면 한 반구의 압력 합력은 투영된 원판의 면적에 압력을 곱한 \(p\pi r^2\)이다. 절단면의 얇은 고리 면적은 \(2\pi rt\)이고, 이곳의 접선 막응력 \(\sigma_t\)가 압력 합력을 지지한다.

\[
\sigma_t(2\pi rt)=p\pi r^2
\quad\Longrightarrow\quad
\boxed{\sigma_\theta=\sigma_\phi=\frac{pr}{2t}.}
\]

반경응력은 내면의 \(-p\)에서 외면의 0으로 변하지만, 접선응력에 비해 \(O(t/r)\) 크기이므로

\[
\boxed{\sigma_r\simeq0.}
\]

## 2.5 자유 경계 AB의 응력 조건

문제의 기하에 따라 바깥쪽 단위 법선과 경계의 단위 접선을

\[
\boldsymbol n=(\sin\alpha,\cos\alpha),\qquad
\boldsymbol m=(\cos\alpha,-\sin\alpha)
\]

로 잡는다. 평면응력 텐서에 Cauchy 공식을 적용하면

\[
\boldsymbol t=\boldsymbol\sigma\boldsymbol n
=\begin{pmatrix}\sigma_x&\tau_{xy}\\\tau_{xy}&\sigma_y\end{pmatrix}
\begin{pmatrix}\sin\alpha\\\cos\alpha\end{pmatrix}.
\]

자유 경계에는 표면력이 없으므로

\[
\boxed{\sigma_x\sin\alpha+\tau_{xy}\cos\alpha=0,\qquad
\tau_{xy}\sin\alpha+\sigma_y\cos\alpha=0.}
\]

법선 및 접선 성분으로 쓰면 동등하게

\[
\boxed{\sigma_{nn}=\sigma_x\sin^2\alpha+\sigma_y\cos^2\alpha
+2\tau_{xy}\sin\alpha\cos\alpha=0,}
\]

\[
\boxed{\tau_{mn}=(\sigma_x-\sigma_y)\sin\alpha\cos\alpha
+\tau_{xy}(\cos^2\alpha-\sin^2\alpha)=0.}
\]

각도를 나누는 식을 쓰지 않았으므로 \(\alpha=0\) 및 \(\pi/2\)에도 적용된다. 경계에서 가능한 응력은 \(\boldsymbol\sigma=\sigma_{mm}\boldsymbol m\otimes\boldsymbol m\)이며, 자유 경계라고 해서 경계에 평행한 \(\sigma_{mm}\)까지 0일 필요는 없다.

## 2.6 3차원 Mohr 원과 최대 전단응력

주응력은 \(\sigma_1=50.00\), \(\sigma_2=0\), \(\sigma_3=-30.00\;\mathrm{MPa}\)이다. 각 주응력 쌍에 대응하는 원의 중심과 반지름은

\[
C_{ij}=\frac{\sigma_i+\sigma_j}{2},\qquad
R_{ij}=\frac{|\sigma_i-\sigma_j|}{2}.
\]

| 원 | 중심 \(C_{ij}\) (MPa) | 반지름 \(R_{ij}\) (MPa) | 수평축과의 교점 (MPa) |
|---|---:|---:|---|
| 1–2 | 25.00 | 25.00 | 0, 50.00 |
| 2–3 | −15.00 | 15.00 | −30.00, 0 |
| 1–3 | 10.00 | 40.00 | −30.00, 50.00 |

세 원을 그리는 정확한 식은 다음과 같다. 좌표 단위는 MPa이다.

\[
(\sigma-25.00)^2+\tau^2=(25.00)^2,
\qquad(\sigma+15.00)^2+\tau^2=(15.00)^2,
\]
\[
(\sigma-10.00)^2+\tau^2=(40.00)^2.
\]

스케치에서는 수평축에 \(-30.00,0,50.00\)을 표시한다. \(-30.00\)에서 \(50.00\)까지를 지름으로 하는 바깥 원을 그리고, 그 안에 \([-30.00,0]\)과 \([0,50.00]\)을 각각 지름으로 하는 두 작은 원을 그린다. 아래는 수평축상의 배치를 나타낸 도식이다.

```text
          2–3 원의 지름            1–2 원의 지름
       |----------------|--------------------------|
σ  →  -30               0                         50
       |------------------------------------------|
                    1–3 원의 지름
```

‘면내 최대 전단응력’은 어느 주방향 평면을 말하는지 지정해야 한다. 여기서는 면의 법선이 해당 두 주방향이 만드는 평면 안에서 회전하는 경우를 뜻한다.

\[
\boxed{|\tau_{\max}^{(1-2)}|=25.00\;\mathrm{MPa},\qquad
|\tau_{\max}^{(1-3)}|=40.00\;\mathrm{MPa}.}
\]

참고로 \(|\tau_{\max}^{(2-3)}|=15.00\;\mathrm{MPa}\)이다. 모든 3차원 방향을 허용한 절대 최대값은 가장 큰 원의 반지름이다.

\[
\boxed{|\tau_{\max}|=\frac{50.00-(-30.00)}{2}=40.00\;\mathrm{MPa}.}
\]

이는 면의 법선이 \(\boldsymbol e_1\)과 \(\boldsymbol e_3\)에 각각 \(45.00^\circ\)를 이루는 면에서 발생한다. 예를 들어 \(\boldsymbol n=(\boldsymbol e_1+\boldsymbol e_3)/\sqrt2\)이며, 그 면의 수직응력은 \(10.00\;\mathrm{MPa}\)이다.

## 2.7 주응력과 최대 인장응력 면의 방향코사인

주어진 응력 텐서는

\[
\boldsymbol\sigma=\begin{pmatrix}
220&-80&0\\-80&220&40\\0&40&0
\end{pmatrix}\;\mathrm{MPa}.
\]

### (a) 불변량과 삼각함수 해법

\[
I_1=220+220+0=440\;\mathrm{MPa},
\]
\[
I_2=220(220)+220(0)+0(220)-(-80)^2-40^2-0^2
=40400\;\mathrm{MPa}^2,
\]
\[
I_3=\det\boldsymbol\sigma=220(0-40^2)=-352000\;\mathrm{MPa}^3.
\]

따라서 특성방정식은

\[
\boxed{s^3-440s^2+40400s+352000=0}
\]

이다. 여기서 \(s\)의 수치는 MPa 단위이다. 주어진 공식에서

\[
D=I_1^2-3I_2=72400\;\mathrm{MPa}^2,
\]
\[
\phi=\frac13\arccos\left[
\frac{2I_1^3-9I_1I_2+27I_3}{2D^{3/2}}\right]
=0.5161\;\mathrm{rad}.
\]

반올림 전 \(\phi\)를 사용하여

\[
s_k=\frac{I_1}{3}+\frac23\sqrt D
\cos\left(\phi+\frac{2\pi(k-1)}3\right),\qquad k=1,2,3
\]

를 계산한다. 이 공식의 \(k\) 순서가 크기 순서는 아니므로 내림차순으로 재배열하면

\[
\boxed{\sigma_1=302.7\;\mathrm{MPa},\qquad
\sigma_2=145.3\;\mathrm{MPa},\qquad
\sigma_3=-8.003\;\mathrm{MPa}.}
\]

### (b) 최대 인장응력 면의 법선

최대 인장응력이 작용하는 면의 법선은 \(\sigma_1\)의 고유벡터이다. 방향코사인 \((l,m,n)\)은 면 자체의 접선이 아니라 이 법선의 성분이다.

\[
(\boldsymbol\sigma-\sigma_1\boldsymbol I)\boldsymbol n_1=0.
\]

반올림 전의 \(\sigma_1\)을 사용하고 \(a=220-\sigma_1\)라 하면 첫 두 행은

\[
\boldsymbol r_1=(a,-80,0),\qquad
\boldsymbol r_2=(-80,a,40).
\]

따라서 두 행에 수직인 벡터는

\[
\boldsymbol c=\boldsymbol r_1\times\boldsymbol r_2
=(-3200,-40a,a^2-6400).
\]

이를 정규화하고 첫 성분이 양수가 되도록 전체 부호를 선택하면

\[
\boxed{\boldsymbol n_1=(l,m,n)
=(0.6922,-0.7155,-0.09455).}
\]

반대 부호 \(-\boldsymbol n_1\)도 같은 면을 나타낸다. 좌표축과의 방향각은

\[
\boxed{\alpha_x=46.19^\circ,\qquad
\alpha_y=135.7^\circ,\qquad
\alpha_z=95.43^\circ.}
\]

Cauchy 공식으로 계산한 표면력은

\[
\boldsymbol t=\boldsymbol\sigma\boldsymbol n_1
=(209.5,-216.6,-28.62)\;\mathrm{MPa}
=\sigma_1\boldsymbol n_1.
\]

따라서 이 면에는 전단응력이 없으며 수직응력이 최대 인장 주응력이다.

### Python 수치 검산

실행 환경에 NumPy가 설치되어 있지 않아, 추가 파일을 생성하지 않는 Python 표준 라이브러리 검산을 실행하였다. 세 근의 특성방정식 잔차와 정규화한 벡터의 고유방정식을 직접 확인하였다. 반올림 전 값으로 얻은 결과는

\[
\|\boldsymbol\sigma\boldsymbol n_1-\sigma_1\boldsymbol n_1\|_2
=6.355\times10^{-14}\;\mathrm{MPa}
\]

이며, 아래 검산의 모든 `assert`가 통과하였다. 같은 실행에서 2.3의 부호별 조건과 2.6의 원 반지름도 확인하였다.

```python
from math import acos, cos, pi, sqrt, isclose

S = [[220, -80, 0], [-80, 220, 40], [0, 40, 0]]
I1, I2, I3 = 440.0, 40400.0, -352000.0
D = I1**2 - 3*I2
phi = acos((2*I1**3 - 9*I1*I2 + 27*I3)/(2*D**1.5))/3
s = sorted([I1/3 + 2*sqrt(D)/3*cos(phi + 2*pi*k/3)
            for k in range(3)], reverse=True)
a = 220 - s[0]
c = [-3200, -40*a, a*a - 6400]
c_norm = sqrt(sum(x*x for x in c))
n = [-x/c_norm for x in c]
traction = [sum(row[j]*n[j] for j in range(3)) for row in S]
for x in s:
    assert abs(x**3 - I1*x*x + I2*x - I3) < 1e-7
assert abs(sum(x*x for x in n) - 1) < 1e-12
assert max(abs(traction[i] - s[0]*n[i]) for i in range(3)) < 1e-10

# 2.3: A=1로 정규화, B/A를 -10에서 10까지 0.001 간격으로 검사
for j in range(-10000, 10001):
    b = j/1000
    stresses = [0, 1, b]
    N = max(map(abs, stresses))
    T = (max(stresses) - min(stresses))/2
    assert isclose(T, N, abs_tol=1e-12) == (j == -1000)
    assert isclose(T, N/2, abs_tol=1e-12) == (j >= 0)

# 2.6
circles = [((x+y)/2, abs(x-y)/2)
           for x, y in [(50, 0), (0, -30), (50, -30)]]
assert circles == [(25, 25), (-15, 15), (10, 40)]
```

수치 표본 검사는 2.3의 해석적 경우 분류를 보조하는 검산이며, 모든 실수 축력에 대한 증명은 앞의 대수적 유도에 따른다.

## 2.8 응력 불변량으로 표현한 탄성 변형에너지 밀도

이 문제의 \(u\)는 변위가 아니라 단위 체적당 탄성 변형에너지이다. 등방성 선형탄성체의 주축계에서

\[
\varepsilon_i=\frac1E[\sigma_i-\nu(\sigma_j+\sigma_k)]
\]

이며 \(i,j,k\)는 서로 다르다.

### (a) 불변량 표현

이를 \(u=\tfrac12\sum_i\sigma_i\varepsilon_i\)에 대입하면

\[
u=\frac1{2E}\left[\sigma_1^2+\sigma_2^2+\sigma_3^2
-2\nu(\sigma_1\sigma_2+\sigma_2\sigma_3+\sigma_3\sigma_1)\right].
\]

주응력으로 표현한 불변량은

\[
I_1=\sigma_1+\sigma_2+\sigma_3,\qquad
I_2=\sigma_1\sigma_2+\sigma_2\sigma_3+\sigma_3\sigma_1.
\]

따라서 \(\sum_i\sigma_i^2=I_1^2-2I_2\)이므로

\[
\boxed{u=\frac{I_1^2-2(1+\nu)I_2}{2E}
=\frac{I_1^2}{2E}-\frac{I_2}{2G},\qquad
G=\frac{E}{2(1+\nu)}.}
\]

에너지 밀도의 SI 단위는 \(\mathrm{J/m^3}=\mathrm{Pa}\)이다.

### (b) \(I_1=0\)인 경우

위 식에 직접 대입하면

\[
\boxed{I_1=0\quad\Longrightarrow\quad u=-\frac{I_2}{2G}.}
\]

이때 \(I_2=-\tfrac12\sum_i\sigma_i^2\le0\)이므로 \(G>0\)일 때 \(u\ge0\)이다.

## 2.9 모든 응력 상태에서의 불변량 부등식

일반적인 대칭 응력 텐서에 대해

\[
I_2-\frac{I_1^2}{3}
=\sigma_x\sigma_y+\sigma_y\sigma_z+\sigma_z\sigma_x
-(\tau_{xy}^2+\tau_{yz}^2+\tau_{zx}^2)
-\frac{(\sigma_x+\sigma_y+\sigma_z)^2}{3}.
\]

정리하면

\[
I_2-\frac{I_1^2}{3}
=-\frac16\left[(\sigma_x-\sigma_y)^2
+(\sigma_y-\sigma_z)^2+(\sigma_z-\sigma_x)^2\right]
-(\tau_{xy}^2+\tau_{yz}^2+\tau_{zx}^2).
\]

우변은 음의 제곱합이므로

\[
\boxed{I_2\le\frac{I_1^2}{3}.}
\]

등호는 모든 제곱항이 동시에 0일 때만 성립한다. 즉

\[
\boxed{I_2=\frac{I_1^2}{3}
\iff\sigma_x=\sigma_y=\sigma_z=q,\quad
\tau_{xy}=\tau_{yz}=\tau_{zx}=0
\iff\boldsymbol\sigma=q\boldsymbol I.}
\]

이는 영응력을 포함하는 구형 응력 상태이며, \(q<0\)은 정수압 압축, \(q>0\)은 등방 인장이다. 동등하게 세 주응력이 모두 같을 때 등호가 성립한다.
