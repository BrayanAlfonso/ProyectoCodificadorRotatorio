# ProyectoCodificadorRotatorio

Este codigo consiste en utilizar el codificador rotatorio haciendo una prueba para que detecte la rotación del mismo y nos vaya imprimiendo en el monitor serial numeros del 0 al 100 empezando por el 50. Ahora la explicación del codigo, primero declaraos dos variables A y B, las cuales usaremos para el pin 2 y 4 respectivamente, posteriormente declaramos una variable llamada anterior que usaremos para guardar el ultimo valor almacenado en la variable posicion, estara por defeco en 50 y por ultimo declaramos la variable Posicion la cual servira para saber la posicion en la que se encuetra el codificador rotatorio iniciando en la posicion 50, la declaramos como volatile para hacerla global y poderla usar en todo el codigo. Ahora en el setup creamos con el pinMode los pines A y B que ambos seran como entrada y también creamos el monitor serial, posetriormente hacemos un attachInterrupt en el que especificamos que en el momento en el cual el pin A se vea interrumpido por el giro del codificador es decir su voltaje sea LOW, se ejectura la funcion encoder e imprimiremos en el monitor serial "Listo".

Ahora en el loop haremos un condicional que nos imprima el valor de Posicion e igualara el valor de posicion a la variable anterior siempre y cuando el valor de la variable posicion sea diferente al valor de la variable anterior. Casi para finalizar creamos la funcion llamada encoder en la cual declaramos dos variables que nos ayudaran a calcular el tiempo entre interrupciones, la primera, ultimaInterrupcion inicializada en 0 y unsigned long que nos permitira usar los 32 bits de almacenamiento que tiene el tipo de dato long ya que el numero almacenado en esta variable sera muy largo acompañado de un static que nos permitira que la variable no se borre al finalizar la función, en esta es donde vamos a guardar el valor de la segunda variable antes de salir de la funcion, y hablando de la segunda variable esta calculara el tiempo en milisegundos por medio de la funcion millis desde que se inicaliza el programa hasta que ocurre una interrupción. Posetriormente haremos un condicional para evitar rebotes, en la condicion calcularemos el tiempo entre la ultima interrupcion y la actual haciendo la operacion de restar el valor en la variable tiempoInterrupción menos el valor en la variable ultimaInterrupción con este resultado comparamos si es mayor a 5, si no lo es significa que es un rebote y no lo cuenta, si la condicion se cumple entra al condicional donde hay otro condicional que nos dice que si el pin numero B esta en alto nos restara uno a la variable posicion, es decir que esta en sentido anti horario y si por el contrario es bajo, le sumara 1 a la variable posicion es decir que esta girando en sentido horario despues de este condicional definimos el limite minimo y maximo que podra tener la variable posicion que sera entre 0-100 y por ultimo le asignamos el valor de la variable tiempoInterrupcion a la variable ultimaInterrupcion repetir el condicional con el nuevo tiempo de interrupción.
