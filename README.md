
# Fonte de Tensão ajustável(3v - 12v)

Buscamos diagramar e construir uma fonte com capacidade para até 100mA de corrente e uma tensão ajustável dada uma fonte inicial de 127V.






## Transformador

O Transformador é necessário para ajustar a tensão alternada residencial com tensão maxima de 179.6V e frequência de 60Hz para uma tensão que o aparelho possa receber.

A tensão eficaz é o equivalente contínuo de uma fonte alternada e seu cálculo é dado por:  

$V{ef}=\frac{V{max}}{\sqrt{2}}$

$V{ef}=\frac{179.6}{\sqrt{2}}$

$V{ef}\approx127$

A razão entre o número de voltas na espira primária e secundária é diretamente proporcional a razão entre a voltagem primária e secundária 

![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/assets/128495824/1f843eb6-1e2e-46d0-9f88-eb5aba02f8c8)


Logo, a equação se dá por:

$\frac{V_1}{V_2}=\frac{N_1}{N_2}$

Aplicando:

$\frac{179.6}{24.6}=\frac{N_1}{N_2}$

## Diodos / Ponte de diodos

Sem diodos e com uma transformador $\frac{N_1}{N_2}=10$, a tensao em uma resistência, varia conforme o seguinte gráfico (apresentando tensões negativas, o que não é desejado)

![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/assets/128495824/8dba6314-f129-4f2b-b983-e84d2f787b04)

Com uma retificador de meia onda, ou seja, apenas um diodo, a tensão em uma resistencia varia da seguinte maneira

![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/assets/128495824/bcdb7ee7-a130-4338-96fd-8f611e7a08c7)

Assim, será necessária uma ponte de diodos para retificar a corrente (manter o sentido da corrente após o transformador)
Um diodo permite que a corrente passe em apenas um sentido. Uma ponte de diodos associa 4 diodos como mostrado na imagem para que a fonte alternada de tensões positivas e negativas se polarize apenas em tensões positivas.

![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/assets/128495824/e82fc914-da09-455a-b5ef-d3aa6a5a751c)

![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/assets/128495824/c2eb18fb-68f5-42f5-aa4a-363e8e6bfe75)

(note que dois diodos consomem cerca de 1.4v)

Cada diodo de sílicio consome cerca de 0.7V, e como são utilizados dois por vez, um consumo de 1.4V deve ser considerado. 

## Capacitor

Apos retificar a tensão, é necessário evitar que ela chegue a 0. Para isso, utilizaremos um capacitor, que impede a queda de tensão total, mantendo-a mais próxima de uma voltagem constante para a resistência final.

Em eletrônica, capacitância é uma grandeza oposta à voltagem, sendo gerada pelo acúmulo de carga em uma determinada região, sendo que há inexistência de corrente entre uma região e outra. 
Dessa forma, capacitores são dispositivos compostos por duas placas isoladas entre si e próximas, assim ao passar uma corrente por ele (a corrente não passa realmente pela existência de material isolante entre as placas, apenas é gerada pela indução das cargas), um dos lados terá acúmulo de elétrons que gerará uma indução crescente até que as placas atinjam seu limite de carga (no infinito). Quando a tensão da fonte for menor do que a sua interna, a carga acumulada gerará uma corrente no sentido inverso, até que ela seja novamente 0 (o que não chega a acontecer no nosso circuito).
O tempo de carga de um capacitor até que esse chegue a 98%, pode ser aproximado por $t=5\cdot R\cdot C$

![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/assets/128495824/8ad8f747-13f5-4e99-9d3e-3284eff435e2)

Esse agora é o comportamento da tensão, com um capacitor em paralelo no circuito, a tensão ainda varia nesse padrão que se denomina ripple. E o valor do ripple(diferença entre máximo e mínimo) é calculado por ripple = $\frac{V_2-2\cdot D}{2\cdot f\cdot C\cdot R}$

O valor máximo é a tensão após a fonte de diodos, que é 24.6(medido no transformador)-2Diodos, = 23.2V
O valor mínimo é o maximo decrescido do ripple(cerca de 23.6V, considerando um ripple de 4.3%).

Considerando um ripple de 4.3% após a ponte de diodos (equivalente a 1V) e aplicando na fórmula, a capcitância encontrada é de 1mF, que é um valor comercial.
Agora, resta eliminar o ripple.

## Diodo zener

O diodo zener é um componente eletrônico que permite a passagem da corrente em apenas um sentido como um diodo normal, no outro sentido ele consome uma tensão cosntante. Ele é utilizado na fonte como um regulador de tensão, com o objetivo de manter uma corrente contínua. Para este projeto, a sua tensão limite é de 13V, pois, se esse limite não for atingido, ele não se torna condutor e 13V é o valor comercial mais próximo acima de 12,7V(valor do transitor mais o valor máximo fornecido). Além disso, ele opera a uma potência de 500 miliwatts.


![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/assets/128495824/3ec42bf5-eec7-451e-8fe3-abe763374f84)


## Transistor

O transistor bipolar é um componente que funciona como amplificador de corrente, sendo que a corrente do coletor para a base é cerca de 100 vezes menor do que a corrente da base para o emissor.
Utilizaremos ele para permitir a passagem da corrente estabilizada ao mesmo tempo em que recebe a tensão controlada pelo zener. O transistor consome 0.7V.

## Potenciometro

O potenciometro opera como uma resistência variável para permitir a troca de tensão fornecida. Quando o seu valor é mínimo, a tensão fornecida é a mesma da tensão que o zener permite menos a tensão consumida pelo transistor. Quando a resistência é máxima, a potência entregue é 0V. Para corrigir isso, adicionamos duas resistências de 820 em série após o potênciometro para que a voltagem mínima seja de cerca 1.2V.
Foi utilizado um potênciometro de 10k.





# Tabela de Preços

|Componente|Preço unitário|Quantidade|Subtotal
|---|---|---|---|
[Led 5mm Verde](https://www.baudaeletronica.com.br/produto/led-difuso-5mm-verde)|R$ 0,27|1|R$ 0,27
[LED Difuso 3mm Vermelho](https://www.baudaeletronica.com.br/produto/led-difuso-3mm-vermelho)|R$ 0,25|3|R$ 0,75
[LED Difuso 5mm Azul](https://www.baudaeletronica.com.br/produto/led-difuso-5mm-azul)|R$ 0,27|1|R$ 0,27
[Resistor 820R 5% (2W)](https://www.baudaeletronica.com.br/produto/resistor-820r-5-2w.html)|R$ 0,42|4|R$ 1,68
[Transistor NPN 2N2222](https://www.baudaeletronica.com.br/produto/transistor-npn-2n2222.html)|R$ 0,55|4|R$ 2,20
[Ponte Retificadora KBPC1010](https://www.baudaeletronica.com.br/produto/ponte-retificadora-kbpc1010.html)|R$ 4,90|2|R$ 9,80
[Capacitor Eletrolítico 1000uF / 25V](https://www.baudaeletronica.com.br/produto/capacitor-eletrolitico-1000uf-25v-105c.html)|R$ 0,95|4|R$ 3,80
[Resistor 82R 5% (2W)](https://www.baudaeletronica.com.br/produto/resistor-82r-5-2w.html)|R$ 0,42|3|R$ 1,26
[Potenciômetro Linear de 10K (10000Ω)](https://www.baudaeletronica.com.br/produto/potenciometro-linear-de-10k-10000.html)|R$ 2,70|1|R$ 2,70
[Diodo Zener BZX55C (13V / 0.5W)](https://www.baudaeletronica.com.br/produto/diodo-zener-bzx55c-13v-05w.html)|R$ 0,09|5|R$ 0,45
[Resistor 5K1 5% (2W)](https://www.baudaeletronica.com.br/produto/resistor-5k1-5-2w.html)|R$ 0,42|3|R$ 1,26
[Protoboard 170 Pontos Azul](https://www.baudaeletronica.com.br/produto/protoboard-170-pontos-azul.html)|R$ 4,75|2|R$ 9,50
[Resistor 3K 5% (1/4W)](https://www.baudaeletronica.com.br/produto/resistor-3k-5-14w.html)|R$ 0,06|4|R$ 0,24
Frete|||R$ 18,16
TOTAL:|||R$ 52,34

# Circuito do Falstad
![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/blob/main/Imagens/falstad.PNG)

## Link para o circuito
[https://tinyurl.com/2bppeaun](https://tinyurl.com/26yewllb)

# Esquemático da PCB (EAGLE)
![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/blob/main/Imagens/esquematico.PNG)

# PCB (EAGLE)
![image](https://github.com/pedrohfsilva/trabalho-de-eletronica/blob/main/Imagens/PCB.PNG)


## Alunos

Bruno Figueiredo Lima - 14562383

Gabriel Antunes Afonso de Araujo - 14571077

Lázaro Pereira Vinaud Neto - 14675396

Pedro Henrique Ferreira Silva - 14677526
