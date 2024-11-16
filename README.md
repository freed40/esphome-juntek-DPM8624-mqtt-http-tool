# ESPHome Juntek DPM8650 MQTT & HTTP Tool

Control your **Juntek DPM8650 50A Buck Converter** using its RS485 interface. This setup integrates seamlessly with **Home Assistant**, **Node-RED**, or a simple web control interface using ESPHome YAML configuration.

---

## Hardware Setup

Wiring for the ESP32 to RS485 connection:

- **TX Pin (ESP)** → **TX Pin (TTL to RS485 Board)**
- **RX Pin (ESP)** → **RX Pin (TTL to RS485 Board)**

### Hardware Diagram

![Hardware Setup](https://github.com/user-attachments/assets/4ec21d7a-58c2-4e0e-ba94-ae161a18d58e)

---

## Software Configuration

To set up your Juntek DPM8650, follow these steps:

1. **Long-press the SET button** on your DPM8650 to enter the configuration menu.
2. Adjust the following settings:

   - **Communication Port (5-CS)**: Set this to `1` to enable RS485 Modbus communication.
     
     ![RS485 Communication Setting](https://github.com/user-attachments/assets/3c7d8b94-be98-4546-a028-9f66a0a23167)

   - **Baud Rate (6-bd)**: Set this to `115.2` for a baud rate of 115200.

     ![Baud Rate Setting](https://github.com/user-attachments/assets/c1d746ba-8af8-44a6-983a-bae01121d99c)

### Wiring Diagram

Ensure the TX and RX pins are connected as described:

<img width="314" alt="Wiring Diagram" src="https://github.com/user-attachments/assets/d9023c15-6558-4439-a2d4-f81ea47c9c6a">

For detailed ESPHome configuration, refer to the [DPM8650 Controller YAML](./dpm8650_controller.YAML).

---

## Interface Options

Depending on your use case, you can enable different interfaces in the ESPHome YAML configuration:

1. **Home Assistant API**:
   - Keep the `api:` block if you're using Home Assistant integration.

2. **MQTT for Node-RED**:
   - Retain the `mqtt:` block if you're using MQTT for integration with Node-RED or other MQTT clients.

3. **Web Interface**:
   - Use the `web_server:` block if you prefer controlling the DPM8650 via a simple web interface.

---

## Home Assistant Integration

Here's a screenshot of how the DPM8650 sensors and controls appear in Home Assistant:

![Home Assistant Screenshot 1](https://github.com/user-attachments/assets/b4653e18-b158-4e96-b338-9c1baadd233c)

![Home Assistant Screenshot 2](https://github.com/user-attachments/assets/e3875b73-5015-4242-b751-a7b257a10a61)

---

## Web Control Interface

You can also control the DPM8650 via a built-in web tool:

![Web Tool Screenshot](https://github.com/user-attachments/assets/ed2d3045-e1a3-45d1-9db0-80c54820f2ea)

---

## MQTT Configuration

### MQTT Text Sensors

- **CCCV Output State Label**  
  State Topic:  
  `dpm8650_controller/sensor/cccv_output_state_label/state`

### MQTT Sensors

- **Max Output Voltage**  
  State Topic:  
  `dpm8650_controller/sensor/max_output_voltage/state`
  
- **Max Output Current**  
  State Topic:  
  `dpm8650_controller/sensor/max_output_current/state`
  
- **Output Voltage**  
  State Topic:  
  `dpm8650_controller/sensor/output_voltage/state`
  
- **Output Current**  
  State Topic:  
  `dpm8650_controller/sensor/output_current/state`
  
- **Temperature**  
  State Topic:  
  `dpm8650_controller/sensor/temperature/state`

### MQTT Numbers

- **Set Max Voltage**  
  State Topic:  
  `dpm8650_controller/number/set_max_voltage/state`
  
- **Set Max Current**  
  State Topic:  
  `dpm8650_controller/number/set_max_current/state`

### MQTT Switches

- **Output Control**  
  - State Topic:  
    `dpm8650_controller/switch/output_control/state`
  - Command Topic:  
    `dpm8650_controller/switch/output_control/command`

### MQTT Binary Sensors

- **CCCV Output State**  
  State Topic:  
  `dpm8650_controller/binary_sensor/cccv_output_state/state`

---
## Resources

[Library](https://github.com/Lotiq/DPM8600)

[Manual](./JT-DPM8600-Manual_2024-05-24.pdf)

[Modbus Protocol](./JT-DPM86XX_Communication_protocol_2023-01-05.pdf)



