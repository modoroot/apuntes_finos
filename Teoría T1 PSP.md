
## 1. Características de los procesos y su ejecución
Un proceso es un ente abstracto que representa al conjunto de instrucciones de un
programa en ejecución y bajo el control del sistema operativo. Un proceso puede
atravesar diversas etapas en su «ciclo de vida». Los estados en los que puede estar
son:
- **Admitido:** el proceso ha sido admitido por el sistema operativo y entra
en la cola de procesos, pasando al estado en espera o preparado.
 - En ejecución: el proceso se está ejecutando dentro de
microprocesador.
- **Pausado/detenido/en espera/preparado:** el proceso tiene que seguir en
ejecución pero en ese momento el S.O tomó la decisión de dejar paso
a otro.
- **Interrumpido o bloqueado:** el proceso tiene que seguir en ejecución
pero el usuario ha decidido interrumpir la ejecución, o bien está
pendiente de que ocurra un evento externo como por ejemplo la
finalización de una operación E/S.
- **Finalizado**: el sistema operativo saca al proceso de la cola de procesos
y libera los recursos utilizados por el mismo.
![[Pasted image 20221115201954.png]]
En el sistema operativo, un proceso representa a código ejecutable de un programa,
los datos y pila de programa, el contador del programa, el puntero a pila y otros
registros necesarios.
El sistema operativo decide cuándo debe para la ejecución de un proceso y arrancar
otro, por ejemplo cuando ha consumido mucho tiempo de CPU. Cuando se
suspende la ejecución de un proceso, el sistema operativo guarda el estado de
ejecución del mismo, esto es necesario para poner en ejecución de nuevo el
proceso.
El Bloque de Control de Proceso (BCP) es el lugar donde se almacena la
información de cada proceso.
## 2. Hilos y procesos
La función fork() se utiliza para crear un proceso hijo idéntico al proceso que llama a
la función, mismo código y datos. Cada uno de los dos procesos, padre e hijo,
tienen memoria independiente por lo que las variables se pueden modificar de
manera independiente. Una vez se crea el proceso hijo, ambos, padre e hijo
continúan la ejecución a partir del código que haya después de la llamada a la
función fork().
Un hilo es una secuencia de código (fragmento de un programa o programa
completo) en ejecución dentro del contexto de un proceso. Los hilos se gestionan
desde un proceso padre, no se pueden ejecutar solos. Dentro de un proceso
pueden existir varios hilos en ejecución.
Algunas de las diferencias más importantes entre procesos e hilos son:
● Los hilos comparten el espacio de memoria del proceso, muchos comparten
datos y espacios de direcciones en memoria, a diferencia de los procesos
que disponen de espacios de direcciones de memoria independientes.
● Los hilos y procesos tienen ciclos de vida gestionados por transiciones y
estados. Sin embargo, los cambios de estado en los procesos son más
costosos ya que es necesario cambiar todo el contexto de ejecución,
mientras que los hilos pueden cambiar de estado manteniendo el proceso
que los contiene el mismo contexto de ejecución.
● Debido al cambio de contexto que tiene que realizar el procesador cada vez
que un hilo cambia de estado, es más rápido crear y terminar un hilo que un
proceso.
● En la comunicación entre procesos interviene el núcleo del procesador,
mientras que en la comunicación entre hilos no necesita intervenir el núcleo,
lo puede realizar el proceso que contiene a los hilos.
## 3. Programación concurrente
## 4. Progamación paralela y distribuida
