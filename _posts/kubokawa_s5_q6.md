\現代数理統計学の基礎
問題文
======

問 6 マルコフの不等式と同様にして次の不等式を示せ。

\(1) $Z \sim \mathcal{N} (0, 1)$ としその確率密度関数を $\phi (z)$
とするとき，$P (|Z| \geq t) \leq (2/t) \phi (t)$ が成り立つ。

\(2) 任意の確率変数 $X$ と $t > 0$ について,
$P(X \geq a) \leq e^{−at} M_X(t)$ が成り立つ。

準備
====

マルコフの不等式
----------------

$Y$を非負の確率変数で$E[Y]<\infty$とする。このとき、任意の$c>0$に対して次の不等式が成り立つ。
$$P(Y \geq c) \leq \frac{E[Y]}{c}$$

　

$I_{[Y \geq c]}$を定義関数、すなわち、 
$$I_{[Y \geq c]} = \left\{
    \begin{array}{ll}
    1 & (Y \geq c)\\
    0 & (else)
    \end{array}
    \right.$$

とする。このとき、 

よって、 
$$P(Y\geq c) \leq \frac{E[Y]}{c}$$

$\Box$

また、(\*)式での結果を用いて、次のようにも言える。問題で使う。
$$P(Y\geq c) \leq \frac{E[Y I_{[Y \geq c]}]}{c} \leq \frac{E[Y]}{c}$$ 

回答
====

\(1) $Z \sim \mathcal{N}(0, 1)$より、$|Z|$の確率密度関数は、

$$\begin{aligned}
      f_{|Z|}(z) 
      &= \frac{d}{dz} F_{|Z|}(z)\\
      &= \frac{d}{dz} P(|Z| \leq z )\\
      &= \frac{d}{dz} P(-z \leq Z \leq z )\\
      &= \frac{d}{dz} \left\{ P(Z \leq z ) - P(Z \leq -z ) \right\}\\
      &= \frac{d}{dz} \left\{ P(Z \leq z ) - P(Z \geq z ) \right\}\\
      &= \frac{d}{dz} \left\{ P(Z \leq z ) - [1 - P(Z \leq z )] \right\}\\
      &= \frac{d}{dz} \left\{ 2P(Z \leq z ) - 1  \right\}\\
      &= \frac{d}{dz} \left\{ 2F_Z(z) - 1  \right\}\\
      &= 2f_Z(z)
    \end{aligned}$$

ここで、$|Z|$は非負の確率変数で、$E[|Z|]<\infty$が成り立つ。よって、マルコフの不等式より、任意の$t>0$に対して、

$$\begin{aligned}
      P(|Z| \geq t) 
      &\leq \frac{E[|Z| I_{[|Z| \geq t]} ]}{t}\\
      &= \frac{1}{t} E[|Z| I_{[|Z| \geq t]} ]\\
      &= \frac{1}{t} \int_{t}^{\infty} |z| f_{|Z|}(|z|)dz\\
      &= \frac{1}{t} \int_{t}^{\infty} z \times 2f_{Z}(z)dz \\
      &= \frac{1}{t} \int_{t}^{\infty} z \times 2 \times \frac{1}{\sqrt{2 \pi}} e^{-z^{2} / 2} dz\\
      &= \frac{2}{t} \frac{1}{\sqrt{2 \pi}} \int_{t}^{\infty} z  e^{-z^{2} / 2} dz\\
      &= \frac{2}{t} \frac{1}{\sqrt{2 \pi}} \int_{t}^{\infty} -(e^{-z^{2} / 2})' dz\\
      &=\frac{2}{t} \frac{1}{\sqrt{2 \pi}} \left[-e^{-z^{2} / 2}\right]_{t}^{\infty} \\
      &=\frac{2}{t} \frac{1}{\sqrt{2 \pi}} e^{-t^{2} / 2} \\
      &=\frac{2}{t} \phi(t)
    \end{aligned}$$

ゆえに、$P (|Z| \geq t) \leq \frac{2}{t} \phi (t)$ が成り立つ。

$\\$

\(2) $M_X(t) = E\left[e^{t X}\right]$に注目すると、任意の$a>0$に対して、

$$\begin{aligned}
      M_{X}(t)
      &= E\left[e^{t X}\right] \\ 
      &= E\left[e^{t X} \{ I_{[X \geq a]} + I_{[X < a]} \} \right] \\
      &= E[e^{t X} I_{[X \geq a]}] + E[e^{t X} I_{[X < a]}]\\
      &\geq E[e^{t X} I_{[X \geq a]}] \\
      &= \int_{a}^{\infty} e^{t X} f_X(x)dx \\
      &\geq \int_{a}^{\infty} e^{t a} f_X(x)dx \\
      &= e^{t a} \int_{a}^{\infty} f_X(x)dx \\
      &= e^{a t} P(X \geq a)
    \end{aligned}$$

ゆえに、$P(X \geq a) \leq e^{−at} M_X(t)$ が成り立つ。
