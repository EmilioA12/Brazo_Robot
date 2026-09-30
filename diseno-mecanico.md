---
layout: default
title: Diseño mecánico
nav_order: 2
---

# Diseño mecánico del brazo robótico

## En esta página
{: .no_toc }

1. Contenido
{:toc}

El proyecto utiliza un modelo CAD de referencia de un brazo
robótico con pinza para desarrollar dos versiones físicas:
una mediante impresión 3D y otra mediante corte láser.

El objetivo es obtener un robot de al menos tres grados de
libertad, además del accionamiento de la pinza, y evaluar
su capacidad para tomar un objeto.

## 1. Organización de partes del ensamble

El modelo se organiza en los siguientes grupos:

| Parte | Función |
|---|---|
| Caja y estructura de base | Proporcionar soporte al conjunto y espacio para componentes. |
| Soportes de articulaciones | Alojar componentes y establecer las uniones móviles. |
| Eslabones y barras | Conectar las articulaciones y transmitir movimiento. |
| Pinza | Sujetar y liberar el objeto. |
| Elementos dentados y de transmisión | Transmitir o coordinar movimientos del mecanismo. |
| Servomotores y electrónica | Accionar y controlar el robot. |
| Tornillería y separadores | Unir los componentes y mantener las separaciones necesarias. |

Los componentes comerciales representados en el CAD se
distinguen de las piezas fabricadas por impresión 3D o corte láser.

## 2. Modelo CAD del ensamble

El archivo STEP conserva la geometría del conjunto y sus
componentes. Se utiliza como referencia para inspeccionar
el diseño y preparar vistas, planos e imágenes del robot.

El modelo mostrado corresponde al diseño CAD de referencia.
Las adaptaciones realizadas durante la fabricación se
documentan por separado.

## 3. Visualización 3D interactiva

Arrastra sobre el modelo para girarlo y utiliza la rueda
del ratón para acercarte o alejarte. La carga inicial puede
tardar mientras se procesa el archivo STEP.

<iframe
  src="https://3dviewer.net/embed.html#model=https://raw.githubusercontent.com/EmilioA12/Brazo_Robot/main/assets/cad/brazo-ensamble.step"
  title="Ensamble 3D interactivo del brazo robótico"
  width="100%"
  height="580"
  style="border:1px solid #ddd; border-radius:8px;"
  loading="lazy"
  allowfullscreen>
</iframe>

[Abrir el visor en otra pestaña](https://3dviewer.net/#model=https://raw.githubusercontent.com/EmilioA12/Brazo_Robot/main/assets/cad/brazo-ensamble.step)

Este visor permite inspeccionar la geometría del conjunto;
no representa una simulación de sus movimientos.

## 4. Versión fabricada mediante impresión 3D

Se dispone de un archivo STL con la disposición de piezas
preparada para una cama de impresión de 250 × 250 mm.

La geometría del archivo ocupa aproximadamente
238.5 × 239.7 mm en planta, con una altura máxima de 24 mm.
Estos valores describen el archivo STL; el espacio adicional
para bordes de adhesión u otros ajustes depende del laminado.

[Descargar STL de impresión]({{ '/assets/cad/brazo-impresion.stl' | relative_url }})

## 5. Versión fabricada mediante corte láser

El material utilizado para el corte tuvo un espesor de **6 mm**.

El DXF disponible corresponde al diseño original para 3 mm.
Este archivo fue modificado en el taller antes de la fabricación,
pero no se conserva la versión modificada.

Por ello, el DXF se publica como referencia del diseño original.
Sus encastres y dimensiones deben revisarse antes de reutilizarlo
para fabricar piezas de 6 mm.

[Descargar DXF de referencia para 3 mm]({{ '/assets/cad/brazo-laser-referencia-3mm.dxf' | relative_url }})

## 6. Archivos del proyecto

| Archivo | Uso |
|---|---|
| STEP | Geometría CAD del ensamble de referencia. |
| STL | Disposición de piezas para impresión 3D. |
| DXF | Contornos de corte del diseño original para 3 mm. |

[Descargar ensamble STEP]({{ '/assets/cad/brazo-ensamble.step' | relative_url }})

[Consultar fotografías y registro de fabricación]({{ '/fabricacion.html' | relative_url }})