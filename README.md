# esphome-juntek-DPM8650-mqtt-http-tool
 Control your JUNTEK 50A Buck converter using its RS585 interface. Homeasistant/NodeRed/Web Control  ESPHome YAML Config






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
