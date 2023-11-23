# Configuracion del proyecto de NeatBeans

## Compiling 

Las 5 primeras

## Packaging 

Las 3 primeras

## Run

Elegir el main de la pantalla 

## Hacer un clean and build del proyecto

Esto generara un `jar` un `txt` en la carpeta `dist`

# Creacion del archivo ejecutable 

## Installar el launch4j

Para este apartado se deberá instalar un programa el cual es launch4j el cual es un
programa que permite crear archivos .exe que todos conocemos a partir de archivos .jar.
Este se puede descargar desde su página oficial para acceder a ella pulse [aqui](https://launch4j.sourceforge.net/).

## Uso del launch4j

Solo se escribira ha cerca de 

### Basic

| Apartado      | Que hace                                                                                                                                              |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Output file   | Crea el archivo de salida en la direccion indicada al final debe de tener obligatoriamente la extension `.exe`                                        |
| Jar           | Se le pasa la ruta del jar que se desa pasar a exe                                                                                                    |
| Icon          | Se le pasa la ruta de la imagen que tendra como icono esta debe de ser `.ico` para pasar de png a ico pulsa [aqui](https://convertio.co/es/png-ico/)  |

### Header 

Header que debe de tener seleccionado la opción GUI viene puesta por defecto

### JRE

Se debe de escribir las diferentes versiones tanto de `JRE` como de `Min JRE version` de normal se pondra la version **`1.0`**

### Spash

Sin tocar nada del apartado seleccionamos el engranaje de arriba a la derecha y creara un archivo con una extension `.xml`

# Creacion del archivo 

## Instalar el NSIS

Se utiliza el programa NSIS para instalarlo pulsa [aqui](https://nsis.sourceforge.io/Download)

## Crear un zip

Este archivo es necesario para que NSIS pueda crear el archivo de instalacion todos los archivo generados `exe`, `xml` y `txt` todo esto en una carpeta

## Creacion del archivo 

### 1ª Parte

Para esto en la opcion de compiler seleccionaremos la opcion `Installer based on .ZIP file` 

### 2º Parte 

Se le pasara el zip generado con el boton `open`, en el apartado de default folder se pondra `C:\Program Files` o la ruta deseada cambiaremos la compresion `BZip2` y seleccionaremos la ruta donde se creara el archivo de salida y pulsaremos la opcion generate 