# GET-3: Diode

## Aufgabe B1: Dimensionierung Vorwiderstand LED

### Dimensionieren Sie den Vorwiderstand $R_1$ so, dass sich ein Diodenstrom $I_D=20mA$ bei $U_q=5V$ einstellt. Führen Sie die Berechnung ausführlich auf und prüfen ihr Ergebnis in LT-Spice.

$$U_q=U_R+U_D$$

Datasheet: $U_D = 3.6 V$
$$U_q-U_D=1.4V$$

$$\frac{U_R}{I_D}=\frac{1.4V}{20mA}=70\Omega$$

### Welche Leistungsaufnahme hat die Diode bei ID=20mA.

$$P_D=U_D*I_D = 3.6V*20mA = 0.072 W$$

## Aufgabe B2: Dimensionierung Kondensator einer B2U

$$C=I*\frac{\Delta t}{\Delta U}$$

$$\Delta t = 5ms$$

$$\Delta U = 0.5V$$

$$I = 0.1A$$

$$C=0.1*\frac{5ms}{0.5V} = 1mF$$

## Aufgabe B3: Lampenschaltung am Ausgang des Arduinos

### Berechnen Sie zunächst den erforderlichen Strom $I_{P1}$, der bei einer Versorgungsspannung $U_1=12V$ durch die Glühlampe fließt.

$$P=U*I \rightarrow I=\frac{P}{U}$$

$$\frac{5W}{12V}\approx 0,42 A = I_C$$

### Wie groß ist der Widerstand $R_1$ zu dimensionieren, wenn der Transistor eine Stromverstärkung $B=100$ besitzt? Die Basis-Emitter-Spannung kann mit $U_{BE}=0,75V$ angesehen werden.

$$B=\frac{I_C}{I_B} \rightarrow \frac{I_C}{B}=I_B$$

$$I_B=\frac{0,42A}{100}=4.2mA$$

$$R_1=\frac{U}{I_B}=\frac{5V}{4.2mA}= ‭1190,5 \;\Omega‬$$

## Aufgabe B4: Linearer Spannungsregler

$$𝑅_2+𝑅_3=10𝑘\Omega$$

$$U_Z=6,5V \qquad I_Z=6,22mA \qquad U_{BE}=0,79V$$

$$U_1 = 12V - U_Z = 5,5V$$

$$U_2+U_3=U_Z$$

$$R_2=\frac{U_2}{I_2}$$

$$I_L=I_E=\frac{2V}{1k\Omega}=2mA$$

Brute-Force:
$$R_2=6000 \Omega$$
$$R_3=4000 \Omega$$
