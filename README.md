# ⚡ Sistema IoT de Monitoramento de Energia Elétrica

> **Monitoramento de tensão, corrente, potência e estimativa de custo utilizando ESP32, MQTT e ThingsBoard Cloud.**

---

## 📌 Visão Geral

Este projeto apresenta um protótipo de **monitoramento de energia elétrica utilizando IoT**, desenvolvido com ESP32.

O sistema realiza a leitura de sinais de tensão e corrente, processa os dados localmente no ESP32 e transmite as informações por meio do protocolo **MQTT** para o **ThingsBoard Cloud**, onde os dados podem ser visualizados em um dashboard em tempo real.

O projeto foi desenvolvido com foco em aprendizado e demonstração prática de conceitos de:

- IoT Industrial
- Sistemas embarcados
- Comunicação MQTT
- Processamento de dados na borda (*Edge Computing*)
- Telemetria
- Monitoramento de grandezas elétricas
- Visualização de dados em nuvem

---

## 🎯 Objetivo

Desenvolver uma solução IoT capaz de coletar grandezas elétricas, realizar processamento local e disponibilizar os dados remotamente por meio de uma plataforma de monitoramento em nuvem.

O projeto demonstra o fluxo completo:

**Aquisição → Processamento → Comunicação → Nuvem → Visualização**

---

## 🏗️ Arquitetura do Sistema

```text
┌─────────────────────┐
│     Sensores        │
│                     │
│ Tensão + Corrente   │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│        ESP32        │
│                     │
│ Aquisição de dados  │
│ Processamento local │
└──────────┬──────────┘
           │
           │ MQTT / JSON
           ▼
┌─────────────────────┐
│  ThingsBoard Cloud  │
│                     │
│ Telemetria / Dados  │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│      Dashboard      │
│                     │
│ V / A / W / Custo   │
└─────────────────────┘
```

### Camadas da solução

| Camada           | Tecnologia                        | Função                              |
| :--------------- | :-------------------------------- | :---------------------------------- |
| **Campo**        | Potenciômetros / sinais simulados | Simulação das grandezas elétricas   |
| **Edge**         | ESP32                             | Aquisição e processamento dos dados |
| **Comunicação**  | MQTT                              | Transmissão da telemetria           |
| **Cloud**        | ThingsBoard Cloud                 | Recepção e armazenamento dos dados  |
| **Visualização** | Dashboard ThingsBoard             | Monitoramento das informações       |

---

## ⚙️ Funcionalidades
## 📊 Monitoramento de grandezas

O sistema realiza a leitura de sinais analógicos utilizados para representar:

- Tensão (V)
- Corrente (A)

Os valores podem ser alterados durante a simulação para representar diferentes condições de operação.

## 🧮 Processamento local

O ESP32 realiza o processamento das informações recebidas e calcula:

- Estimativa de potência elétrica (W)
- Estimativa de custo por hora (R$)

O processamento ocorre localmente no dispositivo antes do envio dos dados para a nuvem.

## 📡 Telemetria MQTT

Os dados são enviados periodicamente utilizando o protocolo **MQTT**, permitindo a comunicação entre o ESP32 e o ThingsBoard Cloud.

As informações são organizadas em um payload no formato JSON.

## ☁️ Dashboard em Nuvem

O ThingsBoard Cloud é utilizado para receber e visualizar os dados enviados pelo ESP32.

O dashboard apresenta as informações de monitoramento de forma gráfica e em tempo real.

---

## 🛠️ Tecnologias Utilizadas
### Hardware / Firmware
### - ESP32
### - C++
### - Arduino Framework
### Comunicação
### - MQTT
- Biblioteca ``` PubSubClient ```
- Payload em formato JSON
### Cloud
### - ThingsBoard Cloud
### Simulação
### - Wokwi Simulator

---

## 🔗 Demonstração
### 🎮 Simulação Interativa

O firmware pode ser executado diretamente no navegador através do Wokwi:

👉 **[Acessar Simulação Interativa no Wokwi](https://wokwi.com/projects/472703937958391809)**

Durante a simulação, os potenciômetros podem ser utilizados para alterar os valores de tensão e corrente.

---

## 📈 Dashboard

O ThingsBoard recebe os dados enviados pelo ESP32 e apresenta as informações em um dashboard de monitoramento.

---

## 🔄 Fluxo de Funcionamento
**1.** Os sinais de tensão e corrente são simulados através dos componentes do Wokwi.
**2.** O ESP32 realiza a leitura dos sinais analógicos.
**3.** Os valores são processados localmente.
**4.** O sistema calcula uma estimativa de potência elétrica.
**5.** O custo estimado por hora é calculado a partir dos valores configurados.
**6.** Os dados são estruturados em um payload JSON.
**7.** O ESP32 estabelece comunicação utilizando MQTT.
**8.** A telemetria é enviada para o ThingsBoard Cloud.
**9.** O dashboard apresenta os dados para acompanhamento.

---

## 🧠 Conceitos Demonstrados

Este projeto demonstra conhecimentos em:

- Programação de microcontroladores
- ESP32
- Aquisição de sinais analógicos
- Processamento local (Edge Computing)
- Comunicação MQTT
- Estruturação de dados em JSON
- IoT
- Telemetria
- Integração com plataforma Cloud
- Monitoramento em tempo real
- Desenvolvimento de dashboards

---

## ⚠️ Limitações do Protótipo

Este projeto possui finalidade educacional e de demonstração técnica.

Os sinais de tensão e corrente utilizados na simulação são gerados no ambiente Wokwi e não representam uma medição elétrica realizada por um instrumento ou medidor de energia certificado.

Uma aplicação real exigiria:

- Sensores apropriados para tensão e corrente;
- Condicionamento e isolamento dos sinais;
- Proteções elétricas adequadas;
- Calibração dos sensores;
- Validação das medições;
- Projeto adequado de hardware e instalação;
- Avaliação das condições de segurança da aplicação.

A estimativa de potência apresentada no protótipo deve ser interpretada de acordo com o método de cálculo implementado e não como uma medição metrológica certificada.

---

## 🚀 Possíveis Evoluções

Como possíveis evoluções do projeto:

- Utilização de sensores reais de tensão e corrente;
- Medição de energia acumulada (kWh);
- Armazenamento histórico das medições;
- Criação de alarmes para condições anormais;
- Monitoramento de múltiplos circuitos;
- Inclusão de fator de potência quando aplicável;
- Implementação de análises de consumo;
- Integração com outros sistemas de automação.

---

## 📁 Estrutura do Projeto
```text
ESP32-Energy-Monitor-IoT/
│
├── src/
│   └── código do projeto
│
├── Medidor-Energetico.png
├── simulacao.gif
├── diagram.json
├── wokwi.toml
└── README.md
```

---

## 📚 Objetivo de Aprendizado

O projeto foi desenvolvido como parte da construção de um portfólio técnico voltado para **IoT, Automação Industrial e sistemas embarcados.**

A proposta é demonstrar, de forma prática, a integração entre:

### Eletrônica → Firmware → Comunicação → Cloud → Visualização

---

## 👨‍💻 Autor

Raphael Alves Ferreira

Desenvolvimento de soluções em Automação Industrial, IoT e sistemas embarcados.
