# 🚀 Arduino Full-Bridge Shield: Acionamento de Potência para Motor ME19006 (ME0909)

O objetivo principal é criar uma ponte completa (*Full-Bridge*) robusta e didática para realizar ensaios de eficiência e testes de técnicas avançadas de modulação chaveada no motor **ME19006 (ME0909)**, utilizado no barco da equipe de corrida **Zênite Solar (IFSC)**.


A arquitetura foi pensada em formato Shield para o ecossistema Arduino, facilitando a troca rápida de códigos de controle e aquisição de dados durante as bancadas de teste.


## 📋 Especificações do Sistema

O projeto foi dimensionado para operar nas condições reais de teste da equipe de barco solar, trabalhando com alta margem de segurança elétrica e térmica:

| **Parâmetro / Componente** | **Especificação** | **Descrição / Justificativa** |
| :--- | :--- | :--- |
| **Tensão de Barramento** | `60V DC` | Tensão nominal de alimentação do barramento de tração do barco da equipe **Zênite Solar (IFSC)**. |
| **Corrente Máxima** | `50A` | Corrente máxima de teste estipulada para validação das modulações do TCC. |
| **Motor Alvo** | `ME19006 (ME0909)` | Motor utilizado no barco da equipe Zenite Solar (IFSC). |
| **Gate Driver** | `MP1923` | Driver Half-Bridge de 100V. Fornece 7A/8A de pico. |
| **MOSFET de Potência** | `IXFN420N10T` | MOSFET utilizado no barco da equipe Zenite Solar(IFSC). |
| **Frequência de Chaveamento** | `6 kHz a 12 kHz` | Faixa de frequência de modulação otimizada para o motor e para minimizar perdas no driver. |

## 🛡️ Destaques de Projeto da PCB

Para garantir que a placa funcione de forma estável sob correntes de 50A e barramento de 60V, as seguintes proteções e metodologias foram implementadas no layout:

1. **Rede de Bootstrap Otimizada:** Dimensionada utilizando o pior caso de chaveamento (**6 kHz**). Capacitores cerâmicos SMD de **4.7 µF (50V X7R)** foram selecionados para compensar as correntes quiescentes do driver e a perda de capacitância por efeito de *DC Bias*.

2. **Filtros Snubber RC:** Integrados fisicamente rentes aos drenos e fontes dos MOSFETs IXFN420N10T para mitigar os picos de sobretensão causados pela indutância parasita das trilhas na comutação.

3. **Dimensionamento de Trilhas de Potência:** Áreas de cobre superdimensionadas e estanhadas para suportar a densidade de corrente de 50A sem elevação excessiva de temperatura (calculado via IPC-2152).

## 📂 Estrutura do Repositório

O repositório está organizado para facilitar a replicação, fabricação e auditoria do projeto:

```text
📦 AcionamentoMotorME1906
 ┣ 📂 Hardware
 ┃ ┣ 📜 Esquemático (Arquivos fontes e PDF)
 ┃ ┣ 📜 PCB Layout (Arquivos de design e Gerbers para fabricação)
 ┃ ┣ 📜 BOM_Custos.csv (Lista de Materials e Orçamento do Projeto)
 ┃ ┗ 📜 Modelos 3D (Arquivos STEP para integração mecânica do Shield)
 ┣ 📂 Docs
 ┃ ┣ 📜 Calculos (Bootstrap, Snubber e dimensionamento de trilhas)
 ┃ ┗ 📜 Datasheets (Documentações técnicas do MP1923 e IXFN420N10T)
 ┣ 📂 Software
 ┃ ┗ 📜 Codigos Arduino (Implementação das rotinas de controle e PWM)
 ┗ 📜 README.md