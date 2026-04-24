# 🌱 Controle de Iluminação Inteligente com ESP32

Este projeto implementa um sistema embarcado utilizando o ESP32 para monitorar a luminosidade ambiente e controlar automaticamente um LED, além de exibir informações em um display LCD I2C.

O sistema segue o fluxo:
👉 Entrada → Processamento → Saída

---

# 🎯 Objetivos da Atividade

- Leitura de sensor analógico (LDR)
- Uso de entrada digital (botão)
- Processamento de dados (conversão para %)
- Controle de saída (LED)
- Exibição de dados em LCD I2C

---

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
