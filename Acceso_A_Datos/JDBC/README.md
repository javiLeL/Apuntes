# JDBC
## 0º Descargar la libreria
[Link de descarga](https://github.com/javiLeL/Apuntes/raw/master/Acceso_A_Datos/JDBC/mysql-connector-j-8.0.33.jar)
## 1º Paso Crear las conexiones
Creamos la conexion con la siguiente linea
```java
Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/"+nombreBaseDeDatos, usuario, password);
```


#### **Ejemplos**

| **String**          | **Valor**   |
|-------------------- | ----------- |
| `nombreBaseDeDatos` | "libreria"  |
| `usuario`           | "root"      |
| `password`          | "1234"      |

## 2º Paso Crear la sentencia
```java
PreparedStatement preparedStatement = connection.prepareStatement(sentencia)
```
- Si se utliliza el caracter `?` se puede sustituir partes de la sentencia con el comando
    ```java
    preparedStatement.setInt(num, valor);
    preparedStatement.setString(num, valor);
    preparedStatement.setDouble(num, valor);
    ```
    Donde **num** sera la posicion empezando por `1` y el **valor** sera el nuevo valor que va ha adquirir, esto dependera del tipo de valor que se le haya pasado siendo `int`, `String` o `double` 

- #### **Ejemplos de sentencias**

    | Nombre Sentencia  | Ejemplo |
    | ----------------- | ------- |
    | Select            | SELECT nombre_columna1, nombre_columna2, ... FROM nombre_tabla WHERE condicion |
    | Insert            | INSERT INTO nombre_tabla VALUES (valor1, valor2, ...)|
    | Update            | UPDATE nombre_tabla SET nombre_columna = valor WHERE condicion |
    | Delete            | DELETE FROM nombre_tabla WHERE condicion  |



## 3º Paso Lanzar la sentencia (compatible solo con las sentencias que no devuelven nada)

 Lanzamos la sentencia con la siguiente linea 
```java
preparedStatement.executeUpdate();
```
Este metodo devolvera un `int` el numero resultante sera al numero de filas que fueron afectadas
## 4º Paso Lanzar la sentencia (compatible solo con las sentencias que devuelven valores)
- Usaremos una clase que almacene lo que mando la base de datos
    ```java
    ResultSet resultSet = preparedStatement.executeQuery();
    ```
- Si lo que queremos es conseguir estos valores se hara con la sentencia
    ```java
    while(resultSet.next()){
        resultSet.getInt(num)
    }
    ```
    Donde el get puede ser `int`, `String` o `double` y donde el `num` es la posicion de la columna que devuelve (cada iteracion del while es una fila)

## Creadores
[@javiLeL](https://github.com/javilel/)
[@Leri457](https://github.com/Leri457)
