# Parcial1_spd_2023
<h2> Proyecto : Montacargas</h2>
<img src="./Img/Arduino.png" ><br>
<h2> Descripción</h2>
<p>EL proyecto es un modelo de montacargas que recibe ordenes de subir, bajar o pausar
desde diferentes pisos y muestre el estado actual del montacargas en el display 7 segmentos.</p>
<h2> Funciones </h2>
<ul>
<li>La función display() se utiliza para controlar los segmentos del display de siete segmentos. Recibe como argumentos los valores de los segmentos (0 o 1) y utiliza la función digitalWrite() para establecer los valores correspondientes en los pines de los segmentos.</li>
<li>La función visualizacion() recibe un número como argumento y muestra ese número en el display de siete segmentos llamando a la función display() con los valores de segmentos correspondientes al número.</li>
<li>void subirMontacargas(): Esta función se encarga de subir el montacargas al siguiente nivel. Incrementa la variable nivel en uno y luego verifica si el nivel supera el valor máximo permitido (9). Si es así, establece nivel en 9, muestra el número 9 en el display llamando a la función visualizacion(), imprime un mensaje en la comunicación serial indicando que solo se puede subir hasta el nivel 9. En caso contrario, muestra el número actual del nivel en el display, enciende el LED verde utilizando digitalWrite(), imprime el número del nivel actual en la comunicación serial, espera 3 segundos utilizando delay(), apaga los segmentos del display llamando a display() con valores de segmento apagados, y finalmente apaga el LED verde.</li>
<li>void bajarMontacargas(): Esta función se encarga de bajar el montacargas al nivel anterior. Decrementa la variable nivel en uno y luego verifica si el nivel es menor que cero. Si es así, establece nivel en 0, muestra el número 0 en el display llamando a la función visualizacion(), e imprime un mensaje en la comunicación serial indicando que solo se puede bajar hasta el nivel 0. En caso contrario, muestra el número actual del nivel en el display, enciende el LED verde utilizando digitalWrite(), imprime el número del nivel actual en la comunicación serial, espera 3 segundos utilizando delay(), apaga los segmentos del display llamando a display() con valores de segmento apagados, y finalmente apaga el LED verde.</li>
<img src="./Img/LedVerde.png" ><br>
  <p>Así se ve cuando se encuentra en movimiento</p>
<li>void pausarMontacargas(int estadoDelLed): Esta función se encarga de pausar o reanudar el montacargas. Recibe el estado del LED rojo como argumento (estadoDelLed). Si estadoDelLed es igual a 1, se enciende el LED rojo utilizando digitalWrite(), se imprime un mensaje en la comunicación serial indicando que el montacargas está en pausa, y se establece flagPausa en TRUE. Si estadoDelLed es diferente de 1, se apaga el LED rojo, se imprime un mensaje en la comunicación serial indicando que el montacargas está activo, y se establece flagPausa en FALSE. Esta variable flagPausa se utiliza para controlar si se permite o no el movimiento del montacargas en las funciones de subir y bajar, evitando que se mueva mientras está en pausa.</li>
<img src="./Img/LedRojo.png" ><br>
  <p>Así se ve cuando se encuentra pausado</p>
</ul>
<h2> Link al proyecto</h2>

