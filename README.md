# Detector-síntomas-COVID
Dentro de este repositorio encontraremos todo lo necesario para realizar un detector de síntomas COVID con NodeRed, ESP32CAM, el sensor MAX30102 y el sensor MLX90614

# Introducción

*Estamos atravesando por una pandemia la cual nos ha estado obligando a estar monitoreando constantemente nuestros niveles de oxigenación, ritmo cardiaco y temperatura, por lo cual hemos realizado este programa con ayuda de los sensores MAX30102 y MLX90614 para poder  saber si contamos con algún síntoma de COVID y así poder ir al médico a tiempo para ser tratado de dicha enfermedad.*

*El siguiente ejercicio consiste en realizar un detector de síntomas COVID, el cual a través de nuestro microcontrolador ESP32CAM y los sensores de temperatura y ritmo cardíaco manden información a través de WiFi, después los envía por MQTT de forma local a través de un JSON y este JSON es un Flow realizado en NodeRed en dónde encontraremos la interfaz para poder visualizar nuestro ritmo cardiaco, temperatura y oxigenación y a su vez, este se conecta con una base de datos la cual llevará el registro de los pacientes que se han hecho el diagnostico, y tiene la función de poder mandar los resultados arrojados por lo sensores a través de correo electrónico.*

**NOTA: Este flow no nos proporciona un diagnóstico médico, su propósito es realizar una consulta de los signos vitales del paciente, así como su oxigenación y temperatura y comprobar que se encuentren en un rango saludable. Este flow realiza un prediagnóstico, el cual le sugiere al paciente que se realizó el diagnostico a ir al médico para saber cuál es su situación clínica.**

	
## Materiales electrónicos / sensores a utilizar
- [Protoboard](https://articulo.mercadolibre.com.mx/MLM-705443986-protoboard-830-puntos-mb-102-_JM#position=1&search_layout=stack&type=item&tracking_id=da8ad5fa-5d88-41dd-aab2-cd3e65bf6b23)

- [Jumpers macho a macho](https://articulo.mercadolibre.com.mx/MLM-560093984-40-cables-dupont-macho-macho-10-cm-protoboard-pic-arduino-_JM?matt_tool=91188883&matt_word=&matt_source=google&matt_campaign_id=15698047816&matt_ad_group_id=143431914600&matt_match_type=&matt_network=g&matt_device=c&matt_creative=620253690479&matt_keyword=&matt_ad_position=&matt_ad_type=pla&matt_merchant_id=116937574&matt_product_id=MLM560093984&matt_product_partition_id=1638503335377&matt_target_id=pla-1638503335377&gclid=Cj0KCQjwguGYBhDRARIsAHgRm4_UVnUHiSvv3C-Y2R6XGBFkNuszdBsPp4hlbI7Ri8FFMtlxL8IyxSsaAr5IEALw_wcB)

- [Microcontrolador ESP32CAM](https://articulo.mercadolibre.com.mx/MLM-1354031311-esp32-cam-wifi-bluetooth-ch340-micro-usb-hw-297-16-pin-_JM#position=1&search_layout=grid&type=pad&tracking_id=cb2771c1-8ad3-438b-9316-de6117c45b2d#position=1&search_layout=grid&type=pad&tracking_id=cb2771c1-8ad3-438b-9316-de6117c45b2d&is_advertising=true&ad_domain=VQCATCORE_LST&ad_position=1&ad_click_id=OTEyMTI3MWQtYmMyYS00MzZmLTgyOTUtYzQ5NGQ1MzkyOTE2)

- [ Resistencias de 4.7 K Ω](https://articulo.mercadolibre.com.mx/MLM-660627026-200-resistencias-14-w-1-pelicula-metalica-varios-valores-_JM?searchVariation=32042007841#searchVariation=32042007841&position=2&search_layout=stack&type=item&tracking_id=88404fe0-434a-4841-9356-0319120b56fe)

- [Sensor MAX30102 para ritmo cardíaco y saturación de Oxígeno](https://articulo.mercadolibre.com.mx/MLM-1427334301-modulo-sensor-frecuencia-cardiaca-oximetro-max30100-_JM#position=7&search_layout=stack&type=item&tracking_id=363f1404-ba6d-437d-93a8-3d2aea450fd2)

- [Sensor de temperatura MLX90614](https://articulo.mercadolibre.com.mx/MLM-1315023878-sensor-temperatura-termometro-infrarrojo-gy-906-mlx90614-_JM?matt_tool=91188883&matt_word=&matt_source=google&matt_campaign_id=15698047816&matt_ad_group_id=143431914600&matt_match_type=&matt_network=g&matt_device=c&matt_creative=620253690479&matt_keyword=&matt_ad_position=&matt_ad_type=pla&matt_merchant_id=117474830&matt_product_id=MLM1315023878&matt_product_partition_id=1638503335577&matt_target_id=aud-1574484920380:pla-1638503335577&gclid=Cj0KCQjwguGYBhDRARIsAHgRm49jWX4yeWCvwodq2ApHIUFhh7DkZvCfohgEes43ls9l9aTwG0T7hsoaAgEXEALw_wcB)

- [Convertidor FTDI TTL-USB Serial Fy232RL](https://articulo.mercadolibre.com.mx/MLM-660592083-modulo-adaptador-serie-usb-a-serial-ttl-ftdi-ft232rl-33v-5v-_JM#position=2&search_layout=stack&type=pad&tracking_id=3f2ee2da-0338-4f85-ac72-4a20754b51da#position=2&search_layout=stack&type=pad&tracking_id=3f2ee2da-0338-4f85-ac72-4a20754b51da&is_advertising=true&ad_domain=VQCATCORE_LST&ad_position=2&ad_click_id=ZjliZTY3YmMtMzVlNi00NmYwLWFjOWItOWUxYWE0MWNjODQw)

- [Cable USB-A a USB-Mini](https://articulo.mercadolibre.com.mx/MLM-555275297-cable-usb-20-a-macho-a-mini-b-5-pin-18m-calibre-30-_JM#position=4&search_layout=grid&type=item&tracking_id=2cd0f15a-25c8-4abd-b086-a7c2c9f3f2e3)

## Software a Utilizar
- [VirtualBox](https://www.virtualbox.org/)

- [Máquina virtual con sistema operativo Ubuntu, de preferencia la versión 20.04 LTS.](https://releases.ubuntu.com/20.04/)
 
- [IDE de Arduino](https://www.arduino.cc/en/software)
 
- [Configuración de Arduino para poder trabajar con ESP32](https://programarfacil.com/esp8266/programar-esp32-ide-arduino/)
 
- [Mosquitto](https://mosquitto.org/)
 
- [NodeRed](https://nodered.org/)

- [MySQL](https://www.mysql.com/)

## Referencias 

En los enlaces que se muestran a continuación podemos encontrar los cursos de la plataforma **CodigoIoT** correspondientes para poder realizar las configuraciones necesarias:

- [Instalación de Ubuntu 20.04 en VirtualBox Windows](https://edu.codigoiot.com/course/view.php?id=812)

- [Configuración de la IDE de Arduino para el microcontrolador ESP32CAM](https://edu.codigoiot.com/course/view.php?id=850)

- [Instalación de NodeRed en Ubuntu 20.04](https://edu.codigoiot.com/course/view.php?id=817)

- [Introducción a NodeRed](https://edu.codigoiot.com/course/view.php?id=278)

- [Instalación de MQTT](https://edu.codigoiot.com/course/view.php?id=818)

- [Instalación de MySQL](https://edu.codigoiot.com/course/view.php?id=294)

## Instrucciones previas

Para este ejercicio es necesario tomar en cuenta los siguientes puntos:

- Tener configurada la IDE de Arduino para poder cargar los programas al microcontrolador ESP32CAM.
- NodeJS configurado para poder trabajar con NodeRed y tener agregados los nodos Dashboard, MySQL y Mail.
- MQTT Mosquitto configurado. Tendrás que modificar el archivo mosquitto.conf para que acepte conexiones externas y no autentificadas y por último, deberás tener el firewall de Ubuntu abierto para permitir conexiones en el puerto 1883. [En este enlace podrás consultar como poder habilitar el Firewall en Ubuntu](https://www.hostinger.mx/tutoriales/como-configurar-firewall-ubuntu)

## 

## Desarrollo 
Para comenzar, necesitamos desarrollar el programa correspondiente para el microcontrolador y los sensores que tenemos que utilizar.

  [Programa en la IDE de Arduino para el Sensor MAX30102 y el sensor MLX90614 utilizando el Microcontrolador ESP32CAM.](https://github.com/MiguelPM01/Detector-Sintomas-COVID/blob/main/ESP32CAM-MQTT-MLX90614-MAX30102-JSON/ESP32CAM-MQTT-MLX90614-MAX30102/ESP32CAM-MQTT-MLX90614-MAX30102.ino)

