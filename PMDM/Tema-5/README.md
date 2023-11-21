# Animaciones

Para crear una animacion en android estudio es necesario crear la animacion dentro de un xml, dentro de este archivo se le pasara la animacion deseada ya sea una `translate`, `rotate`, `scale`, `alpha` ...

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
| ------------------------- | ----------------------------------------------------- | 
| pivotX="valor"            | La posicion en horizontal en la que rotara el objeto  |
| pivotY="valor"            | La posicion en vertical en la que rotara el objeto    |
| fromDegrees="valor"       | El angulo en el que empieza rotar el objeto           |
| toDegrees="valor"         | El angulo en el que termina la rotacion del objeto    |

## Scale

| Valor                 | Significado                                           |
| --------------------- | ----------------------------------------------------- | 
| fromXScale="valor"    | El tamaño en horizontal en la que empieza el objeto   |
| toXScale="valor"      | El tamaño en horizontal en la que acabara el objeto   |
| fromYScale="valor"    | El tamaño en vertical en la que empieza el objeto     |
| toYScale="valor"      | El tamaño en vertical en la que acabara el objeto     |

## Alpha

| Valor                 | Significado                                                                           |
| --------------------- | ------------------------------------------------------------------------------------- | 
| fromAlpha="valor"     | Si es un `0` el objeto empieza siendo invisible si es un `1` empieza siendo visible   |
| toAlpha="valor"       | Si es un `0` el objeto acabara siendo invisible si es un `1` acabara siendo visible   |

## Universales

| Valor                 | Significado                                       |
| --------------------- | ------------------------------------------------- | 
| duration="valor"      | Sera el tiempo en microsegundos                   |
| interpolator="valor"  | Se le pasara como se hara la animacion            |
| startOfSet="valor"    | Se le pasa el numero de microsegundos que tarada  |

## LayoutAnimation

| Valor                     | Significado                                                                                                   |
| ------------------------- | ------------------------------------------------------------------------------------------------------------- | 
| delay="valor"             | El tiempo en el que el que se lanzara la siguiente animacion `0` seran todas a la vez `1` sera de una en una  |
| animationOrder="valor"    | De normal se usa el valor `normal`                                                                            |
| animation="valor"         | Se le pasa la animacion que va a cargar el contenido de dicho layout                                          |

## Ejemplo

### Parte del xml

- Parte del xml animacion normal

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <set xmlns:android="http://schemas.android.com/apk/res/android">
        <translate
            android:toXDelta="0%p"
            android:fromXDelta="-100%p"
            android:duration="5000"
            />
    </set>  
    ```

- Parte de xml animacion por layout

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <layoutAnimation xmlns:android="http://schemas.android.com/apk/res/android"
        android:delay="1"
        android:animationOrder="normal"
        android:animation="@anim/animation"
    />
    ```

### Parte de java
```java
Animation miAnimacion = AnimationUtils.loadAnimation(this, R.anim.animacion);
miAnimacion.setRepeatMode(Animation.RESTART);

// Hara que se repita un numero de veces
miAnimacion.setRepeatCount(20);  

// Hara que se repita hasta el infiinito
miAnimacion.setRepeatCount(Animation.INFINITE); 
```

# ArrayAdapter

Sirve para adaptar un array a un `spiner`, `autoCompleteTextView`, `multiAutoCompleteTextView` ... 

## Ejemplos 

### Por parte de java para el `Spiner` y `AutoCompleteTextView`

```java
// Por parte de java se le puede pasar un array String de valores 
spinner.setAdapter(new ArrayAdapter<String>(this, android.R.layout.simple_expandable_list_item_1, new String[]{"valor 1", "valor 2", ...}));

// Por parte de XML se le debe de pasar un nombre de una lista que este presente en un XML
spinner.setAdapter(ArrayAdapter.createFromResource(this, R.array.nombreListaXML android.R.layout.simple_expandable_list_item_1));
```

Donde por parte de xml debemos de crear un xml en la carpeta `values` con una estructura similar ha esta: 

### Por parte de xml para todos

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string-array name="nombreListaXML">
        <item>valor 1</item>
        <item>valor 2</item>
        <item>valor 3</item>
                ...
    </string-array>
</resources>
```

### AutoCompleteTextView

Tras hacer el setAdapter se le ha de pasar un valor mas el cual es: 

```java
multiAutoCompleteTextView.setTokenizer(new MultiAutoCompleteTextView.CommaTokenizer());
```

Esto hara que cuando se selecione el texto deseado a continuacion de este ponga una coma y un espacio `, `

# Escuchadores

Para que el usuario pueda seleccionar las diferentes partes de la intrfaz debemos de emplear `escuchadores` cada uno de estos sera distinto dependiendo del objeto que se use

- Spiner

    ```java
    spinner.setOnItemSelectedListener(new AdapterView.OnItemSelectedListener() {
            @Override
            public void onItemSelected(AdapterView<?> parent, View view, int position, long id) {
                switch(posotion){
                    case 0: {
                        // Bloque de comandos
                    }
                    break;
                    case 1: {
                        // Bloque de comandos
                    }
                    break;
                    //           ...
                }
            }
            @Override
            public void onNothingSelected(AdapterView<?> parent) {
                // Bloque de comandos
            }
        });
    ```

    Donde la posicion empieza siendo `0` 

- CheckBox and Switch
    ```java
    checkBox.setOnCheckedChangeListener(new CheckedBox.OnCheckedChangeListener() ) {
        public void onChekedChangeListener(CompoundButton buttonView, boolean pulsado){
            if(pulsado) {
                // Bloque de comandos
            }else {
                // Bloque de comandos
            }
        }
    }
    ```

- RadioButton

    ```java
    radioGroup.setOnCheckedChangeListener(new RadioGroup.OnChecekedChangeListener() {
        public void onCheckedChanged(RadioGroup group, int chekedId) {
            if (checkedId == R.id.radioButton1){
                // Bloque de comandos
            }else if(checkedId == R.id.radioButton1){
                // Bloque de comandos 
            }
        }
    });
    ```

    Donde en la operacion `checkedId == R.id.radioButton1` la R.id.radioButton1 es la id de cada uno de los radio buttons que posee el radio group

# Gradientes 

Los gradientes se crean haciendo un archivo xml en la carpeta drawable en este archivo se le pasaran varios parametros

| Valor                 | Significado                                                                       |
| --------------------- | --------------------------------------------------------------------------------- | 
| startColor="valor"    | Se le pasa el valor del color en el que el degradado empieza                      |
| centerColor="valor"   | Se le pasa el valor del color en el que el degradado tendra el color central      |
| endColor="valor"      | Se le pasa el color que deseas en el que el degradado terminara                   |
| angle="valor"         | Se le pasa el angulo que se le desea aplicar es recomendable multiplos de `45º`   |

## Ejemplo 

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape = "rectangle">
    <gradient
        android:startColor="@color/purpureDark"
        android:centerColor="@color/purpure"
        android:endColor="@color/purpureLight"
        android:type="linear"
        android:angle="45" />
</shape>
```

# Creadores

[@javiLeL](https://github.com/javilel/)
[@Leri457](https://github.com/Leri457)