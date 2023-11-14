# Creacion y uso de hilos
## Uso basico de los hilos

- Como crear un hilo 
    
    Para poder crear un hilo debemos de hacer que la clase importe de la clase `Runable` esta posee un metodo el cual es `void run()` este debe de ser implementado para el correcto funcinamiento del mismo lo que se encuentre dentro de este metodo se ejecutara al llamar el metodo `void start()`

- Metodos y su uso basico
  
  - Metodos de lanzamiento del hilo 

    | Metodo                                | Funcion                                                                       |
    | ------------------------------------- | ----------------------------------------------------------------------------- |
    | void run()                            | Se ejecutar al lanzarse el hilo cuando este termine el hilo se "morira"       |
    | void start()                          | Lanza el hilo junto con el metodo run                                         | 
    | void sleep(long ms)                   | permite dormir un hilo durante x `ms` o milisegundos                          |
    | void join()                           | Permite que un hilo se junte con otro *El que lo ejecuta y el que lo llama*   |
    | void interrupt()                      | Interrumpe un hilo                                                            |
    | Thread currentThread()                | Devuelve el acceso a memoria del hilo                                         |

  - Metodos de informacion  

    | Metodo                            | Funcion                                                   |
    | --------------------------------- | --------------------------------------------------------- | 
    | boolean isInterrupt()             | Devuelve si el hilo se interrumpio o no                   |
    | boolean isAlive()                 | Devuelve si el hilo esta vivo                             |
    | long getId()                      | Devuelve el numero de id del hilo                         |
    | Thread getState()                 | Devuelve el estado hilo                                   |
    | String setName(String name)       | Cambiara el nombre del hilo al que reciba                 |
    | String getName()                  | Devuelve el nombre del hilo                               |
    | void setPriority(int priority)    | Pone la prioridad del hilo a la del valor que se le pasa  |
    | void getPriority()                | Devuelve la prioridad que posee el hilo                   |

## synchronized

Este modificador permite que el metodo solo pueda ejecutarlo un unico hilo este bloquera la entrada al resto de hilos hasta que el hilo que ya habia entrado salga de este
