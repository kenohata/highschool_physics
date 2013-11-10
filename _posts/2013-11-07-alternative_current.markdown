---
layout: post
title:  "交流回路の研究"
date:   2013-11-07 18:48:45
categories: jekyll update

---

# 交流回路の研究

## 数学的準備

以下の計算をしろ

$$ \frac{d}{d t} \sin \omega t = $$
$$ \frac{d}{d t} \cos \omega t = $$
$$ \int \sin \omega t dt = $$
$$ \int \cos \omega t dt = $$

$\sin$を微分したら$\cos$。そんな事は当たり前な諸君にとっては失礼な問いだったかもしれない。では、

$$ \cos(\theta \mp \frac{1}{2} \pi) = \pm sin \theta $$
$$ \sin(\theta \mp \frac{1}{2} \pi) = \mp \cos \theta $$

これらの式変形を用いて、$\sin$の結果は$\sin$で、$\cos$の結果は$\cos$で、答えよ。

答えは以下。

$$ \frac{d}{d t} \sin \omega t = \omega \sin(\omega t + \frac{1}{2} \pi) $$
$$ \frac{d}{d t} \cos \omega t = \omega \cos(\omega t + \frac{1}{2} \pi) $$
$$ \int \sin \omega t dt = \frac{1}{\omega} \sin(\omega t - \frac{1}{2} \pi) $$
$$ \int \cos \omega t dt = \frac{1}{\omega} \cos(\omega t - \frac{1}{2} \pi) $$

**微分は位相を進め、積分は位相を遅らせる**と覚えて置こう。

## 抵抗

交流電源と抵抗の回路を解く。

$$ 0 = E\_0 \sin \omega t - RI $$

より、抵抗の両端の電位は、即座に

$$ RI = E\_0 \sin \omega t $$

電流を求めると、

$$ I = \frac{E\_0}{R}\sin \omega t $$

抵抗の場合は、電位差と電流に位相差は無いことが分かった。

## コンデンサー

交流電源とコンデンサーの回路を解く。

$$ 0 = E\_0 \sin \omega t - \frac{1}{C} q $$

コンデンサーの電圧降下は、

$$ \frac{1}{C} q = E\_0 \sin \omega t $$

電荷は

$$ q = CE\_0 \sin \omega t $$

ところで、電流は以下のように定義することもある。

$$ I = \frac{dq}{dt} $$

これを用いて、電荷から電流を求めると、

$$\begin{align}
I &= \frac{dq}{dt} \\\\
&= CE\_0 \frac{d}{dt} \sin \omega t \\\\
&= CE\_0 \omega \sin(\omega t + \frac{1}{2} \pi)
\end{align}$$

コンデンサーを流れる電流と、両端の電位差を比較すると、電流の位相が進んでいることがわかる。コンデンサーとは微分の性質を持っていて、微分とは位相を進める事だった事からこのような事になった。

ただし「コンデンサーは位相が進む」と覚えても、進んでいるのが電流なのか電位なのかまで含めて覚えていなければ意味が無い。

今回は回路方程式、すなわち電位の式からこの結果を導いたので、**電位に対して**位相が進む、とおぼえておこう。

## コイル

交流電源とコイルの回路を解く。

$$ 0 = E\_0 \sin \omega t - L \frac{dI}{dt} $$

コイルの電圧降下は、

$$ L \frac{dI}{dt} = E\_0 \sin \omega t $$

次に電流を求める。ここで得られた式を積分すれば得られるだろう。

$$\begin{align}
I &= \int \frac{dI}{dt} dt \\\\
&= \int { \frac{E\_0}{L} \sin \omega t } \\\\
&= \frac{E\_0}{L \omega} \sin(\omega t - \frac{1}{2} \pi)
\end{align}$$

このように、コイルの場合、電位差に対して電流の位相が遅れる事が分かった。

## RCL並列回路

抵抗・コンデンサー・コイルを並列につないだ回路を解こう。各経路について回路方程式を立てる。

$$\begin{align}
0 &= E\_0 \sin \omega t - RI \\\\
0 &= E\_0 \sin \omega t - \frac{q}{C} \\\\
0 &= E\_0 \sin \omega t - L \frac{dI}{dt} \\\\
\end{align}$$

この式は先ほどすでに解いてある、それぞれに流れる電流に添字を付けて区別すると、

$$\begin{align}
I\_R &= \frac{E\_0}{R} \sin(\omega t) \\\\
I\_C &= E\_0 C \omega \sin(\omega t + \frac{1}{2} \pi) \\\\
I\_L &= \frac{E\_0}{L \omega} \sin(\omega t - \frac{1}{2} \pi) \\\\
\end{align}$$

これらの合成電流を考えると、

$$\begin{align}
I &= I\_R + I\_C + I\_L \\\\
&= \frac{E\_0}{R} \sin(\omega t) + E\_0 C \omega \sin(\omega t + \frac{1}{2} \pi) + \frac{E\_0}{L \omega} \sin(\omega t - \frac{1}{2} \pi) \\\\
\end{align}$$

このままでは計算を進められない。前後した位相をはやり$cos$に戻して計算しよう。

$$\begin{align}
&= \frac{E\_0}{R} \sin(\omega t) + E\_0 C \omega \sin(\omega t + \frac{1}{2} \pi) + \frac{E\_0}{L \omega} \sin(\omega t - \frac{1}{2} \pi) \\\\
&= \frac{E\_0}{R} \sin(\omega t) + E\_0 C \omega \cos(\omega t) - \frac{E\_0}{L \omega} \sin(\omega t) \\\\
&= \frac{E\_0}{R} \sin(\omega t) + (E\_0 C \omega - \frac{E\_0}{L \omega}) \cos(\omega t) \\\\
&= E\_0 [\frac{1}{R} \sin(\omega t) + (C \omega - \frac{1}{L \omega}) \cos(\omega t)] \\\\
\end{align}$$

最期に、三角関数の合成公式を適用すると、

$$\begin{align}
&= E\_0 [\frac{1}{R} \sin(\omega t) + (C \omega - \frac{1}{L \omega}) \cos(\omega t)] \\\\
&= E\_0 \sqrt{ (\frac{1}{R})^2 + (C \omega - \frac{1}{L \omega})^2 } \sin(\omega t + \alpha) \\\\
\end{align}$$

適当な係数で置き換えよう。

$$\begin{align}
&= E\_0 \sqrt{ (\frac{1}{R})^2 + (C \omega - \frac{1}{L \omega})^2 } \sin(\omega t + \alpha) \\\\
&= \frac{E\_0}{Z} \sin(\omega t + \alpha) \\\\
\end{align}$$

ただし

$$ Z = \frac{1}{ \sqrt{ (\frac{1}{R})^2 + (C \omega - \frac{1}{L \omega})^2 }  } $$

このように係数を取ると、これは抵抗と同じオームの次元を持つ。これは交流回路における合成抵抗に対応する概念で**インピーダンス**または**複素インピーダンス**と呼ばれる。

## RCL直列回路

抵抗・コンデンサー・コイルを直列につないだ回路を解こう。

$$\begin{align}
0 &= E\_0 \sin \omega t - RI - \frac{q}{C} - L \frac{dI}{dt} \\\\
&= E\_0 \sin \omega t - RI - \frac{1}{C} \int I dt - L \frac{dI}{dt} \\\\
E\_0 \sin \omega t &= RI + \frac{1}{C} \int I dt + L \frac{dI}{dt}
\end{align}$$

これは微分方程式なので高校生は解けない。でも、これは実は単振動の運動方程式と数学的には同型である。

高校生には解けないので、解を仮定して解き進めよう。以下のように仮定する。

$$ I = I\_0 \sin(\omega t + \theta\_0) $$

代入していこう。

$$\begin{align}
&= RI\_0 \sin(\omega t + \theta\_0) + \frac{1}{C} \int I\_0 \sin(\omega t + \theta\_0) dt + L \frac{d}{dt} I\_0 \sin(\omega t + \theta\_0) \\\\
&= RI\_0 \sin(\omega t + \theta\_0) - \frac{1}{C \omega} I\_0 \cos(\omega t + \theta\_0) + L \omega I\_0 \cos(\omega t + \theta\_0) \\\\
&= RI\_0 \sin(\omega t + \theta\_0) + (L \omega - \frac{1}{C \omega}) I\_0 \cos(\omega t + \theta\_0) \\\\
&= I\_0 [R \sin(\omega t + \theta\_0) + (L \omega - \frac{1}{C \omega}) \cos(\omega t + \theta\_0)] \\\\
&= I\_0 \sqrt{R^2 + (L \omega - \frac{1}{C \omega})^2} \sin(\omega t + \theta\_0 + \alpha) \\\\
&= Z I\_0 \sin(\omega t + \theta\_0 + \alpha) \\\\
\end{align}$$

インピーダンスは、

$$ Z = \sqrt{R^2 + (L \omega - \frac{1}{C \omega})^2} $$

が得られた。
