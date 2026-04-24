# 🌱 Controle de Iluminação Inteligente com ESP32

Este projeto tem como objetivo demonstrar a integração entre hardware e software em sistemas embarcados, utilizando o ESP32 para realizar leitura de sensores, processamento de dados e controle de atuadores.

A atividade segue o fluxo fundamental:
👉 Entrada → Processamento → Saída

---

# 🎯 Objetivos da Atividade

- Realizar leitura de entradas analógicas (sensor LDR) e digitais (botão)
- Implementar lógica de conversão e tomada de decisão
- Controlar saídas (LED via PWM e display LCD I2C)
- Utilizar ambiente de simulação (PlatformIO/Wokwi)

---

# 📚 Parte I – Avaliação Teórica

## 1. Resolução e Escalonamento

### a) Valor máximo do analogRead()

- ESP32 (12 bits): **4095**
- Arduino UNO (10 bits): **1023**

Isso ocorre porque:
- 12 bits → 2¹² = 4096 valores (0 a 4095)
- 10 bits → 2¹⁰ = 1024 valores (0 a 1023)

---

### b) Por que usar map() ou proporção?

O valor lido pelo sensor (ADC) está em uma escala diferente da saída PWM.

Exemplo:
- Entrada (ADC ESP32): 0 a 4095  
- Saída PWM: geralmente 0 a 255  

Sem conversão:
👉 Os valores não correspondem corretamente

Por isso usamos:
- `map()` ou cálculo proporcional  
👉 Para ajustar os valores entre diferentes escalas

---

## 2. Comunicação I2C

O protocolo I2C é vantajoso porque:

- Usa apenas **2 fios**:
  - SDA (dados)
  - SCL (clock)

- Permite conectar **vários dispositivos no mesmo barramento**

Vantagens:
- Reduz uso de pinos
- Organização mais simples do circuito
- Fácil expansão (adicionar sensores/display)

---

# ⚙️ Parte II – Projeto Prático

## 💡 Problema

Criar um sistema que monitore a luminosidade e controle automaticamente uma iluminação.

---

## 🔄 Fluxo do Sistema

### 🔹 Entrada (Input)

- Sensor LDR (luminosidade)
- Botão para alternar modo do display

---

### 🔹 Processamento

O sistema realiza:

- Conversão do valor do LDR (0–4095) → (0–100%)
- Verificação da luminosidade:
  - Se < 30% → LED ligado
  - Caso contrário → LED desligado
- Controle de brilho:
  - Quanto mais escuro → maior brilho (PWM)

---

### 🔹 Saída (Output)

- LED:
  - Representa a iluminação automática

- Display LCD I2C:
  - Linha 1 → valor da luminosidade
  - Linha 2 → status:
    - "Ligada"
    - "Desligada"

---

# 🔌 Montagem do Sistema

- ESP32 como controlador
- LDR → GPIO 34 (ADC)
- Botão → entrada digital com `INPUT_PULLUP`
- LCD I2C:
  - SDA → GPIO 21
  - SCL → GPIO 22

---

# 💻 Explicação Básica do Código

O código segue uma estrutura simples e organizada:

### 1. Leitura do Sensor
O ESP32 lê o valor analógico do LDR usando `analogRead()`, obtendo um valor entre 0 e 4095.

---

### 2. Conversão de Valores
Esse valor é convertido para porcentagem (0 a 100%) para facilitar a interpretação da luminosidade.

---

### 3. Lógica de Decisão
O sistema verifica:
- Se a luminosidade é menor que 30%
  - Liga o LED
- Caso contrário
  - Desliga o LED

---

### 4. Controle de Brilho (PWM)
O brilho do LED é ajustado proporcionalmente:
- Mais escuro → LED mais forte
- Mais claro → LED mais fraco ou desligado

---

### 5. Controle do Botão
O botão alterna o modo de exibição:
- Mostrar valor bruto (ADC)
- Mostrar porcentagem (%)

---

### 6. Exibição no LCD
O display mostra:
- Linha 1: valor da luminosidade
- Linha 2: estado da lâmpada

---

# ✅ Critérios Atendidos

✔ Leitura de sensor analógico  
✔ Uso de entrada digital (botão)  
✔ Processamento e tomada de decisão  
✔ Controle de LED com PWM  
✔ Interface com LCD I2C  
✔ Organização do código  

---

# 🚀 Possíveis Melhorias

- Controle automático de irrigação
- Integração com app/web
- Armazenamento de dados
- Uso em agricultura de precisão

---

# 👨‍💻 Autor

Ysmael Sa
