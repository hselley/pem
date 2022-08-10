# Introducción a la programación estructurada

## Paradigmas de programación
Los lenguajes de programación han evolucionado y se han creado nuevos paradigmas
que tienen como objetivo resolver nuevos tipos de problemas.

1. Programación procedural
2. Programación modular
3. Abstracción de datos
4. Programación orientada a objetos
5. Programación genérica

### Programación procedural
Este paradigma se basa en la creación de funciones o procedimientos como nuevas operaciones.

Cuando los programas comienzan a ser más complejos, no es sencillo resolver el problema como
una única función. En el desarrollo del software se estudian las tareas que queremos tener
resueltas para el problema, y se implementan los algoritmos correspondientes como funciones
o procedimientos. 

Estas funciones ocultan los detalles del algoritmo que implementan, y ofrecen la posibilidad de 
utilizarlo en base a una interfaz bien definida. 

Por ejemplo, podemos definir una función que contiene todos los pasos necesarios para obtener
la raíz cuadrada de un parámetro de doble precisión en punto flotante.

```
double raizCuadrada(double x) {
    // Código para resolver la raíz cuadrada
}
```
Así, una llamada a la operación sólo necesita conocer la interfaz, obviando los detalles internos.

Con respecto al diseño procedural, Dijkstra y otros propusieron utilizar un conjunto de construcciones
lógicas limitadas, concretamente la *secuencia*, la *condición* y la *repetición* al desarrollar 
un programa. De esta forma, una función sólo tiene una entrada y una salida. Además, cada una de 
las tareas a realizar puede anidarse, es decir, una tarea puede ser otro conjunto de tareas y estructuras
de control con una única entrada y salida (podemos considerar este anidamiento como la estructura
del programa en procedimientos).

Finalmente, conviene destacar, que un ejemplo dogmático de estas construcciones puede implicar una 
pérdida de eficiencia y complicar el código.


### Programación modular
Cuando el problema se hace muy complejo, es recomendable dividirlo en subproblemas para que sea más fácil 
de resolver. Así podemos enfrentarnos a la búsqueda de soluciones para éstos, y que unidas, podrán 
ofrecernos el programa que deseamos.

La programación modular se basa en la creación de unidades, denominadas módulos, y que corresponden
a un conjunto de procedimientos y de datos relacionados entre sí. Nótese que una función o procedimiento
lo podemos considerar un módulo simple. 

Cuando se desarrolla un módulo, es necesario también definir la interfaz para acceder a su funcionalidad.
Lógicamente, todos los detalles, funciones o datos que son necesarios para la interfaz, se pueden
obviar a la hora de utilizarlo. Así, en un módulo podemos encontrar datos y funciones ocultas en 
el sentido de que no se utilizan, más que para el funcionamiento interno del módulo.

Por ejemplo, el lenguaje C++ ofrece:

* **Compilación separada**. Permite dividir el código en distintos archivos. De esta forma 
    podemos agrupar los datos y procedimientos asociados según su almacenamiento físico. Podemos
    considerar dos tipos de archivos, los que almacenan la interfaz o cabecera (extensión *.h*) y 
    otros con las definiciones (con extensión *.cpp*).

* **Espacios de nombres**. Permite indicar que un conjunto de indicadores están relacionados, 
    asignandoles un espacio de nombres (*namespace*). Posteriormente, para utilizar alguno de ellos,
    necesitamos especificar el espacio al que pertenece, anteponiendo el nombre del *namespace*
    con el separador *::*. Por ejemplo, para usar *cout*, se necesita indicar que está dentro de *std*,
    por lo tanto en el código se debe indicar *std::cout*.


### Abstracción de datos
Hasta ahora, nos hemos centrado en los algoritmos y como nos enfrentamos a su creciente dificultad.
Sin embargo, cuando los problemas a resolver son más complicados, las estructuras de datos también
son más complejas. 

La solución a un problema puede implicar el manejo de una compleja estructura de datos que representa
algún tipo de información en nuestro problema. Si al algoritmo añadimos la posible complejidad de los
detalles de esta estructura, puede resultar más difícil, y con un programa resultado de peor calidad.

Para aliviar estos problemas se propone el uso de la abstracción de datos. La idea básica consiste
en desarrollar un módulo que resuelva los problemas de manejo de esa estructura, ocultando todos
los detalles innecesarios por medio de una interfaz sencilla que ofrezca la funcionalidad que 
necesitamos para nuestros algoritmos.

La forma más cómoda para usar la abstracción de datos es la definición de un nuevo tipo de dato, con
una interfaz adecuada y que tenga un comportamiento idéntico a los tipos predefinidos del lenguaje.

Por ejemplo, si desarrollamos un programa para tratamiento matemático y necesitamos manejar
polinomios, puede resultar engorroso arrastrar todos los detalles de su implementación a lo largo
de los algoritmos. Es más sencillo disponer de un tipo *Polinomio* que nos ofrezca la funcionalidad
que necesitamos, por ejemplo, sumas, restas, productos, evaluación, etc. en una interfaz bien
definida, para la que no es necesario conocer cómo se ha representado en una estructura de datos.

El lenguaje C++ ofrece la posibilidad de crear nuevos tipos de datos mediante la creación de 
una *clase* y los mecanismos necesarios para su utilización, como los constructores para inicializar
las variables, un método para implementar la forma de copiar un objeto, sobrecarga, etc.


### Programación orientada a objetos
En las secciones anteriores la discusión se ha basado en un modelo en el que los datos y los algoritmos
se manejan de forma independiente, por un lado tenemos los datos que trata el problema y por otro
los algoritmos que los transforman. En este sentido, podemos decir que eran soluciones orientadas
a al flujo de datos.

Para poder implementar las soluciones de los modelos orientados a objetos, los lenguajes soportan 
este paradigma de programación basándose en los siguientes principios:

1. Encapsulamiento
2. Herencia
3. Polimorfismo

El encapsulamiento nos permite combinar los datos y las operaciones en un miso objeto, de forma
que éste ofrezca una interfaz de comunicación para relacionarse con otros objetos, haciendo inaccesibles
todos los detalles internos de su funcionamiento.

La herencia es un mecanismo que permite indicar que una clase de objetos hereda las propiedades de
otra. Por ejemplo, podemos tener un sistema de gestión en el que hay que procesar los datos de los 
empleados. Para ello podemos crear una clase de objetos *empleado*. En ésta, se resuelven los problemas
comúnes de cualquier empleado. Por ejemplo, se almacenan datos personales, tiene operaciones para
calcular la antigüedad del empleado, etc.

Ahora bien, si queremos añadir un nuevo tipo de objeto, por ejemplo *Directivo*, no es necesario
indicar que, para esta clase de objetos, hay que almacenar datos personales, fecha de incorporación, 
etc. Sólo tenemos que indicar en el programa que hereda las propiedades de un *empleado*. Así, 
con esa operación tan simple, ya disponemos de un objeto con todos los datos y operaciones que
se habían definido para *empleado*, ahora sólo se deben modificar las diferencias.

El *polimorfismo* permite que un objeto determine, en tiempo de ejecución, la operación a realizar.
Por ejemplo, supongamos que un sistema de diseño gráfico para el que tenemos un conjunto de objetos,
tales como: *circunferencia*, *rectángulo* y *triángulo*. Todos ellos tienen área, por lo tanto
pueden tener una operación para calcular y devolver su valor. Imaginemos que queremos una función 
para escribir en pantalla el área de una *figura*, siendo cualquiera de las anteriores mencionadas.
El polimorfismo permite definir una única función que, tomando como parámetro *figura*, escribe
en pantalla su área.

Por supuesto, en tiempo de ejecución la función llamará a la operación correspondiente dependiendo
del tipo de figura.

### Programación genérica
En programación existen múltiples algoritmos que se repiten continuamente, y que por tanto, es
necesario implementar para distintos tipos de datos o entornos de programación. Por ejemplo, en 
un programa podemos necesitar un algoritmo de ordenación de números enteros y de números flotantes.
El algoritmo es idéntico, aunque en muchos lenguajes será necesario disponer de dos funciones para
resolverlo.

La programación genérica hace referencia a la implementación de algoritmos para aplicarlos en múltiples
ocasiones. En lugar de construir un algoritmo particular para cada caso, es posible especificar
un algoritmo general compuesto de todos los pasos comunes a cada una de las implementaciones, y que
el lenguaje nos permitirá aplicar para todos los casos. Como es de esperar, el único requisito
es que cada paso del algoritmo general sea compatible con cada tipo particular.

La programación genérica es una técnica para la *reutilización*, que es un concepto muy importante
en la mejora de la productividad y la calidad del software. 

### Desarrollo de programas
En la actualidad podemos considerar fundamentalmente, dos tendencias en el desarrollo de software:

1. *Análisis y diseño estructurado*. El sistema se modela con un enfoque orientado al flujo de 
datos. Se pueden aplicar los paradigmas de programación procedural, modular, abstracción de datos
e incluso programación genérica para el desarllo de software.

2. *Análisis y diseño orientado a objetos*. El sistema se modela con un enfoque orientado a objetos
y se utiliza el paradigma orientado a objetos.

## Características de la programación estructurada
## Codificación, depuración y compilación
## Enlace, carga y ejecución de programas
