# Practica_10
## Integrantes:  
- Francisco Javier Godinez Lopez
- Pablo Axel Silva Fuentes
- Eduardo David Salas Ayala
- 
## Introducción:  

El objetivo principal de esta práctica es replicar un dibujo a partir de una imagen, empleando un brazo robótico Epson equipado con un plumón para trazar sobre un pizarrón. Para lograrlo, el sistema utiliza un enfoque basado en puntos, en el cual el robot está configurado para realizar trazos precisos que conforman la ilustración. Esta tarea se complementa con el uso de MATLAB, una herramienta  para procesar la imagen original. MATLAB permite extraer los puntos clave del dibujo, ajustar su tamaño según los requerimientos y generar una matriz que sirve como base para las instrucciones enviadas al robot.

## Instrucciones

El robot debe realizar el dibujo.

1. Seleccionar una imagen con un tamaño pequeño en la resolucion para su rapido dibujo.
2. Ser porcesada por medio de matlab, utilizando el comando proporcionado por el profesor.
3. Obtener los valores para la matriz y puntos que se dibujaran.
4. Emplementar un codigo en Epson+ para realizar el dibujo y cargar los datos obtenidos por matlab.
5. Fijar el punto de inicio del robot para el dibujo.
6. Ejecutar la programacion para realizar la tarea asignada.

De tal manera que el codigo desarrollado en el Epson+ quedo de la siguiente manera:

```
Function main
Speed 30
Accel 30, 30
SpeedS 60
AccelS 6000, 6000

String linea$, xt$, yt$
Integer x, y, largo, archivo, espacio, i
Boolean fin

fin = 1
 i = 1

archivo = FreeFile
ROpen "datos.txt" As #archivo

Do While fin
  Input #archivo, linea$
  largo = Len(linea$)
  espacio = InStr(linea$, " ")
  yt$ = Mid$(linea$, 1, espacio - 1)
  xt$ = Mid$(linea$, espacio + 1, largo - espacio)
  x = Val(xt$)
  y = Val(yt$)

Print "columna =", x, " renglón = ", y
Go inicio +X(x * 2) -Y(y * 2)
 i = i + 1
Move Here -Z(20)
Move Here +Z(20)

  fin = Eof(archivo) + 1
Loop
Close #archivo
Fend
```

El codigo implementado en Matlab fue el siguiente:

```
clc 
clear all
close all
color = imread("mondongo.jpg");
imshow(color)

gris = rgb2gray(color);
figure;
imshow(gris)

blancoynegro = imbinarize(gris, 'adaptive', 'Sensitivity',0.8)
figure;
imshow(blancoynegro)

nblancoynegro = not(blancoynegro)
figure
imshow(not (nblancoynegro))
                
sblancoynegro = sparse (nblancoynegro)
```

En el video acontinuacion se muestra un poco del procedimineto para la realziacion del dibujo: (se aclara que no se grabo todo por la duracion de realizar por completo el dibujo.)





https://github.com/user-attachments/assets/bb94244d-0063-4dca-938b-c6c3ea28f952


Acontinuación se muestra la comparación del dibujo procesador por matlab y el obtenido:


![mondongoinstalar](https://github.com/user-attachments/assets/7a8ccd45-d0f7-4742-b1ec-c2e966d6770e)

![WhatsApp Image 2024-11-28 at 10 02 10 AM](https://github.com/user-attachments/assets/d59523e9-099f-43c0-9fec-3be884feb370)


El dibujo no fue realizado a la perfección, debido a que el pizarron ya se encontraba con superficies irregulares, por lo que, fue imposible llevar acabo el dibujo correctamente.

## Conclusiones:  
### Francisco Javier Godinez Lopez:
La práctica demostro el valor del brazo robótico Epson como una herramienta versátil y adaptable en tareas que requieren precisión y automatización. La interacción con MATLAB permitió procesar y manipular datos de una imagen, traduciéndolos en movimientos exactos del robot para replicar el dibujo. Más allá del éxito obtenido en esta tarea específica, este ejercicio destaca el enorme potencial del robot para abordar actividades mucho más complejas, como la programación de trayectorias dinámicas o el manejo de materiales en procesos industriales. Esta práctica no solo consolidó conocimientos técnicos, sino que también planteó nuevas posibilidades de exploración para futuras aplicaciones que combinen procesamiento digital y control robótico avanzado.


### Pablo Axel Silva Fuentes: 
La práctica permitió comprobar cómo la combinación de MATLAB con el brazo robótico Epson amplía notablemente las posibilidades de automatización y precisión en tareas específicas. Al trabajar con una imagen procesada digitalmente, se logró transformar datos abstractos en instrucciones concretas que el robot pudo ejecutar con alta precisión. Esto no solo refuerza la capacidad del sistema para realizar trazos complejos con exactitud, sino que también demuestra su potencial para aplicaciones en áreas más avanzadas, como la manufactura automatizada, la impresión de patrones personalizados o incluso el prototipado rápido. Además, esta experiencia pone de manifiesto la importancia de dominar tanto el software como el hardware para desarrollar soluciones tecnológicas integradas y funcionales.


### Eduardo David Salas Ayala: 
En esta práctica, se realizó un dibujo utilizando el brazo robótico Epson, pero con una diferencia significativa respecto a ejercicios previos, ahora se trabajó a partir de una imagen obtenida de la red y procesada con MATLAB. Esto permitió explorar las diversas capacidades del robot Epson. En esta ocasión, se cargaron datos específicos en el código, lo que permitió al robot seguirlos con alta precisión y comprender las instrucciones generadas por MATLAB.Por otro lado, esta experiencia destaca la versatilidad del robot para llevar a cabo diversas tareas. No solo es capaz de realizar dibujos mediante datos procesados en MATLAB, sino que también tiene el potencial de realizar actividades mucho más complejas con el apoyo de esta plataforma. Este ejercicio demuestra la versatilidad y el potencial del robot Epson para adaptarse a diferentes aplicaciones que requieren precisión, automatización y flexibilidad.


