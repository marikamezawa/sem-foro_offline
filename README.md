# semáforo Offline
&nbsp;&nbsp;&nbsp;&nbsp;Este repositório contém a atividade prática de programação da semana 3, incluindo uma explicação detalhada sobre a proposta do projeto, a lista de materiais necessários e uma breve descrição da montagem do circuito. Ao final, são apresentadas as avaliações realizadas pelos meus colegas de sala sobre o projeto.

## 1. Objetivo
&nbsp;&nbsp;&nbsp;&nbsp;O objetivo dessa atividade, é programar um semáforo que garanta a segurança de pedestres e veículos, seguindo a lógica de tempo de cada fase das luzes, desde a montagem dos LEDs até a programação da sequência correta. 

## 2. Componentes utilizados
&nbsp;&nbsp;&nbsp;&nbsp;Para desenvolver o semáforo, será necessário os seuintes materiais:

| **Nome** | **Quantidade**| **Descrição** |
|----------|---------------|----------------|
|Protoboard| 01| Ferramenta para a montagem de circuitos eletrônicos com 400 pontos.
|Arduino Uno|  01| Placa de desenvolvimento versátil para protótipos eletrônicos e projetos IoT.
|Jumper|  14| Condutor curto para fechar, abrir ou desviar parte de um circuito eletrônico.
|LED|  03| Diodo semicondutor que quando energizado emite luz visível.
|Resistor|  04| Sensor de medição de distância. 
|Botão|  01| Dispositivo eletrônico que permite o controle manual para acionar ou interromper o funcionamento de um circuito eletrônico.

## 3. Instrução
&nbsp;&nbsp;&nbsp;&nbsp;**1. Posicionamento de LEDs e Resistores:** Insira os LEDs vermelho, amarelo e verde na protoboard. Conecte uma extremidade de um resistor de 1K Ohm à haste negativa (menor) de cada LED, e a outra extremidade ao barramento negativo da protoboard. Isso ajuda a limitar a corrente e proteger os LEDs.

<div align="center">
  <p><strong>Figura 1:</strong> LEDs e Resistores </p>
  <img src="assets\passo1.png" widht = 90% />
  <p><em>Créditos: material produzido pelo autor (2024)</em></p>
</div>

&nbsp;&nbsp;&nbsp;&nbsp;**2. Conexão dos Jumpers:** Depois conecte um jumper do barramento negativo da protoboard ao pino GND do Arduino Uno para garantir que todos os componentes compartilhem o mesmo aterramento. Em seguida, use três jumpers adicionais para conectar a haste positiva de cada LED a uma porta digital no Arduino (no meu exemplo, utilizei as portas 10, 9 e 8 para os LEDs vermelho, amarelo e verde, respectivamente).

<div align="center">
  <p><strong>Figura 2:</strong> Conexão dos Jumpers </p>
  <img src="assets\passo2.png" widht = 9% />
  <p><em>Créditos: material produzido pelo autor (2024)</em></p>
</div>

&nbsp;&nbsp;&nbsp;&nbsp;**3. Adicional (Botão de Ativação):** Esta etapa é opcional e adiciona uma funcionalidade extra ao semáforo offline: o acionamento do semáforo por meio de um botão. Para isso, foi necessário incluir o botão na protoboard e conectá-lo da seguinte forma:

- Conecte um jumper entre uma extremidade do botão e o barramento negativo da protoboard (aterramento).
- Conecte outro jumper do barramento positivo (5V) até o botão, fornecendo a tensão necessária.
- Use um terceiro jumper para conectar o botão ao pino digital 5 do Arduino.
- Por fim, adicione um resistor para estabilizar o circuito e evitar leituras incorretas ao pressionar o botão.

<div align="center">
  <p><strong>Figura 3:</strong> Botão </p>
  <img src="assets\passo3.png" widht = 9% />
  <p><em>Créditos: material produzido pelo autor (2024)</em></p>
</div>

&nbsp;&nbsp;&nbsp;&nbsp;**4. Código:**  Com a montagem e as conexões finalizadas, implemente o código para ativar o funcionamento do botão e controlar os LEDs conforme os tempos especificados na atividade:

- 6 segundos para o LED vermelho
- 2 segundos para o LED amarelo
- 4 segundos para o LED verde (2 segundos iniciais + 2 segundos extras para a travessia de pedestres)
- 2 segundos novamente para o LED amarelo

&nbsp;&nbsp;&nbsp;&nbsp;O código deve incluir a lógica para que, ao pressionar o botão, o ciclo dos LEDs seja iniciado e executado nas sequências corretas.

## 4. Código

```cpp

int Buttonstate = 0;

void setup()
{
  pinMode(5, INPUT);
  pinMode(8, OUTPUT); 
  pinMode(9, OUTPUT); 
  pinMode(10, OUTPUT); 
}

void loop()
{
  if (digitalRead(5) == LOW) {

  digitalWrite(10, HIGH);
  delay(6000); 
  digitalWrite(10, LOW);
  
  digitalWrite(9, HIGH);
  delay(2000); 
  digitalWrite(9, LOW);
  
  digitalWrite(8, HIGH);
  delay(4000); 
  digitalWrite(8, LOW); 

  digitalWrite(9, HIGH);
  delay(2000); 
  digitalWrite(9, LOW);
 
}}
```


## 5. Foto

<div align="center">
  <p><strong>Figura 4:</strong> Foto do semáforo  </p>
  <img src="assets\semaforo.jpg" widht = 80% />
  <p><em>Créditos: material produzido pelo autor (2024)</em></p>
</div>

## 6. Vídeo
<div>
<p> Vídeo do semáforo  </p>
</div>


https://github.com/user-attachments/assets/84134aae-0431-4f20-b075-3f3488a2b491

Caso o vídeo não rode, você pode acessar ele clicando [aqui](https://drive.google.com/file/d/17yqP2TNr6d8Hy-jwM15HBv4_AngBT8RH/view?usp=sharing) e em seguide baixe o vídeo para ser possível assistir.

## 7. Avaliação Pares

### Avaliador: Cecília Galvão

| Critério                                                                                                 | Contempla (Pontos) | Contempla Parcialmente (Pontos) | Não Contempla (Pontos) | Observações do Avaliador |
|---------------------------------------------------------------------------------------------------------|--------------------|----------------------------------|--------------------------|---------------------------|
| Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores                | Até 3              | Até 1,5                            | 0                        |                     3      |
| Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo                  | Até 3              | Até 1,5                          | 0                        |             3              |
| Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) | Até 3              | Até 1,5                          | 0                        |             3              |
| Extra: Implmeentou um componente de liga/desliga no semáforo e/ou usou ponteiros no código | Até 1              |  Até 0,5                         | 0                        |                 1          |
|  |                                                             |  | **Pontuação Total**|10|

### Avaliador: Pablo Azevedo 

| Critério                                                                                                 | Contempla (Pontos) | Contempla Parcialmente (Pontos) | Não Contempla (Pontos) | Observações do Avaliador |
|---------------------------------------------------------------------------------------------------------|--------------------|----------------------------------|--------------------------|---------------------------|
| Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores                | Até 3              | Até 1,5                            | 0                        |                     3      |
| Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo                  | Até 3              | Até 1,5                          | 0                        |             3              |
| Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) | Até 3              | Até 1,5                          | 0                        |             3              |
| Extra: Implmeentou um componente de liga/desliga no semáforo e/ou usou ponteiros no código | Até 1              |  Até 0,5                         | 0                        |                 1          |
|  |                                                             |  | **Pontuação Total**|10|

