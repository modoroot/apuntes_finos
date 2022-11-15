
![[Recording 20221115202131.webm]]
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
información de cada proceso. La información que contiene este bloque es la
siguiente:

## 2. Hilos y procesos
## 3. Programación concurrente
## 4. Progamación paralela y distribuida
