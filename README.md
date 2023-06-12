
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

179.6/o que queremos = n1/n2;

## Diodos / Ponte de diodos

Sem diodos e com uma transformador n1/n2 = 10, a tensao em uma resistência, varia conforme o seguinte gráfico (apresentando tensões negativas, o que não é desejado)

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




