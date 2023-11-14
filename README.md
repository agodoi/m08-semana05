# Interfaces de comunicação para sistemas embarcados

Ao longo deste encontro, o objetivo principal é apresentar aos estudantes os conceitos principais de comunicação, no contexto de sistemas embarcados. Apresentação das principais interfaces de comunicação utilizadas em sistemas embarcados, como comunicação serial, I2C, SPI, apenas para listar algumas. Os conceitos de comunicação apresentados serão implementados pelos estudantes, de forma guiada para validar o comportamento das interfaces. Espera se que depois desta etapa de implementação, os estudantes sintam-se preparados para implementar as interfaces nos projetos que apresentem este tipo de demanda. Neste encontro serão abordados: Apresentação das interfaces de comunicação; Implementação da interface de comunicação serial assíncrona; Implementação da interface de comunicação SPI síncrona; Avaliação das interfaces de comunicação.

Assuntos relacionados:
* Atuadores
* Dispositivos lógico-programáveis
* Energia em sistemas embarcados
* Interfaces de comunicação
* Microcontroladores
* Programação de microcontroladores
* Segurança em sistemas embarcados
* Sensores analógicos e digitais


# Por que haver uma comunicação entre dispositivos embarcados?

No vasto ecossistema da computação embarcada, a comunicação entre dispositivos desempenha um papel crucial que vai muito além de uma simples troca de dados. É fundamental compreender que os microcontroladores, componentes-chave nesse cenário, frequentemente operam em conjunto para realizar tarefas complexas e, para atingir eficiência máxima, a comunicação entre eles se torna imperativa.

**1. Coordenação e Sincronização:**
Em um sistema embarcado, diferentes dispositivos muitas vezes precisam agir em conjunto para realizar funções específicas. A comunicação permite a coordenação e sincronização eficientes entre esses dispositivos. Por exemplo, em um sistema de controle automotivo, os microcontroladores responsáveis pelo motor, transmissão e freios precisam se comunicar para garantir um desempenho seguro e eficaz do veículo.

**2. Otimização de Recursos:**
A comunicação entre dispositivos embarcados possibilita a otimização de recursos, um aspecto crucial na concepção de sistemas eficientes. Por meio da troca de informações, os dispositivos podem ajustar seu funcionamento conforme as demandas, evitando desperdício de energia e maximizando a eficiência operacional.

**3. Modularidade e Escalabilidade:**
A comunicação entre dispositivos oferece uma base sólida para a construção de sistemas modulares e escaláveis. Microcontroladores podem ser adicionados ou removidos conforme necessário, facilitando atualizações e expansões no sistema sem a necessidade de redesenhos completos.

**4. Resiliência e Redundância:**
Em ambientes críticos, como sistemas de equipamentos médicos ou de controle de aeronaves, a comunicação entre dispositivos permite a implementação de estratégias de resiliência e redundância. A troca contínua de informações possibilita a rápida detecção de falhas e a ativação de mecanismos de backup, garantindo a continuidade operacional.

**5. Flexibilidade e Adaptabilidade:**
A comunicação entre dispositivos confere flexibilidade ao sistema. Os microcontroladores podem ser programados para se adaptar a diferentes condições e cenários, respondendo a mudanças nas entradas ou requisitos do sistema. Isso é crucial em aplicações dinâmicas, como automação residencial, onde os dispositivos precisam se ajustar a padrões de uso variáveis.

**Conclusão:**
Em resumo, a comunicação entre dispositivos embarcados transcende a mera transferência de dados, sendo a espinha dorsal de sistemas complexos. Ela viabiliza a sinergia entre componentes, impulsiona a eficiência operacional e confere a flexibilidade necessária para enfrentar os desafios dos ambientes modernos. Ao explorar esses conceitos, os estudantes e profissionais de microcontroladores estarão mais bem equipados para criar soluções inovadoras e robustas no mundo da computação embarcada.

# Quais os tipos de comunicação

Existem diversos tipos de comunicação entre dispositivos embarcados, cada um adaptado para necessidades específicas. Abaixo, estão alguns dos tipos mais comuns:

1. **Comunicação Serial:**
   - **UART (Universal Asynchronous Receiver/Transmitter):** Permite a transmissão serial assíncrona de dados entre dispositivos. No autoestudo, tem-se a documentação do [pySerial](https://pyserial.readthedocs.io/en/latest/pyserial.html). Aqui tem um [exemplo](https://blog.eletrogate.com/como-conectar-o-arduino-com-o-python/) de aplicação do pySerial.
   - **SPI (Serial Peripheral Interface):** Usado para comunicação síncrona entre um mestre e vários dispositivos periféricos.
   - **I2C (Inter-Integrated Circuit):** Facilita a comunicação entre componentes em uma placa de circuito, utilizando apenas dois fios.

2. **Comunicação Paralela:**
   - **Paralela de Dados:** Transmissão simultânea de vários bits de dados, comumente usada para transferência rápida de dados em curtas distâncias.

3. **Comunicação Wireless:**
   - **Bluetooth:** Ideal para comunicação de curto alcance entre dispositivos, com aplicações em áudio, dispositivos móveis, e periféricos.
   - **Wi-Fi:** Proporciona comunicação sem fio de médio a longo alcance, sendo amplamente utilizado para conectividade à internet em dispositivos embarcados.
   - **RFID (Radio-Frequency Identification):** Usa ondas de rádio para identificar e rastrear objetos, com aplicações em controle de estoque e segurança.

4. **Comunicação de Rede:**
   - **Ethernet:** Utilizada para comunicação em redes locais (LAN), permitindo a conexão de dispositivos embarcados a sistemas mais amplos.
   - **CAN (Controller Area Network):** Projetada para comunicação em tempo real em sistemas embarcados, frequentemente utilizada em veículos para troca de dados entre unidades de controle.

5. **Comunicação Analógica:**
   - **PWM (Pulse Width Modulation):** Usada para controlar a potência de dispositivos analógicos, como motores e LEDs, variando a largura de pulsos.
   - **ADC (Analog-to-Digital Converter):** Converte sinais analógicos em digitais, essencial para processamento digital de sinais analógicos.

6. **Comunicação de Barramento:**
   - **PCI (Peripheral Component Interconnect):** Padrão para conexão de dispositivos de hardware em computadores.
   - **USB (Universal Serial Bus):** Utilizado para conectar dispositivos diversos, desde periféricos simples até dispositivos de armazenamento e áudio.

7. **Comunicação de Campo (Fieldbus):**
   - **Profibus, Modbus, CANopen:** São protocolos de comunicação de campo amplamente utilizados na automação industrial para interconectar dispositivos em tempo real.

8. **Comunicação de Rádio Frequência (RF):**
   - **Zigbee, LoRa (Long Range):** São utilizados para comunicação sem fio em longas distâncias, sendo aplicáveis em redes de sensores e comunicação de baixa potência.

# Definições rápidas

Seguem 3 características de cada tipo de comunicação: Serial, Wireless e Rede:

**1. Comunicação Serial:**
   - **UART (Universal Asynchronous Receiver/Transmitter):**
     - Taxa de Transmissão Ajustável (Baud Rate).
     - Utiliza apenas dois fios para transmissão (TX - Transmit e RX - Receive) + fio referência, GND (Ground).
     - Ideal para comunicação ponto a ponto.

   - **SPI (Serial Peripheral Interface):**
     - Comunicação Síncrona.
     - Possui linhas dedicadas para mestre e escravos (MISO, MOSI, SCLK).
     - Suporta velocidades de transferência de dados mais elevadas em comparação com UART.

   - **I2C (Inter-Integrated Circuit):**
     - Dois fios para comunicação (SDA - Serial Data e SCL - Serial Clock) + fio referência, GND.
     - Permite múltiplos dispositivos em um barramento. Até 128 dispositivos diferentes nos mesmos fios SDA e SCL.
     - Suporta transferência de dados em alta velocidade.

**2. Comunicação Wireless:**
   - **Bluetooth:**
     - Variedade de perfis para diferentes aplicações (por exemplo, A2DP - Advanced Audio Distribution Profile, para áudio).
     - Consumo de energia otimizado em modos de baixa potência.
     - Suporte a emparelhamento seguro.

   - **Wi-Fi:**
     - Suporte a redes locais (LAN).
     - Alta taxa de transferência de dados.
     - Criptografia integrada para segurança de dados.

   - **RFID (Radio-Frequency Identification):**
     - Leitura sem contato.
     - Utiliza frequências de rádio para comunicação gratuitas.
     - Ampla aplicação em logística, controle de acesso e rastreamento.

**3. Comunicação de Rede:**
   - **Ethernet:**
     - Padrão para redes locais (LAN).
     - Taxas de transferência de dados de 10/100/1000 Mbps.
     - Utiliza protocolos como TCP/IP para comunicação.

   - **CAN (Controller Area Network):**
     - Projetado para comunicação robusta em ambientes automotivos e industriais.
     - Topologia de barramento.
     - Suporta comunicação de alta velocidade e baixa latência.

   - **MIDI (Musical Instrument Digital Interface):**
     - Originalmente desenvolvido para comunicação entre instrumentos musicais eletrônicos.
     - Utiliza conectores padrão de cinco pinos.
     - Transmissão de eventos musicais em tempo real.

# Comunicação Serial
## pontos positivos

## pontos negativos

# Comunicação I2C

## pontos positivos

## pontos negativos

# Comunicação SPI

## Pontos positivos

## Pontos negativos

# Comunicação UART

## Pontos positivos

## Pontos negativos
