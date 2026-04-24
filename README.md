# MONITORAMENTO COM ESP32
Esta atividade visa avaliar a capacidade de integração de componentes de hardware e o
desenvolvimento de lógica de programação para sistemas embarcados, focando no fluxo
fundamental: Entrada, Processamento e Saída.

1. Objetivos da Atividade
· Demonstrar domínio sobre leitura de entradas analógicas (sensores) e digitais
(interrupções/botões).
· Implementar lógica de processamento para conversão de grandezas e controle de
estados.
· Validar o uso de saídas de dados via atuadores (LED/PWM) e interface visual
(LCD I2C).
· Utilizar o ambiente de desenvolvimento (VSCode/PlatformIO ou Wokwi) para
simulação e depuração.

# 📚 Parte I – Avaliação Teórica

## 1. Resolução e Escalonamento

### a) Valor máximo do analogRead()

- ESP32 (12 bits): **4095**
- Arduino UNO (10 bits): **1023**

---

### b) Por que usar map() ou proporção?

O valor do sensor (0–4095) não está na mesma escala que outras saídas.

Por isso é necessário converter os valores para:
- porcentagem (0–100%)
- ou escala PWM

Isso garante interpretação correta dos dados.

---

## 2. Comunicação I2C

O protocolo I2C utiliza apenas dois pinos:

- SDA (dados)
- SCL (clock)

Vantagens:
- Menos fios
- Permite vários dispositivos no mesmo barramento
- Facilita a expansão do sistema

---

# ⚙️ Parte II – Projeto Prático

## 💡 Funcionamento do Sistema

O sistema realiza:

### 🔹 Entrada
- Sensor LDR (leitura analógica)
- Botão (controle do modo de exibição)

---

### 🔹 Processamento

- Leitura do valor do sensor (0–4095)
- Conversão para porcentagem:
  
  ```cpp
  percentage = 100 - (sensorValue / 4095.0) * 100.0;
# 👨‍💻 Autor

Ysmael Sa
