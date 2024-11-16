# esphome-juntek-DPM8650-mqtt-http-tool
 Control your JUNTEK 50A Buck converter using its RS485 interface. Homeasistant/NodeRed/Web Control  ESPHome YAML Config

# Hardware Setup:

![Hardware Setup](https://github.com/user-attachments/assets/4ec21d7a-58c2-4e0e-ba94-ae161a18d58e)


# Software Setup:
Long-press SET button the DPM8650 and make sure that:

Inverter setup:
"5-CS" is set to "__1__"  (sets the communication port to RS485 modbus)

![Screenshot 2024-11-16 140530](https://github.com/user-attachments/assets/3c7d8b94-be98-4546-a028-9f66a0a23167)

"6-bd" is set to "115.2"  (sets the baudrate to 115200)

![Screenshot 2024-11-16 140551](https://github.com/user-attachments/assets/c1d746ba-8af8-44a6-983a-bae01121d99c)

Make sure the TX pin defined in YAML is connected to TX pin of the TTL to RS485 board, same for the RX pin. 

<img width="314" alt="Screenshot 2024-11-16 135528" src="https://github.com/user-attachments/assets/d9023c15-6558-4439-a2d4-f81ea47c9c6a">

see [View DPM8650 Controller YAML](./dpm8650_controller.YAML)

## Interface: 
1) If you use Homeassistant keep the api: block


2) if you use MQTT/NodeRed keep the mqtt: block


3)  If you just need the web interface keep the web_server: block


# Home Assistant Screen Shot:

![Screenshot 2024-11-16 131035](https://github.com/user-attachments/assets/b4653e18-b158-4e96-b338-9c1baadd233c)

![Screenshot 2024-11-16 131049](https://github.com/user-attachments/assets/e3875b73-5015-4242-b751-a7b257a10a61)




# Web-Tool Screen Shot:

![Screenshot 2024-11-16 122421](https://github.com/user-attachments/assets/ed2d3045-e1a3-45d1-9db0-80c54820f2ea)


# MQTT:

## MQTT Text Sensors
- **CCCV Output State Label**  
  State Topic: `dpm8650_controller/sensor/cccv_output_state_label/state`

## MQTT Sensors
- **MAX Output Voltage**  
  State Topic: `dpm8650_controller/sensor/max_output_voltage/state`
- **MAX Output Current**  
  State Topic: `dpm8650_controller/sensor/max_output_current/state`
- **Output Voltage**  
  State Topic: `dpm8650_controller/sensor/output_voltage/state`
- **Output Current**  
  State Topic: `dpm8650_controller/sensor/output_current/state`
- **Temperature**  
  State Topic: `dpm8650_controller/sensor/temperature/state`

## MQTT Numbers
- **Set MAX Voltage**  
  State Topic: `dpm8650_controller/number/set_max_voltage/state`
- **Set MAX Current**  
  State Topic: `dpm8650_controller/number/set_max_current/state`

## MQTT Switches
- **Output Control**  
  State Topic: `dpm8650_controller/switch/output_control/state`  
  Command Topic: `dpm8650_controller/switch/output_control/command`

## MQTT Binary Sensors
- **CCCV Output State**  
  State Topic: `dpm8650_controller/binary_sensor/cccv_output_state/state`
