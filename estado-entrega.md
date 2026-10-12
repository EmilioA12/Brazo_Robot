---
layout: default
title: Estado de la entrega
nav_order: 6
---

# Estado de la documentación

Revisión del contenido disponible frente al documento **PROYECTO DE INTEGRACIÓN: BRAZO ROBÓTICO DE 3 GDL CON PINZA, CONTROL MANUAL Y CONTROL WiFi**, realizada el 12 de octubre de 2026.

Se documentan dos métodos de fabricación: impresión 3D en PLA y corte láser en MDF de 6 mm. El repositorio contiene geometría CAD y evidencias de piezas fabricadas. La electrónica se presenta como propuesta; los resultados de ensamblaje, programación e integración requieren evidencias adicionales.

## Requisitos y evidencias

| Área | Disponible | Pendiente para completar |
|---|---|---|
| Concepto | Objetivo, equipo y versiones del brazo | Bocetos, alternativas y justificación de selección; precisar objeto de espuma de aproximadamente 7 cm |
| Mecánica | STEP, visor interactivo y descripción de grupos | BOM mecánico, dimensiones, planos por pieza, renders e identificación de articulaciones |
| Fabricación PLA | STL y foto de piezas impresas | Confirmar parámetros reales, configuración, uso de máquina e incidencias |
| Fabricación MDF | Foto de piezas, captura de contornos y DXF de referencia de 3 mm | Archivo utilizado para MDF de 6 mm, planos, parámetros confirmados y evidencias del proceso |
| Ensamblaje | Geometría CAD de referencia | Secuencia, tornillería, fotografías del montaje y pruebas mecánicas de ambas versiones |
| Electrónica | Bloques, BOM preliminar, asignación de pines e imágenes de conexiones y PCB | Esquemático y PCB editables, revisión eléctrica, vistas 3D, Gerbers y perforados |
| Manufactura electrónica | Layout propuesto | Método, PCB fabricada, soldadura, montaje y resultados de pruebas |
| Programación | Descripción del funcionamiento manual previsto | Código usado, arquitectura, diagrama de flujo, librerías, compilación y pruebas |
| WiFi | Selector previsto en el circuito | Access Point, servidor web, SSID/IP, interfaz y pruebas de operación |
| Integración | Objetivo de manipulación | Instalación real, pruebas manuales y WiFi, fotos y videos tomando la pelota |
| Comparación y conclusiones | Dos procesos identificados | Comparación con datos de tiempo, costo, peso, rigidez, montaje y desempeño; conclusiones basadas en pruebas |

La captura de contornos no sustituye el archivo vectorial empleado en la cortadora. De igual manera, las imágenes de la electrónica no sustituyen el proyecto editable, el esquemático completo ni los archivos de fabricación.

## Orden para completar la entrega

1. Incorporar el proyecto electrónico editable y resolver las observaciones de alimentación, entradas ADC y asignación física de pines.
2. Completar planos, BOM mecánico y archivos de fabricación que correspondan a las piezas reales.
3. Documentar PCB, soldadura y pruebas por bloques con mediciones y fotografías.
4. Incorporar el código que efectivamente se cargó al ESP32, con instrucciones reproducibles.
5. Documentar montaje y pruebas del brazo de PLA y del de MDF, incluidos ambos modos de control y la manipulación de una pelota de aproximadamente 7 cm.
6. Comparar los dos brazos y redactar conclusiones apoyadas en sus resultados.

Si se acuerda con los profesores una entrega limitada al control manual, se debe registrar explícitamente ese cambio de alcance. Mientras no exista ese acuerdo, el modo WiFi sigue siendo un requisito del documento proporcionado.

## Registro de resultados

Cada evidencia debe identificar **qué se probó, cómo se probó, cuál fue el resultado y qué se corrigió**. Los valores aún no medidos se mantendrán como pendientes. No se deben presentar parámetros sugeridos como valores registrados en máquina.

[Ver fabricación]({{ '/fabricacion.html' | relative_url }}) · [Ver electrónica]({{ '/electronica.html' | relative_url }})
