# Analysis

## Zahlenfolgen, Grenzwerte von Zahlenfolgen

### Aufgabe 1
$$\begin{matrix}
a_0 = 0 \\
a_1 = \frac{a_0}{2}+1 = 1 \\
a_2 = \frac{a_1}{2}+1 = \frac{3}{2} \\
a_3 = \frac{a_2}{2}+1 = \frac{7}{8} \\
\vdots \\
a_n = 2
\end{matrix}$$
Der Grenzwert der gegebenen Funktion entspricht 2.

### Aufgabe 2: Bestimmung von Grenzwerten

Zur rechnerischen Bestimmung von Grenzwerten muss der Grad des Zählers dem des Nenners entsprechen. Sollte dies nicht der Fall sein, ist der Grenzwert entweder $0$ oder $\pm \ \infty$.

$$a_k := \frac{4k-3}{6-5k}$$

Faktoren vor dem höchsten Exponenten:

$$\frac{4}{-5}$$

Daraus ergibt sich folgender Grenzwert:

$$\lim\limits_{k \rightarrow \infty}{a_k} \rightarrow \frac{4}{-5}$$

Im folgenden Beispiel müssen zunächst die Klammern aufgelöst werden

$$a_k := \frac{2k(k-1)^2}{(k+2)^3}=\frac{2k(k^2-2k+1)}{k^3+8}=\frac{2k^3-4k^2+2k)}{k^3+8}$$

$$\lim\limits_{k \rightarrow \infty}{a_k} \rightarrow 2$$

### Aufgabe 3: Grenzwertbeziehungen

Bestimme folgende Grenzwerte mit Hilfe der Grenzwertbeziehung $\lim\limits_{k \rightarrow \infty}{(1+\frac{x}{k})^k}=e^x$.

$$a_k := (1+\frac{3}{k})^k \qquad \lim\limits_{k \rightarrow \infty}{(1+\frac{3}{k})^k}=e^3$$

$$a_k := (1+\frac{1}{2k})^k \qquad \lim\limits_{k \rightarrow \infty}{(1+\frac{1}{2k})^k}=e^{\frac{1}{2}}=\sqrt{e}$$

$$a_k := (1-\frac{5}{k})^{\frac{k}{4}+3} =  (1-\frac{5}{k})^{\frac{k}{4}}  (1-\frac{5}{k})^{3}$$

$$\lim\limits_{k \rightarrow \infty}{(1-\frac{5}{k})^{3}}\rightarrow 1$$


$$\lim\limits_{k \rightarrow \infty}{(1-\frac{5}{k})^{k^{\frac{1}{4}}}}=e^{-5^{\frac{1}{4}}}=e^{-\frac{5}{4}}$$

### Aufgabe 4: Werte geometrischer Reihen

Bestomme unter Zuhilfename der geometrischen Reihe $\sum_{k=0}^{\infty} q^k =\frac{1}{1-q}$ die Werte folgender Reihen:

$$\sum_{k=0}^{\infty} \frac{2^k}{3^{k+1}} \rightarrow \sum_{k=0}^{\infty} (\frac{2}{3})^k \times \frac{1}{3} \rightarrow \frac{1}{3} \times \frac{1}{1-\frac{2}{3}}=1$$

Beginnt die Reihe nicht bei 0, so muss noch mit $q^n$ multipliziert werden:

$$\sum_{k=3}^{\infty} \frac{2^{k+2}}{3^{k+1}} \rightarrow \sum_{k=3}^{\infty} (\frac{2}{3})^k \times \frac{4}{3} = \frac{4}{3} \times \frac{1}{1-\frac{2}{3}} \times (\frac{2}{3})^3=\frac{32}{27}$$

$$\sum_{k=3}^{\infty} \frac{2^{2k}}{5^k} = \sum_{k=3}^{\infty} (\frac{4}{5})^k = \frac{1}{1-\frac{4}{5}}=5$$
