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

