# GET-3: Diode

## Aufgabe B1: Dimensionierung Vorwiderstand LED

### Dimensionieren Sie den Vorwiderstand $R_1$ so, dass sich ein Diodenstrom $I_D=20mA$ bei $U_q=5V$ einstellt. Führen Sie die Berechnung ausführlich auf und prüfen ihr Ergebnis in LT-Spice.

$$U_q=U_R+U_D$$

Mit Hilfe der Diodenkennlinie aus LT-Spice bzw. dem Datenblatt der Diode lässt sich die Sperrspannung $U_D$ bestimmen.

$$U_D = 3.6 V$$

$$U_q-U_D=1.4V$$

$$\frac{U_R}{I_D}=\frac{1.4V}{20mA}=\underline{\underline{70\Omega}}$$

### Welche Leistungsaufnahme hat die Diode bei $I_D=20mA$?

$$P_D=U_D*I_D = 3.6V*20mA = \underline{\underline{0.072 W}}$$

## Aufgabe B2: Dimensionierung Kondensator einer B2U

Für eine Spanungsgleichrichtung mittels B2U ist die Größe des Kondensators $C_1$ zu dimensionieren, sodass am Widerstand $R_1$ der Spannungsrippel $\Delta U$ kleiner $0,5V$ ist.

$$C=I*\frac{\Delta t}{\Delta U}$$

Die Zeitdifferenz zwischen dem Minimum und dem Maximum entspricht einem Viertel der Periodendauer.

$$\Delta t = \frac{1}{4 * 50Hz} = 5ms$$

$$\Delta U = 0.5V$$

$$I = \frac{U}{\sqrt{2}*R} = \frac{10V}{\sqrt{2}*100\Omega} = 0.071A$$

$$C = 0.071A*\frac{5ms}{0.5V} = \underline{\underline{0,71mF}}$$

## Aufgabe B3: Lampenschaltung am Ausgang des Arduinos

### Berechnen Sie zunächst den erforderlichen Strom $I_{P1}$, der bei einer Versorgungsspannung $U_1=12V$ durch die Glühlampe fließt.

$$P=U*I \rightarrow I=\frac{P}{U}$$

$$\frac{5W}{12V}\approx 0,42 A = I_C$$

### Wie groß ist der Widerstand $R_1$ zu dimensionieren, wenn der Transistor eine Stromverstärkung $B=100$ besitzt? Die Basis-Emitter-Spannung kann mit $U_{BE}=0,75V$ angesehen werden.

$$B=\frac{I_C}{I_B} \rightarrow \frac{I_C}{B}=I_B$$

$$I_B=\frac{0,42A}{100}=4.2mA$$

$$R_1=\frac{U}{I_B}=\frac{5V-0.75V}{4.2mA}= ‭1011,9 \; \Omega‬$$

## Aufgabe B4: Linearer Spannungsregler

$$U_Z=6,5V \qquad I_Z=6,22mA \qquad U_{BE}=0,79V$$

$$U_1 = 12V - U_Z = 5,5V$$

$$U_2+U_3=U_Z$$

$$U_3=\left|-U_{BE}-U_L\right|=2,79V$$

$$U_2=U_Z-U_3=3,71V$$

$$\frac{U_2}{U_3}=\frac{R_2}{R_3}$$

$$𝑅_2+𝑅_3=10𝑘\Omega$$

$$R_2=\frac{10𝑘\Omega*U_2}{U_2+U_3}=\underline{\underline{5707.692 \Omega}}$$

$$R_3=\frac{10𝑘\Omega*U_3}{U_2+U_3}=\underline{\underline{4292.308 \Omega}}$$

$$I_2=\frac{U_2}{R_2}=\underline{\underline{0,65mA}}$$

$$I_3=\frac{U_3}{R_3}=\underline{\underline{0,489mA}}$$

$$I_b=I_2-I_3=\underline{\underline{0,161mA}}$$

## Aufgabe B5: Operationsverstärker

Durch die Kennlinie des Operationsverstärker lässt sich eine maximale Ausgangsspannung von $10,8V$ und eine Offsetspannung von $1.8V$ bestimmen. Der maximale Verstärkungsfaktor ergibt sich aus dem Verhältnis der Ein- und Ausgangsspannung und beträgt $V=\frac{10.8V-1.8V}{6mV}=1500$. Da der Einfluss der Widerstände $R_1$ und $R_2$ nur durch deren Verhältnis bestimmt wird, kann für einen der beiden Widerstände ein Wert festgelegt werden. Analog zu den Übungen kann so beispielsweise ein Widerstand von $R_2 = 100k\Omega$ angenommen werden. Durch den bereits bestimmten Verstärkungsfaktor lässt sich der verbleibende Widerstand $R_1 = \frac{R_2}{V-1} = 66.71\Omega$.

## Aufgabe B6: Subtrahierverstärker

Wenn $\frac{R_4}{R_2}=\frac{R_3}{R_1}$, dann gilt:

$$U_a=\frac{R_4}{R_2}(U_{e2}-U_{e1}) = \frac{R_3}{R_1}(U_{e2}-U_{e1})$$

$$\left|\frac{-7V}{2V-1,5V}\right| = 14$$

$$14 = \frac{R_4}{R_2}=\frac{R_3}{R_1}$$

Für die Widerstände $R_4$ und $R_3$ können Werte angenommen werden. Bsp.: $R_4 = R_3 = \underline{\underline{14k\Omega}}$. Daraus ergibt sich für die verbleibenden Widerstände $R_2 = R_1 = \underline{\underline{1 k\Omega}}$
