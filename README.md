# Remapear-Pinout-FC


### Como cambiar el pad del buzzer/beeper?  
Se puede cambiar el pad del buzzer, pero necesitaremos añadir electronica.  
 
El buzzer necesita una gran cantidad de corriente (mas de la que el procesador STM32 puede proporcionar), es por eso que nuestra placa lleva integrado un transistor. Este transistor es el encargado de asumir la corriente del buzzer y se controla con la señal del procesador. Si soldamos el buzzer a cualquier otro pad de la controladora sin la electronica pertinente podemos quemar la controladora!  

No es recomendable mover este pin, claro esta que puede dañarse y aquí tenemos la alternativa para poder controlar el buzzer desde otro pad.  

<img src="https://oscarliang.com/ctt/uploads/2017/10/buzzer-beeper-flight-controller-transistor-circuit-STM32-processor.jpg">

 Esto es un ejemplo sobre la controladora CC3D, consulta al fabricante de tu placa para obtener este circuito.  
 
### Multiples funciones compartiendo el mismo pin?   

Aveces se comparten diferentes funciones de Betaflight en un mismo pad, si esa no es nuestra intención es mejor liberar ese pin para no sobrecargar la controladora.    

Para mirar que recursos estamos usando, escribir “resource” en el CLI.   
Este es un ejemplo, se puede ver como el pin C08 esta compartido por dos funciones: LED_STRIP y CAMERA_CONTROL.      

<img src="https://oscarliang.com/ctt/uploads/2018/01/fpv-camera-control-fc-flight-controller-resource-led_strip-cli-betaflight-duplicated-pin.jpg ">

Si no usamos el LED Strip, pero si el camera control, podemos dejar el pin C08 libre de LED_STRIP usando el comando en CLI:
  
resource LED_STRIP 1 none  

### Te faltan Serial Ports o UARTS?    
Si te faltan serial ports o UARTS, puedes convertir algunos pats a serial port, con la opción Soft Serial.    

Por ejemplo, puedes usar los puertos de LED_STRIP, PPM y Motores que no uses.    

### Que pads no pueden ser remapeados?  

Los pads de Voltage (5V,battery voltage, 3.3v...) y GND (tierra) no pueden ser remapeados, ya que son conexiones fisicas que no pasan por el procesador.  

La entrada de camara y salida de video (para Betaflight OSD) no pueden ser remapeadas ya que estas van al chip OSD, y no al procesador principal.  

[Oscar Liang] https://oscarliang.com/betaflight-resource-remapping/

[Oscar Liang] https://oscarliang.com/fpv-camera-control-fc/

[Oscar Liang] https://oscarliang.com/betaflight-soft-serial/
