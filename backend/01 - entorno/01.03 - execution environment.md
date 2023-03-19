# Entorno de ejecución
tags: #js #dsw
## Compilación de JavaScript
### V8
JavaScript nació como un lenguaje interpretado, siendo una de las causas principales de la lentitud de los sitios web con gran interacción con el usuario.

Debido a esto con el surgimiento del browser Chrome se incorporó V8 cuyo objetivo era compilar JavaScript y recurrir a la versión compilada al re-ejecutar el código. Este fue un gran avance en la performance que luego fue aplicado a los demás browsers.

### Node.js
Pero también abrió la posibilidad de combinar V8 con algunos módulos base para interactuar con el SO y convertirlo en entorno de ejecución de JavaScript. Esta idea llevó a Ryan Dahl a crear Node.js el primer entorno de ejecución de JavaScript de backend en 2009 utilizando V8 y su core fue escrito en C++.

### Deno
Luego, en 2018 el mismo Ryan Dahl decidió construir una reimplementación de Node.js con mejores prestaciones, más funcionalidades y más segura llamada Deno. Su motivación fue corregir muchas decisiones que fueron tomadas al crear Node.js. El mismo fue reescrito en rust en lugar de C++ haciéndolo más seguro. También, al ser más moderno, soporta novedades sobre el lenguaje que no existían al crear Node.js como TypeScript y un esquema de paquetes completamente diferente.

También se plantea como una alternativa, no como un reemplazo, siendo incompatible con el sistema de paquetes de Node.js  y al llegar muchos años después su "ecosistema" es aún pequeño en comparación con este. Sin embargo recientemente han empezado a soportar el sistema de paquetes de Node.js y aunque no todos los modulos funcionan aún con Deno su número va incrementándose

### Bun
En 2021 Jarred Sumner comienza el desarrollo de Bun. Una nueva alternativa a Node.js esta vez totalmente compatible siendo su intensión servir de reemplazo y agregar más y mejores funcionalidades. Incluye también soporte para TypeScript, JSX y gestión de paquetes, transpilación y gestor de paquetes y tareas.

Bun no utiliza V8, utiliza JavaScriptCore que es mucho más rápido y los módulos y componentes adicionales fueron desarrollados en Zig en lugar de C++ haciéndolo más seguro y performante. De hecho la performance de Bun es comparable o superior a la de lenguajes modernos de bajo nivel compilados.

Bun aún se encuentra en Beta, y no cuenta aún con proveedores de hosting pero al ser totalmente compatible con Node.js ya cuenta con excelente ecosistema disponible.

### Browsers
JavaScript es originalmente un lenguaje para ejecutar código en el Browser y es el principal lenguaje de frontend.

Los mismos no necesitan acceso a los módulos para interactuar con el pero deben ejecutar el código lo más rápido posible por lo que cuentan con algún runtime de JavaScript para hacer la compilación y ejecución. Por ejemplo Chrome y sus derivados utilizan V8, Firefox utiliza SpiderMonkey y Safari usa JavaScriptCore.

Aunque no ejecutaremos código de backend en un browser al ser JavaScript el principal (y prácticamente el único) lenguaje utilizado en el frontend las librerías de JavaScript de frontend son innumerables, algunas de las cuales deben poder funcionar en Backend como en Frontend. Esto significa que los runtime de los browsers y de backend deben ser compatibles hasta cierto punto.

### Uso en DSW
En DSW utilizaremos Node.js ya que es el runtime estable con el mayor ecosistema y material disponible para los alumnos.

Sin embargo una vez aprendido no debería representar un reto utlizar Deno o Bun.

## Versiones de Node.js
En cualquier lenguaje debemos considerar la versión del mismo a la vez que la versión del runtime o compilador.

Los lenguajes que activamente están siendo mejorados tienen cambios, mejoras y nuevas features con cada versión. Las mismas son acompañadas por nuevas versiones de su runtime o compilador.

### Causas de la complejidad
Normalmente los lenguajes solo deben ser compilados o interpretados en el compilador o runtime compatible con su versión. 

A los sumo el compilador o runtime debe ser capaz de interpretar algunas versiones del lenguaje no muy viejas del lenguaje y compilar correctamente ante los cambios entre versiones.

Pero el caso de JavaScript es particularmente complejo al respecto ya que el lenguaje debe ser ejecutado por múltiples browsers de distintos fabricantes que compiten entre si además del runtime de backend. 

A ello se suma que muchos navegadores son utilizados por muchos años aún después de que ya hay versiones más modernas y que muchos sitios web una vez completos no reciben actualizaciones de su código (esto incluye JavaScript).

### Retro-compatibilidad
Esto causa que para que los sitios web que utilizan JavaScript funcionen tan bien por tantos años, JavaScript debe ser retro-compatible hasta su primer versión. Esto es, cualquier código JavaScript correcto escrito en cualquier momento de su historia, es compatible con la versión actual. 

Las nuevas features deben agregarse mediante nueva sintaxis que no modifique la anterior para que los sitios web viejos sean compatibles con los browsers modernos sin fallar.

También estas nuevas features deberían poder implementarse mediante la sintaxis de versiones anteriores (esto se realiza generalmente mediante transpiladores, más adelante en el curso hablaremos de ellos). De esta forma las nuevas features podrían ejecutarse en browsers más antiguos o que aún no llegan a implementar las nuevas features pero que eventualmente lo harán.

### ECMA Script
Algo importante que no hemos mencionado aún es que unos años después de que se creara el lenguaje las versiones de JavaScript y sus nuevas features son de decididas por un comité de [ECMA](https://www.ecma-international.org) en el standar [ECMAScript](https://www.ecma-international.org/publications-and-standards/standards/ecma-262/) (ES), que es el nombre oficial de JavaScript.

No entraremos en detalles históricos pero si destacaremos que esto permite que los distintos browsers puedan competir libremente y las decisiones del lenguaje no dependan exclusivamente de una empresa u organización que tome decisiones unilaterales ni posea información anticipada.

Desde 2009 (ES5) se han realizado grandes revisiones del lenguaje siendo especialmente notable la versión de 2015 (ES6) que comenzó a incluir en el lenguaje importantes features que estaban siendo provistas por un sinnúmero de librerías y tecnologías de terceros pero que prácticamente todos los desarrolladores usaban o deseaban (clases, promesas, nuevas estructuras de datos, etc).

Cada año desde entonces JavaScript ha tenido mejoras constantes y las mismas son gradualmente implementadas en todos los runtimes y browsers.

*Nota*: Desde 2016 los estándares se numeran con el año en que son publicados. 

### JavaScript "flavors"
En la actualidad hay algunos lenguajes que son transpilados a JavaScript porque proveen funcionalidades que JavaScript carece o simplemente syntatic sugar. Estos no son versiones de JavaScript aunque transpilen a él.

De estos los más comunes y conocidos son **CoffeeScript**, **DART** y **TypeScript** siendo este último el más utilizado.

TypeScript a diferencia de los otros no ofrece una sintaxis alternativa a JavaScript, es un superset de JavaScript es decir que agrega nueva sintaxis a JavaScript que mejora las funciones del mismo. Es decir que cualquier código JavaScript puede ejecutarse como TypeScript ya que respeta el mismo. Más adelante en el curso cambiaremos de lenguaje a TypeScript.

## Gestores de version
Debido al rápido progreso del lenguaje y a la implementación de todas las nuevas features y sintaxis, constantemente querremos mejorar la versión del runtime que utilizamos pero los proyectos que ya hemos iniciado probablemente estén en una versión anterior y cuando debamos volver a modificar o fixear ese código necesitaremos utilizar la versión adecuada para continuar el desarrollo y reproducir errores.

También querremos utilizar features nuevas del lenguaje que probablemente no sean aún soportadas por todos los browsers o runtimes por lo que deberemos utilizar un polyfill mediante transpiladores que cambiarán nuestro código moderno por uno que realice lo mismo pero en una versión anterior del lenguaje cuando sea necesario.

Por ahora sólo comenzaremos con manejar la versión del runtime para el proyecto utilizando un gestor de versiones dejando para más adelante en el curso el tema de transpiladores y polyfill.

Los gestores de versiones son una aplicación o herramienta que permite instalar, remover, y seleccionar la versión a utilizar del runtime.

### Node.js Version Managers
Para poder utilizar distintos runtimes en cada proyecto se han utilizado muchas herramientas a lo largo del tiempo. Todos con enfoques ligeramente diferentes.

1. [n](https://github.com/tj/n)
2. [nvm](https://github.com/nvm-sh/nvm) / [nvm-windows](https://github.com/coreybutler/nvm-windows)
3. [volta](https://github.com/volta-cli/volta)
4. [fnm](https://github.com/Schniz/fnm)
7. otros (nodeenv, nodenv, etc)

**n** fue el primer gestor de versiones y es hasta la fecha el más simple por mucho. La ventaja principal es que es un paquete de Node.js lo que significa que puede instalarse como cualquier otro paquete (más de esto a continuación) pero esa también es su principal desventaja ya que hay que instalar Node.js y npm/yarn para utilizarlo. Además requiere normalmente bastante configuración para poder utilizarse correctamente en algunos IDEs o editores de código y no tener conflictos con la versión instalada originalmente. El cambio de versión es completamente manual, es decir el usuario debe cambiar la versión de node utilizada cuando lo necesita

**nvm** es la siguiente en aparecer, y es al día de hoy el más utilizado por mucho. Toma el enfoque de ser independiente de node y su gestor de paquetes. Resolviendo el problema de integración con otras herramientas. También implementa la idea de que el proyecto/repositorio cuente con la referencia a la versión utilizada de node y que esta se modifique de forma transparente con el usuario. Para esto utiliza un archivo `.nvmrc` en el directorio principal para identificar la versión deseada, aunque también puede usarse manualmente con `nvm use`. Las desventajas es que es un proceso un poco lento, sólo funciona en sistemas operativos POSIX (existe nvm-windows compatible pero es otra aplicación) y requiere una integración con el shell del sistema operativo para hacerlo transparente.

**volta** mucho más reciente y ganando popularidad apunta a resolver algunos inconvenientes de nvm. Al igual que nvm es una aplicación idependiente de node y npm resolviendo la integración con otras herramientas, es mucho más rápido que nvm, permite gestionar la versión de npm y yarn y define esta información junto con las dependencias de nuestro paquete y no en un fichero específico, a su vez es multiplataforma. Sus desventajas: no es compatible con nvm, la integración automática para cambiar de versión la realiza mediante un reemplazo del ejecutable de node (esto hace que sea completamente transparente a los IDEs y editores de código pero significa que no tenemos control sobre la versión a utilizar de manera directa), al momento tiene muchos issues abiertos en github algunos desde hace mucho tiempo.

**fnm** el más nuevo de los 4. Sin embargo ha ganado mucha popularidad recientemente, debido a que trata de integrar las ventajas de todos los anteriores, es independiente de node y npm, es tan rápido como volta, es multiplataforma, es compatible con nvm (fija la versión en un fichero .nvmrc o .node-version).

Es importante entender que se recomienda tener sólo uno de estos instalados a la vez para evitar conflictos

#### Uso en DSW
Desde la cátedra recomendamos el uso de alguno de estos sobre todo para los trabajos grupales donde utilizar la misma versión puede ser fundamental.

Si bien en los videos utilizaremos fnm no requerimos el uso de uno en particular. Se recomienda el uso del mismo (o de algunos compatibles entre si fnm/nvm/nvm-windows) entre los integrantes del mismo grupo.

## Gestor de paquetes
En todos los lenguajes de programación existe la posibilidad de utilizar paquetes o librerías hechos por terceros (dependiendo del lenguaje pueden llamarse de otra forma: crates, gems, jars, etc.)

Buscar e instalar estas librerías manualmente puede ser tedioso, consumir tiempo y propenso a fallas. A su vez coordinar la versión entre distintos miembros del equipo y mantenerla actualizada puede ser un problema y utilizar diferentes versiones puede ser causa de bugs inesperados y fallas entre los miembros de un mismo equipo.

Para resolver este problema la mayoría de los lenguajes modernos de programación cuentan con un gestor de paquetes o gestor de dependencias (ya que nuestro proyecto depende de estas librerías) para gestionar esto. Suelen tener una o más listas de dependencias lo que simplifica enormemente esta tarea.

La mayoría de los lenguajes tiene una herramienta indepediente para ello (aunque en el caso de Deno y Bun se encuentra integrada al ejecutable del runtime).

### npm
Más adelante en el curso volveremos a profundizar sobre los paquetes y los gestores, para nodejs el gestor de paquetes histórico y el más usado es [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) que resultó en un sistema de dependencias que ha sido copiado y trasladado a multiples lenguajes de programación resolviendo problemas que tenían en sus propios gestores. Es extremadamente simple, rara vez tiene problemas o require configuración y es muy robusto.

### yarn
Un tiempo después apareció [yarn](https://yarnpkg.com) que es fundamentalmente diferente e incompatible con npm pero ofrecía ciertas funcionalidades adicionales a npm y mejor performance. Sin embargo su falta de interoperabilidad ha evitado que suplante a npm por ahora.

### pnpm
Recientemente se ha incrementado el uso de [pnpm](https://pnpm.io/installation), una alternativa más performante y hace uso más eficiente de disco que npm y compatible con el funcionamiento de npm aunque no idéntico. Aún no funciona con todos los paquetes y tipos de proyecto y puede requerir un poco de configuración para su uso e integración con los IDEs y editores de código.
Sin embargo a pesar de ello su uso no para de crecer y mejorar ya que la mejora de performance y uso de disco son más que significativas.

### Uso en DSW
En la cátedra utilizaremos pnpm principalmente por su compatibilidad directa con npm que es la opción más utilizada pero por su eficiencia en el uso de disco así como la performance a la hora de instalar nuevos paquetes, pero los alumnos pueden optar por utilizar npm y no deberían tener inconvenientes al respecto.