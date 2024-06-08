# Luck in RPGs: Talent vs Effort with PowerBI

## Objetivo
Este pequeño proyecto tiene como finalidad el demostrar mi capacidad de usar herramientas de visualización tan potentes como PowerBI y cómo esta herramienta, en conjunto con mis habilidades analíticas dado mi trasfonodo como científico puede permitirme estudiar un problema donde las instrucciones son mínimas y, a partir de la deducción, obtener resultados aprovechables con los cuales el cliente esté satisfecho.

## Habilidades desarrolladas
1. Visualizaciones con PowerBI
2. Estadística
3. Deducción lógica y científica
4. Resolución de problemas
5. Análisis de datos
6. Explicación de resultados a audiencias no técnicas

## Desarrollo del proyecto

## Contexto
Nuestro cliente quiere hacer un videojuego del género RPG donde casi todas las acciones que se realizan dependan de cómo se construye el personaje. Sin embargo, como no quiere que la aleatoriedad juegue un papel demasiado importante (quiere que haya un elemento de fortuna, pero que este esté contenido), nos pide que descubramos qué tipo de tiradas debe hacer el motor del juego. Para ello nos explica cómo se construyen los personajes, habiendo una enorme libertad de personalización, y cómo insteractuaría con el mundo. Por último, nos ha pedido que los resultados se los presentemos haciendo uso de PowerBI, pues es una herramienta con la que está muy familiarizado y le resulta más sencillo leer los datos con esta.

### Consideraciones previas.
- El cliente solo nos ha dicho "quiero reducir el factor azar en las tiradas"
- Se le ha preguntado al cliente cómo funciona la creación de personajes y cómo funcionan los dados para comprender mejor el funcionamiento del juego.
- El cliente no posee conocimientos profundos en estadística, solo una base que le permite entender los gráficos

### Funcionamiento del sistema
La creación de personajes está muy inspirada en juegos de rol de mesa como Dungeons&Dragons (D&D), pudiendo distribuir una serie de puntos entre distnitos atributos (Fuerza, Resistencia, Velocidad,... el cliente lo llama "Talento") y elegir una serie de habilidades con distintos niveles de mejora (Escalar, correr, atacar,... el cliente lo llama "Habilidad"). 

Las atributos podrán tener un vaor numérico que va del 1 al 10, mientras que las habilidades tendrán un valor comprendido entre 1 y 5.

Inicialmente, el cliente había pensado en usar el mismo sistema que usa D&D, donde se tira un dado de 100 caras que va bonificado por distintos parámetros, pero en tanto que ello es muy dependiente de la suerte, quiere cambiarlo a otro método que le permita reducir esa dependencia. Para ello, se proponen 2 métodos distintos:
1. Talento-Habilidad (TdH)
2. Habilidad-Talento (HdT)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<b>¿Cómo funcionan estas tiradas de dados?</b>

Una tirada de dados se compone de 2 parámetros diferentes, el número de dados (A) y el número de caras de ese dado (B). Si tomamos el parchís como nuestro juego de referencia, en cada tirada debemos lanar 2 dados de 6 caras (AdB = 2d6). En los juegos de rol, sin embargo, esto se lleva al extremo, usando por ejemplo un dado de 100 caras (1d100) al cual se le añaden valores fijos (+X) para aumentar el resultado (1d100+X), donde X puede ser un bono que dependa de cualquier cosa que desee el creador del juego.

Hay otros juegos, como Cuthulhu Tech, que modifican el dado en acuerdo a los atributos del personaje y el número de veces que han comprado una misma habilidad. Nosotros hemos propuesto un método similar a este último.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Para el primer caso, tendremos un énfasis en el número de tiradas que hacemos, pues T puede llegar a tener hasta 10 valores distintos, mientras que H solo llega a 5. En el segundo tendremos lo contrario, menos tiradas (hasta 5 dados), pero más caras por dado (hasta 10 caras). Cada uno de los métodos propuestos tiene una serie de peculiaridades, en las cuales no se entra para no volver muy compleja la explicación.

### Obtención, carga y Visualización de datos
Para obtener los datos necesarios, basta con tirar una serie de X dados con un número de Y caras las suficientes veces para tener una estadística buena. Para ello vamos a usar Excel, diciéndole que escoga un número aleatorio comprendido entre el menor y el mayor resultado posible de la tirada. Una vez haga un número suficiente de tiradas, le diremos que nos calcule el promedio y la desviación estándar. La figura 1 nos muestra la tabla de datos que hemos obtenido siguiendo este procedimiento. 

Podríamos haber hecho esto con Python, por ejemplo, creando un bucle for. Pero por simplificar el proyecto, se ha optado por usar Excel.

![image](https://github.com/JoseManuelMdlV/Luck-in-RPGs-Talent-vs-Effort-with-PowerBI/assets/83475119/3f7bfbd7-5155-4e00-abe6-04114ed2ce1a)

<b>Fig. 1:</b> Primer set de datos obtenidos usando los comandos propios de Excel.

Con los datos obtenidos, los cargamos en PowerBI y creamos un gráfico de barras donde el Eje horizontal ordene los resultados en 2 bloques distintos: el primer bloque, el exterior, ordena los resultados por el valor del atributo del personaje; el segundo, el interno, los ordena en acuerdo al nivel de la habilidad del personaje. De esta manera, podremos ver la evolución en acuerdo a ambas variables. El eje vertical nos muestra el resultado promedio de las tiradas, dibujando también las barras de error para poder ver la desviación estándar.

* La desviación estándar (error a partir de ahora), dicho rápido y mal, es la diferencia que hay entre los valores máximo y mínimo de una muestra con respecto al promedio. No es exactamente asi, pero como definición para andar por casa nos sirve. La idea es que este valor sea lo más pequeño posible.

En la figura 2 se muestra el gráfico con todos los resultados obtenidos, donde se puede apreciar que las barras muestran el comportamiento esperado inicialmente. No obstante, como este gráfico puede ser un poco engorroso de leer incluso para los ojos más acostumbrados, vamos a hacer uso de las opciones que nos da PowerBI y vamos a filtrar los resultados para que el gráfico nos muestre solo los resultados con un valor de nivel de habilidad concreto. 

![image](https://github.com/JoseManuelMdlV/Luck-in-RPGs-Talent-vs-Effort-with-PowerBI/assets/83475119/7ff7ea81-1646-45a2-a65a-ebe32f793f90)

<b>Fig.2:</b> Visualización de todos los datos cargados de la hoja de Excel de la Fig.1

Para la Figura 3, hemos escogido un nivel de habilidad 1 y hemos visto lo que ocurre tanto cuando tenemos tiradas de la forma Td1 (en color rojo), como de la forma 1dT (color azul). En este caso, ocurre justo lo que tiene que ocurrir, que es que las tiradas Td1 no tienen error (en este caso siempre estamos sumando un valor único (1) un número T de veces) y las tiradas 1dT tienen un error asociado que se va haciendo mayor en tanto aumenta el número de caras del dado. El caso contrario, tiradas de la forma 1dH y Hd1, arrojan resultados similares a la inversa de los mostrados en la figura 3.

![image](https://github.com/JoseManuelMdlV/Luck-in-RPGs-Talent-vs-Effort-with-PowerBI/assets/83475119/548c0f1f-0d32-402c-903d-c7f8bc7a97fa)

<b>Fig.3:</b> Comparativa de las tiradas 1dT (azul) y Td1 (rojo)

Hecha esta pequeña comprobación para ver que los datos son correctos y se comportan como deben, vamos viendo uno por uno los distintos resultados, viendo cuál es aquel que tiene un error menor. Para eso se confeccionan las tablas 1a (izquierda) y 1b (derecha), donde se recogen los promedios y desviaciones de los dos tipos de tiradas propuestos fijando un valor u otro. 

![image](https://github.com/JoseManuelMdlV/Luck-in-RPGs-Talent-vs-Effort-with-PowerBI/assets/83475119/3c5fbadc-305f-45e4-80f6-cee8e2d676ae)

<b>Tabla 1:</b> Valores y desviación estándar de las tiradas TdH y HdT con H fijo (izquierda) y T fijo (derecha)

Mirando los resultados de las tablas, se puede inferir que la mejor solución será usar una serie detiradas TdH, donde el atributo del personaje defina el número de dados a utilizar y el nivel de habilidad el número de caras. La tabla 1a quizás no lleve de forma natural a esa conclusión dado que si nos fijamos solo en los valores del error, la diferencia entre los pares de valores se van haciendo cada vez más pequeños. Si miramos la tabla 1b, el resultado se vuelve más obvio, pues a partir de un valor de atributo 5, los valores de TdH se hacen mayores que los de HdT, manteniendo unas dispersiones más controladas.

Podríamos decir, por tanto, que lo mejor es usar el primer método propuesto, señalándole al cliente que, además de tener una menor error, tendrá resultados consistentemente más altos que con el segundo método. 

Esto es, sin embargo, el resultado de una prueba. Lo ideal sería repetir este mismo procedimiento otras dos veces para comprobar si se reproducen los resultados de forma consistente. Para ello, vamos a repetir las tiradas de dados haciendo otros dos sets, guardamos el promedio de cada set de tiradas y hacemos el promedio de los tres promedios y vemos su desviación estándar. Con ello, conseguiremos unos datos con un grado de prpecisión muy altos que nos permitirán, ahora sí, poder dar una respuesta mucho más certera (siempre y cuando las desviaciones no sean muy grandes. En cuyo caso habríamos de repetir con otros dos sets más)

El resultado es lo que vemos en la figura 4, de nuevo una imagen panorámica de los resultados que se han obtenido, donde poco se puede inferir más que el hecho de que las barras de error ahora son notoriamente más pequeñas. Esto ayuda bastante incluso en la vista general a apreciar que el error para las tiradas TdH es menor que el de las tiradas HdT, lo cual refuerza lo que ya habíamos advertido anteriormente.  

![image](https://github.com/JoseManuelMdlV/Luck-in-RPGs-Talent-vs-Effort-with-PowerBI/assets/83475119/f9de8d9b-b0a3-4568-9bfa-5cdd029f6e24)

<b>Fig. 4:</b> Promedio de los sets de datos obtenidos

Si repetimos la operación anterior con la que obtuvimos las tablas 1a y 1b, podemos obtener un par de tablas similares (Tabla 2a y 2b) donde podamos ver de manera inmediata cómo crecen los resultados de las tiradas y el error.

![image](https://github.com/JoseManuelMdlV/Luck-in-RPGs-Talent-vs-Effort-with-PowerBI/assets/83475119/88396b15-b182-49c4-8a15-8ade4fd2d233)

<b>Tabla 2:</b> Valores y desviación estándar de los promedios de las tiradas TdH y HdT con H fijo (izquierda) y T fijo (derecha)

El análisis es similar al que se hizo para el primer par de tablas, con la tabla 2b mostrándonos mucho mejor la evolución tanto de los valores como de los errores, pudiendo concluir, ahora sí, que el mejor método para poder minimizar la influencia del azar es el primer método propuesto. 
