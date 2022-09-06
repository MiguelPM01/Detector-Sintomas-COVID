# Detector-Sintomas-COVID
Dentro de este repositorio encontraremos todo lo necesario para realizar un detector de síntomas COVID con NodeRed, ESP32CAM, el sensor MAX30102 y el sensor MLX90614

# Introducción

*Estamos atravesando por una pandemia la cual nos ha estado obligando a estar monitoreando constantemente nuestros niveles de oxigenación, ritmo cardiaco y temperatura, por lo cual hemos realizado este programa con ayuda de los sensores MAX30102 y  MLX90614 para poder  saber si contamos con algún síntoma de COVID y así poder ir al médico a tiempo para ser tratado de dicha enfermedad.*


	
## Materiales electrónicos / sensores a utilizar
- Protoboard.

- Jumpers.

- Microcontrolador ESP32CAM.

- 2 Resistencias de 4.7 K Ω.

- Sensor MAX30102 para ritmo cardíaco y saturación de Oxígeno.

- Sensor de temperatura MLX90614.

- Convertidor FTDI TTL-USB Serial Fy232RL.

- Cable micro USB a USB.

## Software a Utilizar
- Máquina virtual con sistema operativo Ubuntu, de preferencia la versión 20.04 LTS.
 
- IDE de Arduino para Ubuntu.
 
- Bibliotecas para los sensores MLX90614, MAX30102 y para el microcontrolador ESP32CAM.
 
- Mosquitto.
 
- NodeRed.

- MySQL para Ubuntu.

## Desarrollo 
Para comenzar, necesitamos desarrollar el programa correspondiente para el microcontrolador y los senosres que tenemos que utilizar.

  [Programa en la IDE de Arduino para el Sensor MAX30102 y el sensor MLX90614 utilizando el Microcontrolador ESP32CAM.](https://github.com/MiguelPM01/Detector-Sintomas-COVID/blob/main/ESP32CAM-MQTT-MLX90614-MAX30102-JSON/ESP32CAM-MQTT-MLX90614-MAX30102/ESP32CAM-MQTT-MLX90614-MAX30102.ino)
