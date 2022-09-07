# Detector-Sintomas-COVID
Dentro de este repositorio encontraremos todo lo necesario para realizar un detector de síntomas COVID con NodeRed, ESP32CAM, el sensor MAX30102 y el sensor MLX90614

# Introducción

*Estamos atravesando por una pandemia la cual nos ha estado obligando a estar monitoreando constantemente nuestros niveles de oxigenación, ritmo cardiaco y temperatura, por lo cual hemos realizado este programa con ayuda de los sensores MAX30102 y  MLX90614 para poder  saber si contamos con algún síntoma de COVID y así poder ir al médico a tiempo para ser tratado de dicha enfermedad.*

*El siguiente ejercicio consiste en realizar un detector de Sintomas COVID, el cual a través de nuestro microcontrolador ESP32CAM y los sensores de temperatura y ritmo cardíaco manden información a través de WiFi, después los envia por MQTT de forma local a través de un JSON y este JSON es un Flow realizado en NodeRed en dónde encontraremos la interfaz para poder visualizar nuestro ritmo cardiaco, temperatura y oxigenación y a su vez, este se conecta con una base de datos la cual llevará el registro de los pacientes que se han hecho el diagnostico, y tiene la función de poder mandar los resultados arrojados por lo sensores a través de correo electrónico.*

**NOTA:Este flow no nos proporciona  un diagnostico médico, su propósito es realizar una consulta de los signos vitales del paciente, así como su oxigenación y temperatura y comprobar que se encuentren en un rango saludable. Este flow realiza un diagnostico, el cual le sugiere  al paciente que se realizó el diagnostico a ir al médico para saber cual es su situación clinica.**

	
## Materiales electrónicos / sensores a utilizar
- Protoboard.

- Jumpers macho a macho.

- Microcontrolador ESP32CAM.

- 2 Resistencias de 4.7 K Ω.

- Sensor MAX30102 para ritmo cardíaco y saturación de Oxígeno.

- Sensor de temperatura MLX90614.

- Convertidor FTDI TTL-USB Serial Fy232RL.

- Cable USB-A a USB-Mini.

## Software a Utilizar
- [Máquina virtual con sistema operativo Ubuntu, de preferencia la versión 20.04 LTS.](https://releases.ubuntu.com/20.04/)
 
- IDE de Arduino para Ubuntu.
 
- Bibliotecas para los sensores MLX90614, MAX30102 y para el microcontrolador ESP32CAM.
 
- Mosquitto.
 
- NodeRed.

- MySQL para Ubuntu.

## Desarrollo 
Para comenzar, necesitamos desarrollar el programa correspondiente para el microcontrolador y los senosres que tenemos que utilizar.

  [Programa en la IDE de Arduino para el Sensor MAX30102 y el sensor MLX90614 utilizando el Microcontrolador ESP32CAM.](https://github.com/MiguelPM01/Detector-Sintomas-COVID/blob/main/ESP32CAM-MQTT-MLX90614-MAX30102-JSON/ESP32CAM-MQTT-MLX90614-MAX30102/ESP32CAM-MQTT-MLX90614-MAX30102.ino)
