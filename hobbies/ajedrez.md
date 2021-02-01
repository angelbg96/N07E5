# Ajedrez

## Estrategia
- Siempre tener un plan
- Paciencia para realziar una jugada, se debe esperar el momento oportundo
- Evitar ser materialista, realizar alguna jugada intermedia puede ser mejor opción, y luego recuperar material
- Hacer creer al rival que el ataque más obvio es el de mayor interés, pero por la posición no es así
- Crear ataque
    * Ver debilidades del rey contrario
    * Piezas participantes o que pueden participar en el ataque
    * Piezas participantes o que puede participar en la defensa
    * Analizar elementos tácticos en la posición
    * Hacerse la pregunta de ¿puede haber un contra ataque?
- Defensa activa
    * La mejor defensa es el ataque : contra ataque, que las piezas no se centren en el punto atacado
    * Método de simplificación : Intercambio de piezas
    * Defensa pasiva : Llevar piezas a defender el punto atacado
    * Buscar entradas contra el rey atacado
- Columna abierta: No existen peones sobre la columna, cuando no hay un peon de alguno de los dos bandos se dice que la columna está semiabierta
- Fila libre: No hay piezas colocadas en esa fila, sirve para cambiar de flanco
- Fortaleza: Piezas contrarias no pueden llegar a la posición del rey para dar jaque, las pienzas defensivas no permiten la acción de las atacantes sobre el rey

## Táctica
- Doble amenaza : Usualmente se dan con el avance de un peón, saltos de caballo, jaque más ataque a pieza indefensa
- Clavada de pieza : Pieza inmovil ya que se antepone a la acción de un ataque al rey o una pieza mayor. Atacar pieza clavada, "La pieza clavada no defiende nada"
    * Para salir de una clavada se pueden seguir las opciones:
    * Explusar a la pieza atacante
    * Interponer otra pieza entre la clavada y la atacada con rayos X
    * Retirar pieza mayor que está siendo atacada por rayos X
- Ataque a la descubierta : Una pieza se mueve con tal de dejar que otra pieza realice el ataque. La pieza que se mueve debe ir a una casilla donde siga generando amenazas o no corra peligro
    * Cuando la pieza genera el ataque es contra el rey es un _jaque a la descubierta_, cuando la pieza que se mueve también da un jaque al rey es un _jaque doble_
- _Desviación_ : Localizar a la pieza princpial que defiende al rey y jugar contra ella, el objetivo es que esa pieza vaya a otra casilla y deje de defender:
    * Expulsar pieza de su casilla
    * Cambiar una pieza con ella
    * Sacrificar una pieza para eliminarla
    * Suele usarse cuando la pieza defiende dos puntos de ataque, _está sobrecargada_
- Atracción : Llevar una pieza a alguna casilla donde nos interesa que esté
    * Se lleva a cabo un sacrificio, el rey contrario al estar en jaque debe capturar y luego se crea _red de mate_
    * Atraer alguna pieza mayor a una casilla para llegar a hacer una _enfilada_
- Jugada intermedia : Movimiento de pieza que irrumpe con el flujo más obvio de la variante que se está desarrollando, se crea una amenaza y posteriormente remotar el flujo de la variante o sale de ella (defensa)
- Extracción : Sacar al del de su refugio, sacrificando material y/o con jaques
- Enfilada : Se ataca una pieza, cuando esta se retire se captura otra pieza que estaba detrás de ella (p_ataque, p1_rival, p2_rival)
- Rayos X : Influencia de una pieza a través de la pieza del rival hacia otra pieza o punto (p1_ataque, p_rival, p2_ataque)


## Generar peon pasado en finales
- 3 vs 3
    * Se mueve peón central, el rival captura con algún peon lateral
    * Si captura con el peón de la derecha|izquierda, sobre ese carril se pretende avanzar, por lo que con el peón de la izquierda|derecha se avanza atacando el peón retrasado central del rival, por lo que así se genera el peón pasado
- 4 vs 4
    * Se avanza peón de un extremo, el contrario captura con uno de los peones centrales
    * Se avanza peón del otro extremo, el contrario captura con el otro peón cental
    * Se avanza un peón central, inevitablemente ya se está generando peón pasado


## Patrones geométricos
- Peon vs Rey: Cuando el peon se encuentra a más de la mitad del tablero se imagina una diagonal desde su posición hasta la fila de coronación, si el rey se encuentra dentro del cuadrado formado, alcanza al peon para capturarlo
- Alfil vs Caballo: si el alfil se coloca a 3 casillas del caballo (por fila o por columna), controla 4 posibles saltos de caballo
- Torre vs Caballo: si la torre se encuentra a 2 casillas en diagonal del caballo, lo limita en la disponibilidad de sus saltos
- Rey + Caballo vs Torre: la combinación rey caballo es superior a la torre para conseguir tablas siempre y cuando estas piezas no se separen a más de 1 salto del caballo
- Rey vs Caballo: Cuando el rey recibe un jaque por el caballo, se recomienda que se aleje de tal forma que exista una separación de 2 casillas en diagonal entre las piezas, por lo que el caballo tardaría 3 turnos en volver a dar jaque
- Rey vs Rey: Oposición, se dice que los reyes están en oposición cuando están a una casilla o a un número impar de casillas de separación, un rey gana la oposición cuando imita los movimientos del rey rival, imposibilitando su progreso en la posición o impiendo llegar a una parte del tablero
    * Ganar una oposición: cuando se es el rey que pierde la oposición, para revertirla se debe "invetir el orden de los turnos", es decir llegar a la misma posición pero el rey contrario ahora será quien pierda la opsición. Para ello se debe alejar una casilla (distancia de celdas par del rey) preferiblemente en diagonal, después avanzar una columna y luego avanzar una fila, de esta forma se revierte la oposición. El patrón de movimiento forma un triángulo rectángulo
- Rey vs Rey: En un final de peones, se recomienda que el Rey avance unas cuantas casillas en "Zig Zag (^, v)" si el rey contrario está lejos para ganarle la oposición
- Dama vs Rey: Colocar la dama a distancia de caballo "L" para acortar campo de movimiento, imitar el avance del rey para seguir acortando movilidad
- Dos Alfiles: Cuando se colocan uno a lado de otro, forman un triángulo por las diagonales, por lo que su dominio del tablero es muy fuerte
- Rey enrocado en Fianchetto: Colocar el rey al centro de los peones y avanzar algún peon de los extremos para fortalecer el enroque
- Dos Peones vs Rey: Cuando estos dos peones se encuentran separados y en fila, además el rey se encuentra entre ambos, si se forma un cuadrado imaginario entre los peones el rey NO logra detener la coronación de alguno de ellos, por el contrario si se forma un rectángulo sí logra detener las dos coronaciones

