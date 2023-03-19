# Control de código fuente
tags: #scm #dsw #scm #vcs
## Definición
El control de código fuente (también llamado control de la versión) es la práctica de seguimiento y administración de los cambios en el código. Los sistemas de administración de código fuente (SCM) mantienen un historial del desarrollo de código, y ayudan a resolver conflictos a la hora de combinar las contribuciones (cambios en el código) de diferentes orígenes (multiples desarrollos paralelos).

## Usos
SCM tiene múltiples usos, ya sea en desarrollos individuales pero más aún en equipos.

El SCM permite entre otras cosas:
* **Backup e historial de los cambios**. Registra que se modificó en cada archivo, cuando, quien, etc.
* **Comparación**. Además de tener una copia histórica de nuestro código a la que podemos volver en cualquier momento (y no por esto perder el código ya modificado) si no que automáticamente podemos comparar las diferencias entre distintas versiones.
* **Desarrollar cambios en paralelo**, es decir que una misma persona puede trabajar en dos proyectos de modificación en paralelo sin afectar uno con otro. Por ejemplo mientras se rediseña una interfaz de usuario, a mitad del proceso se detecta un bug crítico. Se pueden guardar los cambios hasta el momento y comenzar un desarrollo en paralelo desde un código que no tiene la interfaz a medio desarrollar, terminar de fixear el código para resolver el bug y luego se puede combinar con el código del rediseño de interfaz, ya sea al finalizarlo o en medio del desarrollo según convenga.

Hay muchos conceptos de SCM más avanzados pero esos ya depende de que software se utilice. El más utilizado por mucho margen es [**git**](https://git-scm.com) y con justa razón. Las ventajas (ya sean de las funcionalidad, simplicidad, performance o simplemente el ecosistema de aplicaciones y soluciones para los desarrolladores) sobre las demás alternativas son tantas que es casi imposible compararlo.

## git
git es un SCM distribuido, es decir que no requiere un repositorio central. Cada desarrollador cuenta con un repositorio propio y puede compartir con otros sus cambios en el código a voluntad, y el desarrollador que recibe estos cambios puede optar por aceptarlos o no.

Es fundamentalmente diferente a otros SCM en su estructura porque registra cambios en el código fuente y no solo el estado estado de cada archivo/código. Pero también lleva registro de que cambios se realizaron juntos pudiendo versionar cambios a través de múltiples archivos a la vez.

Aunque no necesita un servidor central puede designarse un servidor central (de hecho podrían designarse más de uno) para:
* simplificar el proceso de coordinación y compartir los cambios en el código.
* servir de punto de confluencia para usuarios y desarrolladores (ya sea en una organización o en en forma pública para el OSS).

Como se dijo antes git es el software de SCM por excelencia. Los 3 usos básicos de los SCM listados arriba solo ocupan 3 capítulos de el [libro oficial de git](https://git-scm.com/book/en/v2) que tiene 10 capítulos y 3 apéndices. Git tiene un sinnúmero de opciones y funciones. Aquí haremos una introducción básica de su funcionamiento y más adelante en el curso volveremos sobre git para hablar de temas avanzados como workflows para su uso.

## Conceptos
* Repositorio
* Ramas
* commit
* push
* pull
* clone

## Repo "central": github/gitlab
Aunque git es distribuido a diferencia de la mayoría de scm que le precedieron. Enviar y recibir los cambios directamente de otros devs puede resultar cuando menos desafiante:

* Si se trabaja remoto/distribuido compartir el código requiere conocimiento de una ip publica o de un registro dns configurado para poder conectar.
* Se requiere un manejo paralelo para coordinar entre los desarrolladores indicando que cambios quiere pasarle a sus compañeros, en que repo y rama se encuentra, si es algún tag o commit en especial.
* Cada desarrollador debe en algún momento sincronizar su código con el de los demás.

Esos son las dificultades principales de trabajar distribuido pero hay más (aunque menos desafiantes o inconvenientes). Si bien es completamente posible hacerlo, resulta por cuestiones de organización

## Material relacionado

* [Basic review de Brais Moure](https://www.youtube.com/watch?v=3GymExBkKjE) 
* 