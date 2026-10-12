---
layout: default
title: Fabricación
nav_order: 3
---

# Fabricación de las piezas

Se fabricaron piezas para dos versiones del brazo robótico:
una mediante impresión 3D y otra mediante corte láser.

Esta sección reúne las evidencias de fabricación y el registro
de los materiales, equipos y parámetros utilizados.

## Impresión 3D

La fotografía muestra las piezas impresas antes del ensamble.

![Piezas fabricadas mediante impresión 3D]({{ '/assets/images/piezas_impresas.jpeg' | relative_url }})

*Figura 1. Piezas impresas en 3D antes del ensamble.*

### Material y configuración

Los siguientes valores se conservan del registro previo del proyecto.
Su correspondencia con la configuración realmente utilizada debe confirmarse
con el archivo de laminado o las capturas de la máquina.

| Parámetro | Valor utilizado |
|---|---|
| Modelo de impresora | Creality |
| Material | PLA |
| Software de laminado | Ultimaker Cura |
| Altura de capa | 0.20 mm |
| Porcentaje de relleno | 25 % |
| Temperatura de boquilla | 205 °C |
| Temperatura de cama | 60 °C |
| Soportes | Activados en voladizos mayores de 50° |
| Tiempo de impresión | 12 horas aprox |

### Evidencias del proceso

Pendiente de incorporar: capturas de la configuración,
fotografías o videos del uso de la impresora y observaciones
sobre la calidad de las piezas.

## Corte láser

La fotografía muestra las piezas cortadas antes del ensamble.
Se observan paneles con encastres, barras, soportes y elementos
dentados del mecanismo.

![Piezas fabricadas mediante corte láser]({{ '/assets/images/piezas_laser.jpeg' | relative_url }})

*Figura 2. Piezas cortadas en láser antes del ensamble.*

### Distribución de piezas para corte

[![Distribución de los contornos de las piezas del brazo para corte láser]({{ '/assets/images/Corte_laser_brazo.png' | relative_url }})]({{ '/assets/images/Corte_laser_brazo.png' | relative_url }})

*Figura 3. Vista de los contornos de paneles, eslabones, soportes y elementos dentados. Pulsa la imagen para ampliarla.*

La captura permite observar la distribución de las piezas en el plano de corte.
El material reportado para la fabricación es **MDF de 6 mm**. La imagen no
permite comprobar la escala, las cotas ni el ajuste de los encastres; tampoco
sustituye el archivo vectorial utilizado en la máquina.

### Material y configuración

Los parámetros no respaldados por registros de máquina se presentan como
referencias pendientes de confirmar.

| Parámetro | Valor o estado del registro |
|---|---|
| Modelo de cortadora láser | Pendiente de identificar; el registro anterior indicaba «MMM» |
| Material | MDF |
| Espesor de la lámina | 6 mm |
| Software de preparación | LightBurn, según registro previo; confirmar |
| Potencia de corte | 80 %, valor de referencia por confirmar |
| Velocidad de corte y unidades | 12 mm/s = 720 mm/min, valor de referencia por confirmar |
| Número de pasadas | Pendiente de registrar; el texto anterior proponía 1 o 2 según prueba |
| Tiempo de corte | Pendiente de medir; los 20 minutos del registro anterior eran un ejemplo |

### Adaptación del archivo de corte

Se utilizó material de **6 mm de espesor**. El DXF original
estaba identificado para 3 mm y fue modificado en el taller
antes del corte. La versión modificada no está disponible;
el archivo descargable corresponde al diseño de referencia.

### Evidencias del proceso

Pendiente de incorporar: capturas de la configuración,
fotografías o videos del uso de la cortadora y observaciones
sobre la calidad de las piezas.

## Revisión previa al ensamble

Se documentará la comprobación del inventario de piezas,
el ajuste de los encastres y orificios, y cualquier corrección
necesaria antes de armar ambos robots.
