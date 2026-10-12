---
layout: default
title: Electrónica
nav_order: 4
---

# Electrónica y control del brazo

## En esta página
{: .no_toc }

1. Contenido
{:toc}

El sistema propuesto utiliza un **ESP32-C3 SuperMini** para controlar cuatro actuadores por brazo: base (M1), hombro (M2), codo (M3) y pinza. Los tres primeros corresponden a los tres grados de libertad del brazo; la pinza tiene un accionamiento adicional.

Esta sección documenta la propuesta de conexiones y PCB. La fabricación, soldadura y validación electrónica se registrarán con las evidencias del montaje real. Las imágenes disponibles no acreditan todavía el funcionamiento del circuito.

## 1. Alcance del sistema

Cada brazo necesita **tres servos MG996R y un MG90S**, según las etiquetas de la propuesta. Se debe comprobar que los servos adquiridos coincidan con estos modelos y con sus alojamientos mecánicos.

La propuesta incluye dos grupos de conectores: uno para el brazo de MDF y otro para el de PLA. Por tanto, admite **ocho servos físicos con cuatro señales compartidas**. Cada pareja de servos recibe la misma orden; no permite controlar ambos brazos de forma independiente. Compartir la señal tampoco garantiza que los dos mecanismos alcancen exactamente el mismo ángulo.

Para ensayar un solo brazo se conecta únicamente su grupo de cuatro servos. Si se conectan ambos, se deben comprobar el sentido de giro, los topes y el intervalo de movimiento común de cada pareja antes de operar simultáneamente.

Las instrucciones del proyecto requieren control **Manual/WiFi**, un LED y un botón de prueba. El modo manual se plantea con cuatro potenciómetros. El funcionamiento WiFi, la interfaz web y su programación quedan pendientes de evidencia; disponer del selector no demuestra que esas funciones estén implementadas.

## 2. Diagrama de bloques

![Arquitectura propuesta de entradas, controlador, alimentación y actuadores]({{ '/assets/images/bloques-electronica.svg' | relative_url }})

*Figura 1. Arquitectura electrónica propuesta. Los dos grupos de servos comparten las cuatro órdenes. El enlace WiFi forma parte del requisito por implementar y verificar.*

La fuente alimenta la etapa de servos a 5 V. La placa ESP32 recibe alimentación por una rama para lógica compatible con su entrada de 5 V; la salida regulada de 3.3 V se utiliza para los potenciómetros. Todas las ramas comparten GND. La corriente de los motores no debe circular a través del regulador del ESP32.

## 3. Lista de componentes

La cantidad para dos brazos supone una tarjeta y cuatro potenciómetros compartidos, como en las imágenes. **Proveedores y costos quedan por registrar con las compras reales.** Las dimensiones y los encapsulados se deben contrastar con los componentes y las huellas del proyecto editable.

| Componente o valor | Función | Un brazo | Dos brazos | Presentación prevista |
|---|---|---:|---:|---|
| ESP32-C3 SuperMini | Lectura de entradas y generación de señales | 1 | 1 | Módulo con dos hileras de pines |
| MG996R | M1, M2 y M3 | 3 | 6 | Servo con cable de tres conductores |
| MG90S | Apertura y cierre de la pinza | 1 | 2 | Microservo con cable de tres conductores |
| Potenciómetro lineal de 10 kΩ | Consigna manual de cada actuador | 4 | 4 | Tres terminales; montaje por confirmar |
| Selector Manual/WiFi | Selección del modo | 1 | 1 | Interruptor externo; tipo por confirmar |
| Pulsador normalmente abierto | Entrada de prueba | 1 | 1 | Dos contactos eléctricos |
| LED y resistencia de 330 Ω | Indicador de prueba | 1 + 1 | 1 + 1 | Montaje de orificio pasante |
| Capacitor C1, 220 µF / 10 V | Apoyo al filtrado de la rama de lógica | 1 | 1 | Electrolítico radial, según captura de PCB |
| Capacitor C2, 2200 µF | Apoyo al filtrado de la rama de servos | 1 | 1 | Electrolítico radial; se propone tensión nominal ≥10 V |
| Conector para servo | GND, +5 V y señal | 4 | 8 | Tres pines; comprobar orden y paso |
| Conector para potenciómetro | Señal, 3.3 V y GND | 4 | 4 | Tres pines; comprobar orden y paso |
| Entradas J1 y J17 | Alimentación de lógica y servos | 2 | 2 | Dos contactos por entrada, según PCB |
| Fuente regulada de 5 V | Alimentación del sistema | 1 | 1 | Fuente de laboratorio; corriente por dimensionar |
| PCB, zócalos y cableado | Montaje e interconexión | 1 juego | 1 juego | Definir calibre y capacidad de corriente |

El dibujo de conexiones indica una fuente de 5 V y 10 A para dos brazos. Ese valor se conserva como **propuesta inicial**, no como capacidad validada. La fuente, los conectores y las pistas deben dimensionarse con las corrientes de los servos reales y el escenario de movimiento simultáneo.

## 4. Propuesta de conexiones

[![Propuesta de cableado con ESP32-C3 SuperMini, potenciómetros y dos grupos de servos]({{ '/assets/images/electronica_brazo.jpeg' | relative_url }})]({{ '/assets/images/electronica_brazo.jpeg' | relative_url }})

*Figura 2. Diagrama ilustrativo de conexiones proporcionado para el proyecto. Pulsa la imagen para verla a tamaño completo. El esquemático eléctrico editable queda pendiente de incorporar.*

### Asignación de pines

| Elemento | GPIO propuesto | Tipo | Función |
|---|---:|---|---|
| Potenciómetro M1 | 0 | ADC1_CH0 | Consigna de base |
| Potenciómetro M2 | 1 | ADC1_CH1 | Consigna de hombro |
| Potenciómetro M3 | 3 | ADC1_CH3 | Consigna de codo |
| Potenciómetro de pinza | 4 | ADC1_CH4 | Consigna de apertura |
| Servo M1 | 5 | Salida de pulsos | Base de MDF y/o PLA |
| Servo M2 | 6 | Salida de pulsos | Hombro de MDF y/o PLA |
| Servo M3 | 7 | Salida de pulsos | Codo de MDF y/o PLA |
| Servo de pinza | 10 | Salida de pulsos | Pinza de MDF y/o PLA |
| Selector Manual/WiFi | 8 | Entrada digital | Selección de modo |
| LED con 330 Ω | 20 | Salida digital | Indicación de prueba |
| Botón de prueba | 21 | Entrada digital | Orden de prueba |

La asignación de entradas ADC coincide con la [documentación GPIO de Espressif](https://docs.espressif.com/projects/esp-idf/en/stable/esp32c3/api-reference/peripherals/gpio.html). Los números de GPIO no son números de posición física del conector: se debe comprobar el pinout de la placa SuperMini utilizada.

### Entradas y señales

Los extremos de cada potenciómetro se conectan a 3.3 V y GND; el cursor se dirige a la entrada analógica correspondiente. **No conectar los potenciómetros a 5 V.** El firmware deberá filtrar las lecturas y convertirlas a una consigna limitada por los topes mecánicos de cada articulación.

Alimentar el potenciómetro a 3.3 V no implica que el ADC mida linealmente todo ese recorrido: la [documentación del ADC para ESP32-C3](https://docs.espressif.com/projects/arduino-esp32/en/latest/api/adc.html) indica un rango de hasta aproximadamente 2.5 V con la atenuación máxima documentada. Antes de cerrar el diseño se debe resolver el acondicionamiento de entrada para aprovechar todo el recorrido sin saturación; esta corrección aún no está incorporada a las imágenes.

Las entradas del botón y selector requieren un estado definido mediante resistencias de polarización o la configuración apropiada del microcontrolador. GPIO8 es un pin de configuración de arranque; hay que revisar su circuito en la placa utilizada y probar encendido y carga de programa con el selector en ambas posiciones. GPIO20 y GPIO21 también pueden tener funciones UART, por lo que el firmware debe evitar conflictos con el LED y el botón.

Cada servo recibe alimentación y GND desde la rama de potencia, y la orden desde el GPIO asignado. Se debe verificar la compatibilidad de la entrada del servo con señales lógicas de 3.3 V; el intervalo de pulsos y los límites de movimiento se calibrarán con los modelos reales.

## 5. Alimentación

La propuesta utiliza una fuente regulada a **5 V**. Con esa alimentación no se plantea un elevador de tensión. Cualquier cambio de fuente exige revisar la tensión admisible de servos, placa y capacitores.

La captura de PCB identifica **J1 para lógica y J17 para servos**. Deben recibir las ramas correspondientes de la misma fuente, con GND común. La alimentación de potencia se distribuye mediante conductores y conexiones adecuados a la corriente prevista, sin usar los rieles de una protoboard como distribución de alta corriente.

Los capacitores se conectan respetando su polaridad. La anotación «2200 µF (5 V)» del dibujo se interpreta como la tensión del bus; se propone un capacitor con tensión nominal de al menos 10 V. Los capacitores ayudan con transitorios, pero no sustituyen una fuente ni un cableado correctamente dimensionados.

Durante programación por USB debe verificarse el circuito de alimentación de la SuperMini concreta antes de conectar también 5 V externos a la placa, para evitar realimentación entre fuentes.

## 6. Diseño de PCB

[![Layout propuesto de PCB para dos brazos y ocho conectores de servo]({{ '/assets/images/PCB_brazo.png' | relative_url }})]({{ '/assets/images/PCB_brazo.png' | relative_url }})

*Figura 3. Captura del layout propuesto. Se observan pistas en B.Cu, el módulo central, entradas de potenciómetros y dos grupos de conectores de servo. Pulsa para ampliar.*

La distribución agrupa los conectores de actuadores a la izquierda y los de potenciómetros a la derecha. También incluye entradas de alimentación, capacitores, selector, LED y pulsador. La captura anota pistas de 0.8 mm y refuerzo del bus de servos.

**La captura no permite certificar continuidad, separación de redes ni capacidad de corriente.** No se considera una PCB validada para fabricar hasta revisar el proyecto editable y las reglas eléctricas y de diseño.

### Revisión antes de fabricación

1. Comprobar huella, orientación y pinout de la SuperMini, incluyendo USB y zona de antena.
2. Verificar conexiones GND, +5 V, 3.3 V y señales contra el esquemático; comprobar el orden de cada conector.
3. Dimensionar pistas, distribución de potencia y retornos con corriente, longitud, espesor de cobre y calentamiento admisible. La nota de 0.8 mm no acredita capacidad para todos los servos.
4. Resolver el acondicionamiento ADC y comprobar el uso de GPIO8 con la placa real.
5. Ejecutar ERC y DRC, y revisar cada incidencia antes de generar fabricación.
6. Exportar vistas superior, inferior y 3D, Gerbers y perforados; comprobar escala, orientación, taladros y contorno.

### Archivos disponibles y pendientes

| Entregable | Estado |
|---|---|
| Diagrama de bloques | Disponible en esta página |
| Ilustración de conexiones | Disponible como JPEG |
| Captura del layout | Disponible como PNG |
| Proyecto y esquemático editables | Pendientes de incorporar |
| PCB editable y comprobaciones ERC/DRC | Pendientes de incorporar |
| Vistas superior, inferior y 3D | Pendientes de exportar desde el proyecto |
| Gerbers y archivos de perforado | Pendientes de incorporar |

## 7. Manufactura y soldadura

El método de fabricación de la PCB y su montaje aún no están documentados. Esta sección se completará con fotografías de la tarjeta sin componentes, colocación y soldadura, conectores, tarjeta terminada y correcciones realizadas. Se registrarán el método o proveedor y los archivos realmente empleados.

## 8. Pruebas electrónicas por realizar

Las siguientes pruebas constituyen el plan de validación. **No se han registrado resultados medidos en esta documentación.**

| Prueba | Procedimiento | Criterio de aceptación | Resultado |
|---|---|---|---|
| Inspección y continuidad | Sin alimentación, revisar polaridades, conectores y redes con multímetro | Conexiones acordes con el esquemático y sin cortocircuitos no previstos | Pendiente |
| Alimentación de lógica | Encender sin servos y medir 5 V y 3.3 V | Valores compatibles con los componentes y arranque estable | Pendiente |
| Potenciómetros | Registrar lectura ADC durante todo el giro de cada mando | Cambio progresivo, sin saturación prematura ni saltos que impidan el control | Pendiente |
| LED, botón y selector | Verificar los estados y arrancar en ambas posiciones del selector | Lectura estable y arranque/carga de programa correctos | Pendiente |
| Un servo por vez | Ensayar primero sin carga mecánica y limitar el recorrido | Respuesta al mando y sentido de giro identificados | Pendiente |
| Cuatro servos | Conectar un brazo y mover sus articulaciones dentro de límites calibrados | Sin interferencias, reinicios ni caída de tensión fuera de especificación | Pendiente |
| Dos brazos, si se utilizan juntos | Comprobar cada pareja y después el conjunto; medir corriente y tensión | Recorridos compatibles, alimentación estable y conexiones sin calentamiento excesivo | Pendiente |

Para cada prueba se registrarán fecha, tensión, corriente cuando corresponda, observaciones, correcciones y fotografía o video. La sujeción de la pelota se evalúa posteriormente en la integración mecánica, electrónica y de programación.

## 9. Programación e integración

El flujo previsto para modo manual es: lectura de potenciómetros, filtrado, conversión a consignas, aplicación de límites y actualización de señales de los servos. Esto describe la propuesta funcional, no un programa ya validado.

Para completar el requisito WiFi se deberán incorporar el código fuente probado, dependencias, configuración de compilación, SSID, dirección IP real y capturas de la interfaz web. También faltan evidencias de pruebas manuales, WiFi y manipulación de la pelota en ambas versiones.

[Consultar el estado de la entrega]({{ '/estado-entrega.html' | relative_url }})
