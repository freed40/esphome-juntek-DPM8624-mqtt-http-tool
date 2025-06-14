# ESPHome Juntek DPM8624 MQTT & HTTP Tool

Control your **[Juntek DPM8624 24A Buck Converter](./JT-DPM8624_Datasheet-EN_2024-02-14.pdf)** using its RS485 Modbus interface. This setup integrates seamlessly with **Home Assistant**, **Node-RED**, or a simple web control interface using [ESPHome YAML configuration](./dpm8624_controller.YAML)

**[New: Use your DPM8624 as a powerful MPPT Solar Charge controller](https://github.com/mjpalmowski/esphome-juntek-DPM8624-mqtt-http-tool/blob/main/MPPT-DPM8624-solar-charge-controller)**

# ESP32 MQTT dongle

![Screenshot 2024-11-20 105037](https://github.com/user-attachments/assets/9da001c9-dc4f-4839-ad26-15c840f8210d)


---

## Hardware Setup


### Hardware Diagram


![Screenshot 2024-11-19 125602](https://github.com/user-attachments/assets/147db45e-df32-43c5-aa40-c21b1624f38f)


---

### Wiring Diagram


Wiring for the ESP32 to RS485 connection:

- **TX Pin (ESP)** → **TX Pin (TTL to RS485 Board)**
- **RX Pin (ESP)** → **RX Pin (TTL to RS485 Board)**

Ensure the TX and RX pins are connected as described:

<img width="190" alt="Screenshot 2024-11-19 125220" src="https://github.com/user-attachments/assets/dd39aa32-035a-4258-9c77-b1909ab9c67b">


For detailed ESPHome configuration, refer to the [DPM8624 Controller YAML](./dpm8624_controller.YAML).


## DPM8624 Configuration

To set up your Juntek DPM8624, follow these steps:

1. **Long-press the SET button** on your DPM8624 to enter the configuration menu.
2. Adjust the following settings:

   - **Communication Port (5-CS)**: Set this to `1` to enable RS485 Modbus communication.
     
     ![RS485 Communication Setting](https://github.com/user-attachments/assets/3c7d8b94-be98-4546-a028-9f66a0a23167)

   - **Baud Rate (6-bd)**: Set this to `009.6` for a baud rate of 9600.
  
     ![Screenshot 2024-11-19 125050](https://github.com/user-attachments/assets/3caa70ed-20bc-4912-88d7-e7dbc53f51af)





---

## Interface Options

Depending on your use case, you can enable different interfaces in the [DPM8624 Controller YAML](./dpm8624_controller.YAML).

1. **Home Assistant API**:
   - Keep the `api:` block if you're using Home Assistant integration.

2. **MQTT for Node-RED**:
   - Retain the `mqtt:` block if you're using MQTT for integration with Node-RED or other MQTT clients.

3. **Web Interface**:
   - Use the `web_server:` block if you prefer controlling the DPM8624 via a simple web interface.
  


---

## Home Assistant Integration

Here's a screenshot of how the DPM8624 sensors and controls appear in Home Assistant:

![Home Assistant Screenshot 1](https://github.com/user-attachments/assets/b4653e18-b158-4e96-b338-9c1baadd233c)

![Home Assistant Screenshot 2](https://github.com/user-attachments/assets/e3875b73-5015-4242-b751-a7b257a10a61)

---

## Web Control Interface

You can also control the DPM8624 via a built-in web tool which you can find on your network at http://dpm8624_controller.local/

![Screenshot 2025-01-20 152345](https://github.com/user-attachments/assets/6ed36754-8280-4219-99bd-c5b63c4d871b)



## MQTT Configuration

### MQTT Sensors and Controls

- **MQTT Text Sensor 'CCCV Output State Label'**  
  - State Topic: `dpm8624-controller/sensor/cccv_output_state_label/state`

- **MQTT Sensor 'MAX Output Voltage'**  
  - State Topic: `dpm8624-controller/sensor/max_output_voltage/state`

- **MQTT Sensor 'MAX Output Current'**  
  - State Topic: `dpm8624-controller/sensor/max_output_current/state`

- **MQTT Sensor 'Output Voltage'**  
  - State Topic: `dpm8624-controller/sensor/output_voltage/state`

- **MQTT Sensor 'Output Current'**  
  - State Topic: `dpm8624-controller/sensor/output_current/state`

- **MQTT Sensor 'Temperature'**  
  - State Topic: `dpm8624-controller/sensor/temperature/state`

- **MQTT Number 'Set MAX Voltage'**  
  - State Topic: `dpm8624-controller/number/set_max_voltage/state`

- **MQTT Number 'Set MAX Current'**  
  - State Topic: `dpm8624-controller/number/set_max_current/state`

- **MQTT Switch 'Output Control'**  
  - State Topic: `dpm8624-controller/switch/output_control/state`  
  - Command Topic: `dpm8624-controller/switch/output_control/command`  

  ![Screenshot 2024-11-20 110606](https://github.com/user-attachments/assets/c65462c0-e6ce-4368-a1a1-66056a36dfd6)

  Message payload string `on` to `dpm8624-controller/switch/output_control/command` enables Converter output  

  ![Screenshot 2024-11-20 110631](https://github.com/user-attachments/assets/5a5aa78e-367e-4854-9ecf-8271a99b5652)

  Message payload string `off` to `dpm8624-controller/switch/output_control/command` disables converter output

  

- **MQTT Binary Sensor 'CCCV Output State'**  
  - State Topic: `dpm8624-controller/binary_sensor/cccv_output_state/state`

### MQTT Subscribe Sensors

- **MQTT Subscribe Text Sensor 'MQTT Voltage Command'**  
  - Topic: `home/commands/voltage`  
    (The converter subscribes to this topic. Publish a number (e.g., 12.3) to set the voltage to 12.3V)
- **MQTT Subscribe Text Sensor 'MQTT Current Command'**  
  - Topic: `home/commands/current`  
    (The converter subscribes to this topic. Publish a number (e.g., 12.3) to set the current to 12.3A)
    
  ![Screenshot 2024-11-20 132203](https://github.com/user-attachments/assets/8c17a976-8cc4-436f-bbff-5d378bf162e8)

---
## Resources

[Library](https://github.com/Lotiq/DPM8600)

[Manual](./JT-DPM8600-Manual_2024-05-24.pdf)

[Modbus Protocol](./JT-DPM86XX_Communication_protocol_2023-01-05.pdf)



