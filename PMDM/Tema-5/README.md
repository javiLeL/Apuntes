# Animaciones

Para crear una animacion en android estudio es necesario crear la animacion dentro de un xml, dentro de este archivo se le pasara la animacion deseada ya sea una `tralacio`, `rotate`, `scale`, `alpha` ...

- Parte del xml 
    
    Dependiendo de la animacion se la pasara unos valores u otros.

## Traslate
| Valor                 | Significado                                               |
| --------------------- | --------------------------------------------------------- | 
| fromXDelta="valor"    | La posicion en horizontal en la que empieza la animacion  | 
| fromYDelta="valor"    | La posicion en vertical en la que empieza la animacion    |
| toXDelta="valor"      | La posicion en horizontal en la que acabara la animacion  |
| toYDelta="valor"      | La posicion en vertical en la que acabara la animacion    |


## Rotate
| Valor                     | Significado                                           |
| ------------------------- | ------------------------------------------------------| 
| pivotX="valor"            | La posicion en horizontal en la que rotara el objeto  |
| pivotY="valor"            | La posicion en vertical en la que rotara el objeto    |
| fromDegrees="valor"       | El angulo en el que empieza rotar el objeto           |
| toDegrees="valor"         | El angulo en el que termina la rotacion del objeto    |

## Ejemplo

- Parte de xml
    ```xml
    <translate
        android:fromXDelta="0%p"
        android:toXDelta="200%p"
        android:duration = "2000" 
    />  
    ```

- Parte de java
    ```java
    Animation miAnimacion = AnimationUtils.loadAnimation(this, R.anim.animacion);
    miAnimacion.setRepeatMode(Animation.RESTART);
    miAnimacion.setRepeatCount(20); o miAnimacion.setRepeatCount(Animation.INFINITE); 
    ```
