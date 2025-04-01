# Infinity Jump 🚀

#### _Participantes_

Creado por el estudio Silver Way

- Santiago Cordova Molina
- Maria Rivera Gutierrez
- Kevin Javier Esquivel Villafuerte A01174634
  
###### **Aviso de derechos de autor/Información del autor**

## _Game Design Document_

## _Índice_

---

1. [Índice](#índice)
2. [Diseño del juego](#diseño-del-juego)
    1. [Resumen](#resumen)
    2. [Juego](#juego)
    3. [Mentalidad](#mentalidad)
3. [Técnico](#técnico)
    1. [Pantallas](#pantallas)
    2. [Controles](#controles)
    3. [Mecánicas](#mecánicas)
4. [Diseño de niveles](#diseño-de-niveles)
    1. [Temas](#temas)
    2. [Flujo de juego](#flujo-de-juego)
5. [Desarrollo](#desarrollo)
    1. [Clases abstractas](#clases-abstractas)
    2. [Clases derivadas](#clases-derivadas)
6. [Gráficos](#gráficos)
7. [Sonidos y Música](#sonidos-y-música)
    1. [Atributos de estilo](#atributos-de-estilo)
    2. [Sonidos y música necesarios](#sonidos-y-música-necesarios)
8. [Itinerario](#itinerario)

##  _Diseño del Juego_

---

### **Resumen**
El personaje principal salta para desplazarse verticalmente en un mapa con plataformas en aleatorio que tiene que alcanzar a la luna. Al llegar a cierta altura, tendrá que enfrentar a un enemigo para matarlo desde arriba y así avanzar al siguiente nivel. 

### **Juego**

Nuestro juego se trata de que nuestro personaje principal () tiene que ir saltando entre diferentes plataformas hasta llegar a una determinada altura. Más explícitamente, esta altura va a ser lograda al pasar una serie de obstáculos, dividiendo el objetivo en 3 niveles, cada uno de estos va a estar constituido por cierto número de plataformas (100, 150 y 200 respectivamente) y un mini jefe al pasar todas estas plataformas.

Cada uno de los niveles está ambientado de diferente manera, representando el progreso que hace el jugador cada que derrota a un jefe, las plataformas y el fondo cambian dependiendo del nivel en el que se encuentre. Estas plataformas son la forma de avanzar del jugador, ya que la pantalla lo que va a ir mostrando va a ser únicamente las plataformas y si el jugador no calcula bien el salto y no rebota en una de estas va a morir instantáneamente, regresando al inicio de todo el juego independientemente del nivel en el que se encontraba.

Existe la posibilidad de conseguir mejoras para el jugador, ya sean temporales o permanentes a lo largo de sus intentos. Un ejemplo de una temporal sería una catapulta que te haga saltar 4 plataformas de un solo salto, un ejemplo de una mejora permanente sería disminuir la velocidad de caída del jugador en 5% para que tenga mayor control sobre esto.

Los mini jefes van a encontrarse después de pasar el número de plataformas determinado por nivel, y va a ser una página diferente, donde no puedes caerte y van a haber plataformas definidas por nosotros las cuales van a constituir el nivel del jefe en sí y te van a dar la libertad de moverte para poder derrotar a este. Este jefe va a tener una barra de vida y para poder hacerle daño el jugador va a tener que saltar arriba de ellos estilo Mario Bros. Si el jugador colisiona con el jefe en cualquier otra parte de este que no sea su parte superior, va a recibir daño y también, con su respectiva barra de vida, eventualmente después de un número de golpes puede morir ante el jefe.

### **Mentalidad**

El juego está diseñado para que el jugador esté constantemente poniendo a prueba sus habilidades. Debido a la mecánica principal del juego, que es el salto continuo del personaje, el jugador prácticamente va a tener que estar activamente prestando atención a sus movimientos. Solo hay un momento donde esto no es así, al derrotar cada uno de los mini jefes, y con mucha razón, ya que buscamos que sea algo frenético que una vez completes tengas como recompensa un momento de calma y un tiempo para poder utilizar las monedas que has ido recolectando y comprar tus mejoras favoritas.

##  _Técnico_

---

### **Pantallas**

+ Pantalla de inicio de sesión
    - Pantalla de menú principal
      1. Pantalla principal del juego
           + Pantalla de la tienda de mejoras
           + Pantalla de pausa
                1. Pantalla de controles
                2. Regresar al menú principal
           + Pantalla al morir
           + Pantalla por mini jefe
      3. Pantalla de estadísticas
      4. Pantalla de créditos finales

### **Controles**

+ Las flechas ( `←` y `→` ) y las teclas `A` y `D` van a servir para desplazar al personaje en su eje X, de izquierda a derecha respectivamente. Como el usuario no va a tener que saltar manualmente, la flecha hacia arriba no servirá de nada.
+ En momentos específicos (como el inicio de un run del jugador, o después de derrotar un minijefe) el juego le va a dar la oportunidad al jugador de presionar la tecla `T` para abrir la tienda de mejoras.
+ Con la tecla `Esc` se despliega un menú de pausa.

### **Mecánicas**

Las plataformas en Infinity Jump se generan de manera aleatoria, pero al decir esto me refiero exclusivamente al eje X en el que se encuentren y a su tipo, ya que para temas de dificultad contamos con varios tipos de plataformas. Pero en sí siempre se van a generar cada Y coordenada, con una distribución que se ajusta a la dificultad del nivel. A medida que el jugador asciende, las plataformas pueden aparecer con espaciado variable, forzando al jugador a ajustar sus tiempos de movimiento.

El juego cuenta con un sistema de físicas simplificado, donde el personaje tiene una velocidad de caída constante, pero ciertos ítems pueden alterar la gravedad o permitir movimientos especiales.

En cuanto a las colisiones, el juego detectará si el usuario efectivamente aterrizó en una plataforma para que al hacer contacto con esta vuelva a saltar y de esta manera conseguir llegar al mini jefe de cada nivel después de pasar por todas las plataformas de estos.

Vamos a manejar físicas expeciales para ciertas mejoras, ya sean temporales o permanentes, esto con el objetivo de darle un mejor control al jugador sobre su personaje. Estas físicas pueden ser tales como una reducción en la velocidad de caida, un mayor salto o incluso un rebote en caso de caer al vacío.

Los enemigos que se van a encontrar son principalmente los minijefes y eventualmente en los niveles 2 y 3 ciertas plataformas contarán con la mecánica de que si las tocas por debajo te hacen daño, y para vencerlos tienes que saltar encima de ellos. Los jefes teniendo una barra de vida la cual será reducida con cierto número de saltos.

##  _Diseño de Niveles_

---

### **Temas**

1. 🌲 **Bosque**
    1. Estado: Misterioso, pasivo, inquietante
    2. Objetos:
        1. _Ambiente_: Árboles, montañas, animales de bosque, cielo despejado
        2. _Interactivo_: Ramas
2. ☁️ **Cielo**
    1. Estado: Impredecible, dinámico
    2. Objetos:
        1. _Ambiente_: Aviones, nubes enormes
        2. _Interactivo_: Nubes, pájaros
3. 🌌 **Espacio exterior**
    1. Estado: Asfixiante, eufórico, frenético
    2. Objetos:
        1. _Ambiente_: Planetas, estrellas fugaces
        2. _Interactivo_: Cohetes espaciales, OVNI's

### **Flujo de Juego**


1. El jugador empieza en el centro de la pantalla, debajo de las primeras plataformas visibles del primer nivel
2. En cuanto presiona la tecla de iniciar partida, el personaje del jugador comienza a saltar automáticamente, y el usuario tiene que comenzar a utilizar las plataformas arriba de él para ir subiendo en el nivel.
3. Mientras más plataformas vaya subiendo, va ir encontrando objetos que le ayuden como monedas para gastar en un futuro en la tienda o mejoras de un solo uso como un gran salto de 5 plataformas. Además va a encontrarse con plataformas que tienen una mayor dificultad como las del primer nivel que van a haber algunas que desaparezcan después de un salto del usuario en ellas.
4. Al pasar el número de plataformas por nivel, va a encontrarse con un portal que lo va a trasladar al mini jefe de cada nivel, siendo ese el punto donde no puede caerse pero sí puede morir por daño del jefe.
5. Después de derrotar al jefe, se le va a dar la oportunidad de comprar mejoras en la tienda mientras sigue en esa pantalla, y en cuanto decida avanzar únicamente va a tener que saltar la plataforma que se le va a generar para tomar el portal de salida en la parte superior de la pantalla.
6. Tiene que repetir este proceso por 3 diferentes niveles y mientras vaya progresando en estos las plataformas van a ir aumentando su nivel de dificultad y los mini jefes de cada nivel también.
7. Concluye el juego una vez derrotado el jefe del tercer nivel y se le agradece haber jugado.


##  _Desarrollo_

---

### **Clases abstractas**

### **Clases derivadas**

## _Gráficos_

---

Para este juego vamos a usar un estilo animado de pixel art. Este estilo se podrá ver alrededor de todo el juego, tanto en los personajes, el principal y los enemigos, las plataformas en los diferentes niveles, como en las páginas. Esto con la finalidad de hacer que le juego se sienta en el mismo universo aunque vayas avanzando de nivel.

Los colores que usaremos en el juego serán llamativos pero siempre acorde al ambiente para que se puedan identificar en cualquier escenario, además de siempre los mejores para el estilo visual mencionado anteriormente. El personaje tendrá el mismo color blanco para que se pueda distinguir en cualquier nivel. Las plataformas cambiaran de color dependiendo del ambiente del nivel, que quede con la tematica simulando algo que se encuentre en ese ambiente. Por ejemplo, en el primer nivel que es un bosque, la plataforma es verde y café como una rama de los árboles del fondo de este mismo. 

Habrá un cuadro explicativo con los controles del juego en el apartado de “Controles” que aparecerá al darle pausa al juego o en el menú principal de este. De esta manera el jugador sabrá cómo moverse. Además cada vez que el jugador complete un nivel, se regresará una nueva página en donde va a poder acceder a la tienda, en donde podrá gastar sus monedas en mejoras temporales o permanentes. Antes de comprar se verá una pequeña descripción de qué es lo que hace dicha mejora. 

Diseños: 

1. Personajes
    1. Personaje Principal

    2. Enemigo 1

    3. Enemigo 2
       
    4. Enemigo 3
  

2. Plataformas 
    1. Primer nivel: simulando un tronco, verde por dentro con contorno café.
       

    2. Segundo nivel: simulando una nube, blanco por dentro con contorno azul obscuro.


    3. Tercer nivel:  simulando una estrella, amarillo por dentro con contorno naranja.


3. Fondos
    1. Fondo de bosque:
   


    2. Fondo de cielo: 
       
    

    3. Fondo de espacio:

   

4. Mejoras
    1. Permanentes:
         1. Mayor salto

   
         2. Mayor daño a enemigos
         
         
         3. Mejor defensa contra enemigos


    1. Temporales
         1. Escudo
            
           
            
         2. Monedas Dobles
            
            
            
         3. Salto Doble
            
           

6. Icono del  juego
   


##  _Sonidos y Música_

---

### **Atributos de estilo**

La música del juego dependerá del nivel de dificultad del nivel en el que se encuentre el jugador, es decir, no será una única temática a lo largo de todo el juego y esto reflejará el progreso del jugador a medida avanza por los niveles.

Buscaremos que cada uno de estos tracks reflejen efectivamente lo que el jugador está experimentando, es decir, en cada uno de los 3 mini jefes, una canción que exprese la dificultad de estos y sea exclusiva del evento, además una para cada nivel de plataformas que si bien será más pasiva se logrará diferenciar una de la otra.

Para los efectos de sonido, buscamos que sean claros y funcionales, proporcionando retroalimentación sin saturar la experiencia auditiva. Queremos que cada sonido ayude al jugador a reaccionar a lo que sucede en la pantalla sin distraerlo.


### **Sonidos y música necesarios**

#### Sonidos

+ Efectos de movimiento. Efectos de sonido al rebotar en plataformas, caer al vacío o chocar con obstáculos.
+ Sonidos de los jefes. Ruidos de movimiento, golpes o ataques.

#### Música

+ Tema del menú. Una melodía previa al inicio del juego, tranquila pero anticipatoria.
+ Música en los niveles. Un ritmo por nivel, con su propio estilo musical, como un tema misterioso en el bosque o algo más intergaláctico en el espacio.
+ Música en los jefes. Una pista única por jefe para demostrar su dificultad y desafío a la hora de encontrarlos.

## _Itinerario_

---


1. Determinar el concepto general del juego (primeras 3 semanas)
    1. Mecánicas
        1. Compra de habilidades
        2. Aleatoriedad en las plataformas
        3. Movimiento
    2. Reglas
        1. Gestión de habilidades
        2. Requerimientos de 
2. Desarrollo de documentación/issues del proyecto (semana 4)
    1. Historias de usuario
    2. Casos de uso
    3. Issues
4. Primer sprint (semana 5)
    1. Inicialización base de datos
    2. Assets del videojuego 
5. Segundo sprint (semana 6)
    1. Programación de clases abstractas del juego
        1. Habilidades
        2. Jugador
        3. Obstáculos
        4. Entorno
6. Tercer sprint (semana 7)
    1. Desarrollo de clases derivadas
    2. Desarrollo de web
7. Cuarto sprint (semana 8)
    1. Conexión de web con base de datos y videojuego
    2. Sprites y visuales
8. Quinto sprint (semana 9)
    1. Terminar visuales y audio
    2. Web completamente terminada y funcional
9. Semana 10
    1. Presentación final del videojuego
