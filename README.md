# Luck in RPGs: Talent vs Effort with PowerBI

## Contexto
Nuestro cliente quiere hacer un videojuego del género RPG donde casi todas las acciones que se realizan dependan de cómo se construye el personaje. Sin embargo, como no quiere que la aleatoriedad juegue un papel demasiado importante (quiere que haya un elemento de fortuna, pero que este esté contenido), nos pide que descubramos qué tipo de tiradas debe hacer el motor del juego. Para ello nos explica cómo se construyen los personajes, habiendo una enorme libertad de personalización, y cómo insteractuaría con el mundo. Por último, nos ha pedido que los resultados se los presentemos haciendo uso de PowerBI, pues es una herramienta con la que está muy familiarizado y le resulta más sencillo leer los datos con esta.

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
### Consideraciones previas.
- El cliente solo nos ha dicho "quiero reducir el factor azar en las tiradas"
- Se le ha preguntado al cliente cómo funciona la creación de personajes y cómo funcionan los dados para comprender mejor el funcionamiento del juego.
- El cliente no posee conocimientos profundos en estadística, solo una base que le permite entender los gráficos

### Funcionamiento del sistema
La creación de personajes está muy inspirada en juegos de rol de mesa como Dungeons&Dragons (D&D), pudiendo distribuir una serie de puntos entre distnitos atributos (Fuerza, Resistencia, Velocidad,... el cliente lo llama "Talento") y elegir una serie de habilidades con distintos niveles de mejora (Escalar, correr, atacar,... el cliente lo llama "Esfuerzo"). 

Las atributos podrán tener un vaor numérico que va del 1 al 10, mientras que las habilidades tendrán un valor comprendido entre 1 y 5.

Inicialmente, el cliente había pensado en usar el mismo sistema que usa D&D, donde se tira un dado de 100 caras que va bonificado por distintos parámetros, pero en tanto que ello es muy dependiente de la suerte, quiere cambiarlo a otro método que le permita reducir esa dependencia. Para ello, se proponen 2 métodos distintos:
1. Talento-Esfuerzo (TdE)
2. Esfuerzo-Talento (EdT)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<b>¿Cómo funcionan estas tiradas de dados?</b>

Una tirada de dados se compone de 2 parámetros diferentes, el número de dados (A) y el número de caras de ese dado (B). Si tomamos el parchís como nuestro juego de referencia, en cada tirada debemos lanar 2 dados de 6 caras (AdB = 2d6). En los juegos de rol, sin embargo, esto se lleva al extremo, usando por ejemplo un dado de 100 caras (1d100) al cual se le añaden valores fijos (+X) para aumentar el resultado (1d100+X), donde X puede ser un bono que dependa de cualquier cosa que desee el creador del juego.

Hay otros juegos, como Cuthulhu Tech, que modifican el dado en acuerdo a los atributos del personaje y el número de veces que han comprado una misma habilidad. Nosotros hemos propuesto un método similar a este último.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Para el primer caso, tendremos un énfasis en el número de tiradas que hacemos, pues T puede llegar a tener hasta 10 valores distintos, mientras que E solo llega a 5. En el segundo tendremos lo contrario, menos tiradas (hasta 5 dados), pero más caras por dado (hasta 10 caras). Cada uno de los métodos propuestos tiene una serie de peculiaridades, en las cuales no se entra para no volver muy compleja la explicación.

### Obtención, carga y Visualización de datos
Para obtener los datos necesarios, basta con tirar una serie de X dados con un número de Y caras las suficientes veces para tener una estadística buena. Para ello vamos a usar Excel, diciéndole que escoga un número aleatorio comprendido entre el menor y el mayor resultado posible de la tirada. Una vez haga un número suficiente de tiradas, le diremos que nos calcule el promedio y la desviación estándar. La figura 1 nos muestra la tabla de datos que hemos obtenido siguiendo este procedimiento. 

Podríamos haber hecho esto con Python, por ejemplo, creando un bucle for. Pero por simplificar el proyecto, se ha optado por usar Excel.

![image](https://github.com/JoseManuelMdlV/Luck-in-RPGs-Talent-vs-Effort-with-PowerBI/assets/83475119/3f7bfbd7-5155-4e00-abe6-04114ed2ce1a)

<b>Fig. 1</b> Primer set de datos obtenidos usando los comandos propios de Excel.

Con los datos obtenidos, los cargamos en PowerBI y creamos un gráfico de barras donde el Eje horizontal ordene los resultados en 2 bloques distintos: el primer bloque, el exterior, ordena los resultados por el valor del atributo del personaje; el segundo, el interno, los ordena en acuerdo al nivel de la habilidad del personaje. De esta manera, podremos ver la evolución en acuerdo a ambas variables. El eje vertical nos muestra el resultado promedio de las tiradas, dibujando también las barras de error para poder ver la desviación estándar.

* La desviación estándar (error a partir de ahora), dicho rápido y mal, es la diferencia que hay entre los valores máximo y mínimo de una muestra con respecto al promedio. No es exactamente asi, pero como definición para andar por casa nos sirve. La idea es que este valor sea lo más pequeño posible.

En la figura 2 se muestra el gráfico con todos los resultados obtenidos, donde se puede apreciar que las barras muestran el comportamiento esperado inicialmente. No obstante, como este gráfico puede ser un poco engorroso de leer incluso para los ojos más acostumbrados, vamos a hacer uso de las opciones que nos da PowerBI y vamos a filtrar los resultados para que el gráfico nos muestre solo los resultados con un valor de nivel de habilidad concreto. 
