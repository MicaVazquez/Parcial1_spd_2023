# Parcial1_spd_2023
<h2> Proyecto : Montacargas</h2>
<img src="./Img/Arduino.png" ><br>
<h2> Descripción</h2>
<p>EL proyecto es un modelo de montacargas que recibe ordenes de subir, bajar o pausar
desde diferentes pisos y muestre el estado actual del montacargas en el display 7 segmentos.</p>
<h2> Funcionamiento</h2>
<p>Se definen los pines utilizados para los pulsadores, los LEDs y los segmentos del display mediante #define. Por ejemplo, PULSADOR_BAJAR se define como el pin 13.

Se declaran variables para almacenar los estados de los pulsadores y los estados anteriores de los pulsadores. También se declara la variable estadoDelLed para almacenar el estado del LED rojo y la variable nivel para almacenar el nivel del montacargas.

Se declaran dos arreglos: elementos[] para almacenar los pines de los segmentos del display de siete segmentos y pulsadores[] para almacenar los pines de los pulsadores.

En la función setup(), se configuran los pines como entrada o salida utilizando la función pinMode(). Los pines de los segmentos del display se configuran como salidas, mientras que los pines de los pulsadores se configuran como entradas. Además, se inicia la comunicación serial a una velocidad de 9600 baudios y se llama a la función visualizacion() para mostrar el número 0 en el display.

En la función loop(), se realiza el control del montacargas y la detección de los pulsadores.

Primero, se lee el estado del pulsador de subir (PULSADOR_SUBIR) y se compara con el estado anterior (estadoAnteriorBotonSubir). Si hay un cambio en el estado del pulsador y el flag de pausa (flagPausa) es falso, se llama a la función subirMontacargas().

A continuación, se realiza lo mismo para el pulsador de bajar (PULSADOR_BAJAR) y se llama a la función bajarMontacargas() si hay un cambio de estado.

Luego, se lee el estado del pulsador de pausar (PULSADOR_PAUSAR) y se compara con el estado anterior (estadoAnteriorBotonPausar). Si el pulsador está presionado y el estado anterior está en bajo, se cambia el estado del LED verde (LED_VERDE) y se llama a la función pausarMontacargas() con el estado del LED como argumento.

Finalmente, se actualizan los estados anteriores de los pulsadores</p><br>
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
<h2> Link del proyecto </h2>
[Parcial 1 SPD](https://www.tinkercad.com/things/gzPuxQ7PXj4)

