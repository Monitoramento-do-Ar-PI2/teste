# Solução

Os requisitos dos subtemas do projeto foram levantados para a proposta de solução. Primeiramente as diretorias de cada área se reuniram para discutir uma proposta e, então, iniciou-se a etapa de desenvolvimento do projeto.

As simulações de circuitos elétricos foram realizadas através do Software Proteus, versão 8.9. Os esquemáticos, usados para confeccionar o layout da PCB e gerar o 3D das placas de circuitos, foram feitos através do Software KiCad (5.1.6).

## 1. Solução Elétrica

### 1.1 Sensor de temperatura, umidade e pressão

A temperatura, umidade e pressão são fatores importantes para a qualidade do ar. Dessa forma, o Zéfiro para medir essas variáveis utilizará o sensor Adafruit BME280, que realiza a leitura das três variáveis meteorológicas, com boa acurácia e resolução de leitura.

O sensor BME280 é um sensor especialmente desenvolvido para aplicações móveis e compactas, onde tamanho e baixo consumo de energia são os parâmetros importantíssimos de design. Criado pela BOSCH, este sensor é um 3 em 1 que oferece sensores de alta linearidade, alta precisão, estabilidade a longo prazo e alta robustez EMC.(LOPES, 2017). A lista abaixo, resume as características técnicas do sensor:

1. Faixa de Operação
   
  a) Pressão: 300 a 1100 hPa;

  b) Temperatura: -40 a 85 ∘C;

  c) Umidade: 0 a 100 %RH (dentro da faixa de 0 a 60 ∘C)

1. Alimentação: 3V ou 5V;
   
2. Comunicação: I2C OU SPI;
   
3. Corrente durante ações:
   
  a) Modo de espera: 0.5 𝜇A;

  b) Medição de umidade: 340 𝜇A;

  c) Medição de pressão: 714 𝜇A;

  d) Medição de temperatura: 350𝜇A;


### 1.2 Sensores de qualidade de ar

#### 1.2.1 Sensores de gás

Os sensores de gás usados no Zéfiro são os da Alphasense, que é uma marca inglesa com um vasto conjunto óticos e eletroquímicos, dependendo dos gases (no caso do projeto, todos são eletroquímicos). Em relação a qualidade do ar, a Alphasense é a empresa que tem a maior oferta de sensores desenvolvidos tão somente para a medição de poluentes gasosos concentrados no ar.

Os sensores do projeto são células eletroquímicas que operam no modo amperométrico. Ou seja, eles geram uma corrente que é linearmente proporcional ao volume fracionário do gás tóxico a ser medido. A Figura 1 mostra esquematicamente a estrutura de um sensor de gás tóxico.

O eletrodo de trabalho (também chamado de eletrodo de detecção) é projetado para otimizar a oxidação ou redução do gás tóxico a ser medido. Este eletrodo permite que o gás entre em contato com o eletrodo e o eletrólito para criar uma interface de fase de gás, líquido e sólido.

O eletrodo de trabalho é a superfície onde ocorre a oxidação eletroquímica (CO, H2S, NO, SO2) ou redução (NO2, Cl2) ocorre. Um catalisador de alta área de superfície é usado para otimizar o desempenho do sensor, resultando em uma alta capacitância do sensor: normalmente 50 a 200 mF, levando à suscetibilidade à interferência eletromagnética.

Este eletrodo é exposto ao ar externo e, portanto, está diretamente exposto a todos esses gases no ar, incluindo o gás a ser medido. Portanto, este eletrodo pode ser envenenado se exposto a certos gases que se absorvem no catalisador (por exemplo acetileno em sensores de CO), ou reagem, criando subprodutos que inibem o catalisador (por exemplo, NO2 ou aromáticos em sensores de H2S). Este é o mesmo problema de envenenamento em células de combustível e conversores catalíticos automotivos.

Além do eletrodo de trabalho, os sensores possuem mais três eletrodos: eletrodo auxiliar, contra-eletrodo e eletrodo de referência. O eletrodo auxiliar possui as mesmas características do eletrodo de trabalho, mas não é exposto ao gás que se pretende medir. O eletrodo de referência permite que os dois eletrodos (trabalho e auxiliar) estejam referenciados a uma tensão elétrica fixa, a fim de garantir que o sensor esteja trabalhando na
região correta da curva de corrente e tensão e, por último, o contra-eletrodo, que completa o balanço eletroquímico.(GOMES, 2015).

**Curva de corrente-tensão**

A corrente do eletrodo de trabalho muda quando o potencial aplicado é variado, produzindo uma curva  corrente-tensão; um diagrama esquemático de uma curva de tensão de corrente típica é mostrado na Figura 2