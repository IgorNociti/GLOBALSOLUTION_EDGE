# # 🌧️ EcoDrain – Monitoramento de Enchentes com ESP32, MQTT e Node-RED

🚨 **Objetivo do projeto:**  
Desenvolver um sistema de monitoramento de nível de água em bueiros, utilizando sensor ultrassônico, ESP32, display OLED e integração com um painel em tempo real via Node-RED. A ideia é alertar autoridades locais sobre risco iminente de alagamentos com baixo custo e alta eficiência.

---


🧪 Painel Node-RED:https://drive.google.com/drive/folders/1GOkpV-33ZXekA3O7tJLNFHMLFLYWxCFI?usp=sharing

Video no youtube:https://youtu.be/XC5XnSmtkuk

🔌 Simulação Wokwi:https://wokwi.com/projects/432220782107151361

## 👨‍💻 Integrantes

- **Henrique Maciel Rodrigues** – RM559628  
- **Igor Pereira Nociti** – RM560225
- **Pedro Paulo Sabino** – RM559578
- **Sala:** 1ESPS

---

## 🧠 Tecnologias Utilizadas

- **ESP32**  
- **Sensor Ultrassônico HC-SR04**  
- **Display OLED I2C (SSD1306)**  
- **LED de Alerta Vermelho**  
- **MQTT (broker.hivemq.com)**  
- **Node-RED com node-red-dashboard**  
- **Wokwi (para simulação)**

---



## 📶 Como Funciona

1. O **ESP32** mede continuamente a distância entre o sensor e o nível da água.
2. A leitura é convertida em porcentagem (%) do nível.
3. Os dados são enviados via **MQTT** para o tópico `sensor/bueiro/nivel`.
4. O painel **Node-RED Dashboard** recebe e exibe o nível:
   - Gauge (medidor circular)
   - Botões para ativar/desativar alarme remotamente via MQTT
5. Se o botão **Ativar Alarme** for pressionado, uma mensagem `ALARMAR` é enviada ao tópico `bueiro/controle`, acendendo o LED vermelho do ESP32.

---

## 🧪 Fluxo de Dados

[ Sensor Ultrassônico ]
↓
[ ESP32 calcula % ]
↓
[ MQTT Publish: sensor/bueiro/nivel ]
↓
[ Node-RED Dashboard (gauge, alertas) ]
↑
[ MQTT Control: bueiro/controle ← botão ]

markdown
Copiar
Editar

---

## 🌐 Como Rodar

### 🧩 Requisitos

- Node-RED instalado (`npm install -g node-red`)
- MQTT Broker público (ex: `broker.hivemq.com`)
- Biblioteca `node-red-dashboard` instalada
- Arduino IDE com biblioteca do OLED e WiFi + PubSubClient

### 🚀 Passos

1. **Suba o código no ESP32**
2. **Rode o Node-RED**
   ```bash
   node-red
Importe o fluxo do Node-RED fornecido (via JSON)

Abra o Dashboard:

bash
Copiar
Editar
📸 Demonstração Visual


⚙️ Exemplo de Tópicos MQTT
📤 sensor/bueiro/nivel → "Nível de água: 34%"

📥 bueiro/controle → "ALARMAR" ou "DESALARMAR"

📊 Possíveis Melhorias
Notificações por Telegram/WhatsApp

Integração com bancos de dados (InfluxDB/Grafana)

Geolocalização e mapa com vários sensores

Alimentação via energia solar + bateria

🏁 Conclusão
Esse projeto demonstra como soluções IoT acessíveis podem ser aplicadas para prevenção de desastres em áreas urbanas. Ele une sensores, microcontroladores e visualização de dados em tempo real com o Node-RED. 🌍💡
