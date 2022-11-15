
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
La programación concurrente se refiere a la ejecución de procesos de manera
simultánea pero no paralela, es decir los procesos no se ejecutan en distintos
procesadores o núcleos.
**Beneficios de la programación concurrente**
Algunos de los beneficios que aporta la programación concurrente son:
- Mejor aprovechamiento de la CPU. Un proceso puede consumir ciclos
de CPU mientras otro hace uso de recursos de E/S.
- Mayor velocidad de ejecución. Repartir el trabajo entre varios procesos
puede mejorar la velocidad de ejecución en algunos casos porque se
aprovecha mejor el tiempo.
- Solución de problemas de tipo concurrente. Algunos problemas sólo se
pueden solucionar de manera eficiente mediante programación
concurrente, por ejemplo: software en tiempo real (manejan sensores y
actuadores), servidores de chat , servidores de correo, servidores web,
navegador web (descarga archivos mientras realiza una búsqueda en
un buscador web), etc.
**Concurrencia y hardware**
En un sistema monoprocesador se puede llevar a cabo la programación
concurrente gestionando el tiempo que el procesador dedica a cada proceso.
El SO va alternando el tiempo entre procesos, cuando el proceso necesita un
recurso de E/S, abandona el procesador y otro proceso lo ocupa
aprovechando los ciclos de CPU disponibles. La forma de gestionar los
procesos en un sistema monoprocesador recibe el nombre de
multiprogramación. En un sistema monoprocesador todos los procesos
comparten la misma memoria. La forma de comunicar y sincronizar procesos
se realiza mediante variables compartidas. En un sistema multiprocesador es
posible tener varios procesos en ejecución, paralelismo real.
Los sistemas multiprocesador se pueden clasificar en:
**Fuertemente acoplados:** cuando poseen memoria compartida por
todos los procesadores.
**Débilmente acoplados:** cuando los procesadores tienen memorias
locales y no existe compartición de memoria.

### Inconvenientes de la programación concurrente
**Los principales inconvenientes son:**
- Exclusión mutua. El acceso a una variable compartida, para
actualizarla, por varios procesos al mismo tiempo representa una
operación muy común en programación concurrente. Las variables
compartidas que representan una región crítica deben estar
gestionadas para evitar errores producidos por los intentos de lectura y
escritura de distintos procesos de manera no sincronizada. Se deben
sincronizar las lecturas y actualizaciones de las variables de una
región crítica para evitar resultados erróneos.
- Condición de sincronización. Este problema se refiere a la necesidad
de sincronización de los procesos ante operaciones concurrentes.
Puede ocurrir que un proceso entre en un estado en espera y no
pueda continuar su ejecución hasta que otro proceso haya liberado la
CPU. La programación concurrente dispone de mecanismos para
bloquear procesos a la espera de una determinada señal y
desbloquearlos cuando dicha señal llegue.
## 4. Progamación paralela y distribuida
Un programa paralelo está diseñado para programación concurrente y se ejecuta en
un sistema multiprocesador. El procesamiento paralelo permite la ejecución, al
mismo tiempo, de distintas tareas para resolver un problema. El problema se divide
en tareas independientes que cada hilo o proceso ejecuta, y que cuando finalizan
proporcionan los resultados al hilo o proceso principal. Para ello los hilos o procesos
deben comunicarse e intercambiar información, según como se realice el
intercambio de información tendremos distintos modelos de programación paralela:
- Memoria compartida: los procesadores (o núcleos) comparten la memoria,
todos acceden al mismo espacio de memoria. De esta manera todo lo que se
escribe por un procesador es leído por el mismo y el resto.
- Paso de mensajes: cada procesador (o núcleo) dispone de su propia
memoria que es accesible sólo por él. Para que un procesador pueda tener
información de otro es necesario que la solicite mediante un mensaje
(Parallel Virtual Machine PVM, sigue este modelo).
El tipo de almacenamiento compartido de los procesadores da lugar a distintas
arquitecturas paralelas:
- Sistemas de memoria compartida o multiprocesadores: los procesos
comparten físicamente la memoria.
- Sistemas de memoria distribuida o multicomputadores: cada procesador
dispone de su memoria y la comparte a través canales de comunicación muy
rápidos.

#### Las ventajas del procesamiento paralelo son:
-  Proporciona ejecución simultánea de tareas.
-  Disminuye el tiempo total de ejecución
-  Permite resolver problemas complejos y con gran volumen de información
-  Posibilita la utilización de recursos no locales, por ejemplo recursos en una
- red distribuida.
-  Eliminación de arquitecturas de cómputo centralizadas.
- os inconvenientes del procesamiento paralelo son:
-  La programación es más compleja
-  El consumo de energía aumenta al usar más ordenadores
-  Mayor complejidad en el acceso a los datos
-  Es difícil la comunicación y sincronización entre tareas

#### Los inconvenientes del procesamiento paralelo son:
-  La programación es más compleja
-  El consumo de energía aumenta al usar más ordenadores
-  Mayor complejidad en el acceso a los datos
-  Es difícil la comunicación y sincronización entre tareas

Los sistemas distribuidos son difíciles de definir, algunas definiciones válidas serían
las siguientes:
● “Un sistema en el cual componentes conectados a través de una red de
computadoras se comunican y coordinan sus acciones mediante el
intercambio de mensajes”. Principales características:
concurrencia de componentes, ausencia de reloj global e independencia de
fallos en sus componentes
● Un sistema distribuido es una colección de computadoras independientes que
dan la apariencia al usuario de ser una computadora única”
De lo anterior podemos extraer una definición de sistema distribuido, lo vamos a
definir como aquel en el que los componentes hardware o software, localizados en
ordenadores unidos mediante red, comunican y coordinan acciones sólo mediante
paso de mensajes. Consecuencias de la definición:
	a) Concurrencia de procesos y compartición de recursos.
	b) Inexistencia de reloj global. La cooperación de procesos necesita
coordinación de las acciones que se van a ejecutar mediante el intercambio
de mensajes. Los ordenadores que ejecutan los procesos coordinados
pueden sincronizar sus relojes con límites en la precisión. Por lo que no hay
una única noción global del tiempo.
c) Fallos independientes. Los sistemas distribuidos incorporan fallos de red que
no dependen directamente del resultado de la ejecución del proceso que la
usa. Cada componente del sistema puede fallar independientemente,
ordenador, proceso, red, etc.

Algunos ejemplos de sistemas distribuidos son:
● Internet: Es una red extensa de ordenadores de diferentes tipos
interconectados. Los programas que se ejecutan en los ordenadores
conectados a Internet interactúan mediante el paso de mensajes, empleando
un medio común de comunicación. Internet proporciona una infinidad de
servicios como correo electrónico, ficheros compartidos, multimedia, etc.

● Intranets: Es una red privada que también puede formar parte de la red de
Internet conectando por medio de un router. Los servicios que proporciona la
intranet a sus usuarios se protegen ante el acceso no autorizado de usuarios
y de programas maliciosos que provienen de Internet. Normalmente se
utilizan cortafuegos para implementar la configuración de seguridad y realizar
un filtrado de mensajes que entran y salen de la intranet.

● Computación móvil y ubicua: Se llama computación móvil a la realización de
tareas de cómputo mientras el usuario está en movimiento o visitando lugares
distintos a su entorno habitual. Los usuarios pueden acceder a los recursos
de sus intranets conectando a través de Internet.

La computación ubicua corresponde a la utilización de dispositivos de
computación pequeños presentes en los entornos de trabajo de los usuarios.
Normalmente la presencia de pequeños computadores en distintos entornos
sólo tiene sentido si pueden comunicarse entre sí (ej. La lavadora). Los
ordenadores portátiles se comunican conectándose a través de una red local
inalámbrica. Los teléfonos móviles pueden conectarse a Internet para una
comunicación de datos usando GPRS, 3G, 4G o 5G.

La computación móvil y ubicua se solapan puesto que un usuario en
movimiento puede beneficiarse de los ordenadores de los entornos por los
que va pasando.
● Recursos compartidos y web
Utilizamos el término servicio para una funcionalidad proporcionada por los
ordenadores por la cual se gestionan un conjunto de recursos relacionados y
se presenta una interfaz de aplicación al usuario.

Existen varios modelos de programación para la comunicación entre los procesos de un
sistema distribuido:
- Sockets: proporcionan una conexión entre dos puntos de una red, a través de
los cuales se pueden comunicar 2 procesos.
- Llamada a procedimientos remotos (RPC).: permite a un proceso cliente
llamar a un proceso servidor en ejecución. El proceso servidor define una
interfaz de servicio con los métodos disponibles para ser llamados
remotamente.
- Invocación remota de objetos: un objeto, dentro de un proceso, puede llamar
a métodos de un objeto que reside en otro proceso (RMI: Remote Method
Invocation). Java RMI extiende el modelo de objetos para proporcionar
soporte de objetos distribuidos en Java.

#### Las principales ventajas de la programación distribuida son:
- Se pueden compartir recursos y datos
- Capacidad de crecimiento incremental
- Mayor flexibilidad al poderse distribuir la carga de trabajo entre diferentes
- ordenadores
- Alta disponibilidad
- Soporte de aplicaciones inherentemente distribuidas
- Carácter abierto y heterogéneo
- Algunos de los inconvenientes son:
- Aumenta la complejidad
- Problemas con las redes de comunicación (pérdida de mensajes, saturación
- de tráfico de red, etc)
- Problemas de seguridad como por ejemplo ataques de denegación de
- servicio.