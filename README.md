Puppyes-ccgit
=============

Guía para mortales, configura y clona repositorios de git en PuppyLinux

La perspectiva de un usuario común y corriente sin poderes mutantes.
¿Pero cual es la idea de usar git para gestionar un proyecto ya sea personal o 
grupal?, bueno veamos algunas ventajas.

- Se puede trabajar en el proyecto incluso sin una conexión a internet
- Es mas rápido desarrollar proyectos.
- Se puede saber quien ha tocado qué y cuándo el código.
- Se puede volver atrás de forma rápìda.
- Puede controlar las versiones atavés de etiquetas.  
- Mejora nuestra capacidad de trabajar en equipo.

##Tabla de Contenidos##
======================================

- [La forma practica de usar git en Puppy](#la-forma-practica-de-usar-git-en-puppy)
- [Tu identidad](#tu-identidad)
- [Otros parámetros](#otros-parámetros)
- [Trabajando en tu ordenador](#trabajando-en-tu-ordenador)
- [Comandos útiles](#comandos-útiles)
- [Creando ramas y su función](#creando-ramas-y-su-función)
- [Fusionando cambios](#fusionando-cambios)
- [Etiquetas o Tags](#etiquetas-o-tags)
- [Aplicando a Puppy](#aplicando-a-puppy)
- [Metiendo la pata :)](#metiendo-la-pata)
- [La Manada en acción](#la-manada-en-acción)

##La forma practica de usar git en Puppy ##

Lo primero que debemos hacer es:
- Crear nuestra cuenta en github.
- Descargar e instalar los paquetes necesarios.
- Crear nuestro repositorio o proyecto.
- Configurar y clonar nuestro proyecto a la pc.

Puedes adquirir una cuenta y configurarla desde el sitio web en [Github](https://github.com/)

Descargar los paquetes 

[git-1.8.4.2.pet](https://copy.com/YUEQzvioSaKD)

[ccgit-0.1.pet](https://copy.com/6ZeEow0E27UK)

Crear un repositorio. 
Donde alojar nuestro proyecto no es complicado, hasta ahora solo
nos hemos manejado desde el sitio web y descargado los paquetes que nos permitirán 
configurar y usar git en nuestro ordenador.

![screenshot](http://i.imgur.com/T5oZAQ3.png)

Una vez creado nuestro repositorio solo nos falta configurar nuestra cuenta en el 
ordenador, ahi es donde entra en acción el script de automatización ccgit, es recomendable
empezar un proyecto con un archivo Readme y con un archivo de Licencia para proyectos
libres.

Escribe en terminal 

`ccgit`

Originalmente el script fue escrito por D-coy y su finalidad es configurar git en 
nuestro ordenador con ciertos parámetros ya establecidos, veamos una breve descripción.

##Tu identidad ##

- git config --global user.name woofshahenuzp donde "wooshahenzup" es tu usuario
- git config --global user.email tu-correo@bla.com "escribes tu correo"`

## Otros parámetros ##
 
- git config --global core.editor geany  Tu editor "geany" es por default
- git config --global core.pager '' 
- git config --global color.ui true
- git config --global http.sslVerify false
- git config --global push.default matching
- git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

Esto es lo que hace el script, si hay alguna configuración extra solo edita
el archivo en /usr/bin/ccgit 

Bien el script te pregunta si quieres clonar o bajar un repositorio a tu ordenador 
y que escribas la URL para ello solo vas al sitio web de tu cuenta en github y 
copias al portapapeles (copy to clipboard ).

![screenshot](http://i.imgur.com/bVYez9m.png)

Copias la URL donde te lo indique el script, siempre puedes bajar cualquier repositorio
con el comando 

`git clone`

Seguido de la URL del repositorio ej:

`git clone https://github.com/Woofshahenzup/Puppyes-ccgit.git`

Ahora ya podemos ver nuestro proyecto en nuestra carpeta HOME, es en este punto que
podremos trabajar nuestro proyecto con tranquilidad. 

¿Demasiada teoria? bueno simplificando las cosas solo corriendo el script de automatizacion ya puedes
tener lo anteriormente explicado claro con los paquetes instalados y con tu cuenta creada.

##Trabajando en tu ordenador 

![screenshot](http://i.imgur.com/16yzwOn.png)

Bien ahora trabaja normal en tu directorio, dependiendo a las necesidades de tu proyecto
- Creando un documento 
- Creando una estructura de un paquete ejemplo /usr/bin/ccgit el archivo que he subido a este
  proyecto.
- Editando un documento, script o cualquier otra cosa
- Agregando mas archivos con diferentes extensiones .png .txt etc

Cada vez que trabajas dentro de tu directorio proyecto, git esta guardando las modificaciones
esperando que que éstas sean enviadas a tu repositorio remoto osea el que esta en el sitio web

##Comandos útiles ##

Haz un cambio, modifica algun archivo, sube uno nuevo lo que tu quieras, ahora revisa el estado

`git status`

![screenshot](http://i.imgur.com/0Pyw3nA.png)

En letras rojas esta el archivo que modifiqué, y además unos dialogos de ayuda 
- git add file para actualizar lo que se le va a hacer commit
- git checkout -- file para descartar algun archivo. 

Entonces hacemos el siguiente comando 

`git add .`

Asi registramos nuestros cambios ( añadidos al index ) veamos como cambia ahora si 
hacemos nuevamente `git status`.

![screenshot](http://i.imgur.com/EZvCJ3a.png)

Letras verdes indican que ya registraste los cambios, mas comandos de ayuda
- git reset HEAD file  para deshacerlos del index.

Muy bien ahora vamos a hacer el commit para incluirlos al HEAD 
recuerda esta es una guia practica si quieres saber mas puedes buscar tutoriales 
más explicados sobre la terminologia de git [( Guia rápida )](http://rogerdudler.github.io/git-guide/index.es.html)

Pero bueno hagamos el commit. 

`git commit -m "Mensaje del commit entre comillas"`

![screenshot](http://i.imgur.com/Xq8YqDQ.png)

Como ven 1 archivo cambió, se insertaron 37, y se borraron 4

Ahora nuestros cambios ya pueden ser enviados al repositorio remoto si nosotros
queremos.

`git push`

![screenshot](http://i.imgur.com/9sU6Q0m.png)

En este punto se te preguntará tu usuario y contraseña de git para poder guardar
los cambios en tu repositorio remoto.
Puedes ver el registro de los cambios que has hecho en tu repositorio usando el 
comando.

`git lg`  (el cual es un alias a git log previamente configurado con el script de automatización) 

![screenshot](http://i.imgur.com/jyeAR89.png)

Hasta este punto ya hemos explicado lo mas básico de git en Puppy ahora ya puedes
gestionar tus versiones y proyectos de una forma rápida y sencilla.
Si practicas esto repetidaménte podras ver que no es tan complicado como parece.

##Creando ramas y su función ##

Una rama en git a manera fácil de entender es una division de nuestro proyecto principal
de hecho al proyecto en si se le conoce como rama "master" de ahi podemos partir ramificandolo 
y su finalidad puede variar de acuerdo a las necesidades aqui algunos ejemplos con este 
proyecto.

- Quiero agregar una nueva funcionabilidad al script de automatización, un parámetro 
  extra y no se si va a funcionar.
- El script tiene errores de ejecución y voy a hacer cambios mas radicales pero no quiero 
  perder la sintaxis del original
  
Entonces creo una rama paralela al proyecto y eso me servirá para trabajar cómodo sin 
cambiar mi trabajo en la rama 'master'.

`git checkout -b rama-prueba` 

He nombrado a la rama que voy a crear 'rama-prueba' 

![screenshot](http://i.imgur.com/zgzjbRQ.png)

El parámetro extra `-b` me traslada de una vez a la rama-prueba que he creado.
Para ver donde estoy parado puedo usar el comando 

`git branch`

![screenshot](http://i.imgur.com/azR7TbE.png)

ahora puedo trabajar en la rama haciendo mis pruebas, commits, push, etc. Como estoy editando 
este archivo Readme.md estos cambios solo se verán en mi 'rama-prueba' después vamos a fusionar los 
cambios a la rama master.

Si quiero que otros trabajen en la rama-prueba que yo he creado la tengo que subir a 
mi repositorio remoto. 

`git push origin rama-prueba`

![screenshot](http://i.imgur.com/JNqlpr7.png)

Otros comandos útiles

- git checkout master  ( vuelve a la rama principal )
- git branch -d rama-prueba ( borra la rama prueba )

##Fusionando cambios ##

Bueno  me gustaron los cambios que hice en la rema-prueba ahora, volvemos a la rama 
principal del proyecto o rama master para hacer la fusión o para aplicar los cambios
a la rama master.

`git checkout master`

recuerda que siempre por si no estas seguro en que rama estas, puedes usar `git branch`.
Bien ahora fusionamos nuestra rama-prueba.
Debes aseguarte que tanto las ramas master y pruebas o como las renombres deben estar 
actualizados sus cambios, siempre es bueno ver el estado de las ramas y hacer los 
respectivos commits y push para actualizar los cambios antes de fusionar ramas.

`git merge rama-prueba`

Y borramos la rama-prueba y la quitamos de nuestro repositorio local y remoto ya que no
la vamos a necesitar màs por el momento.

`git branch -d rama-prueba` Borra la rama de nuestro repositorio local.

![screenshot](http://i.imgur.com/d2Y70rj.png)

`git push origin :rama-prueba` Elimina la rama de nuestro repositorio remoto.

![screenshot](http://i.imgur.com/zyWWSsE.png)

##Etiquetas o Tags 

Bien tratemos de ser prácticos. Un tag, etiqueta, viñeta o como tu prefieras llamarle es
un punto en la historia de tu trabajo o proyecto en el cual ya tienes algo concreto.
Proyecto, programa, paquete o lo que sea que lleves trabajando y sirve para marcar un punto
donde has lanzado una versión X del mismo. 
¿Quieres leer un poco de teoria? [Creando etiquetas](http://git-scm.com/book/es/Fundamentos-de-Git-Creando-etiquetas)

##Aplicando a Puppy ##

Imagina que has creado un paquete, luego de haber trabajado en tu código probado y diseñado
y tu paquete trabaja perfecto, lo has nombrado versión 0.01,  bien entonces es un buen 
momento para hacerle un tag como dice la teoria un punto en el histórico de tu trabajo donde has
lanzado esa version del paquete.   

Bueno para poder crear un tag lo primero que vamos a hacer es ver el registro (log) para 
visualizar el último commit a que le vamos a hacer tag.

`git lg` 

![screenshot](http://i.imgur.com/xEUMVRp.png)

Vamos a tomar el id del ultimo commit 7b0e873 Para hacer referencia a nuestro tag

`git tag -a ccgit-0.01 -m "Script de automatización de git" 7b0e873`

ahora con el comando `git tag` podré ver mi etiqueta

![screenshot](http://i.imgur.com/J5E1hqv.png)

Si ya vas agarrando el hilo, sabras que si haces una etiqueta en tu repositorio local
tambien tienes que mandarlo a tu repositorio remoto para eso hacemos. 

`git push --tags`

![screenshot](http://i.imgur.com/4ZU8deU.png)

Y si observas tu repo remoto también podrás apreciar el cambio.

![screenshot](http://i.imgur.com/te6C1xv.png)

Como ven crear tags no es tan dificil y es muy bueno para llevar un control de nuestros 
releases o lanzamientos de nuevas versiones.

##Metiendo la pata ##

Hasta el más experto en la materia puede llegar a equivocarse mas aún cuando se trata de usar
git por lo que vamos a ver un poco como ir corrigiendo esas equivocaciones que tengamos pero 
antes hablemos como un usuario común (osea yo ;)) piensa que es git.
Para eso nos planteamos lo siguiente:

Cuando yo uso git para trabajar un proyecto me imagino dos escenarios: 
- 1 - El repositorio local o mi carpeta de trabajo en la pc.
- 2 - El repositorio remoto osea lo que veo cuando voy al sitio web de github.com y entro a mi 
      cuenta.
No es del todo cierto, un usuario por muy nuevo que sea debe entender que su repositorio local 
tiene 3 subdivisiones, etapas, areas, árboles o como mejor se entienda para poder sentirse seguro de
trabajar en su proyecto con toda tranquilidad.

### Repositorio Local

- 1- Directorio de trabajo.

Es ese directorio que ves en tu pc con el nombre de tu proyecto y que contiene todos los archivos
y al cual le vas agregando, quitando, editando etc.

- 2- El index o stage index

Una zona intermedia o área de preparación en explicaciones anteriores hablamos del comando

`git add`

Es en éste punto qué lo que has trabajado lo llevas al area de preparación o indice para luego ser
"commiteado".

- 3- El HEAD

El HEAD se refiere a un punto hacia donde señalan nuestros commits, algo muy útil cuando
trabajemos con ramas. cada HEAD tiene un nombre (nombre de la rama o etiqueta).
Por defecto, hay un HEAD en cada repositorio llamado MASTER y es ahi hacia donde apuntan 
nuestros commits, pero en determinado momento puedes cambiar a una rama y ésta se convierte
en el "current head" o cabecera actual. 

Pero la importancia de éstas definiciones són por que debes tener en claro cuando borres o 
cuando creas que hiciste algo mal y quieras revertir debes saber donde estabas parado antes del 
error.

-Pusiste un archivo en el directorio de trabajo y no era el que tu querias.

-Editaste un archivo y te diste cuenta que no era así.
 
-Tu archivo ya habia pasado al index con `git add`?.

-Hiciste commit `git commit -m "mensaje" ` y te equivoscate o tuviste un error ortográfico.

-Mandaste al repositorio remoto tus cambios `git push` y despues te diste cuenta del error.

Para todos estos casos es necesario saber donde estamos y así resultará más fácil
enmendar el problema, si usas la lógica irás viendo que no es tán complicado revertir un cambio 
en git.

![screenshot](http://i.imgur.com/r7ls9fG.png)

Una imágen para comprender mejor.

### Pusiste un archivo en el directorio de trabajo y no era el que tu querias.

Puedes crear y borrar sin problemas usando el administrador de archivos (sea rox, pcmanfm etc)
como tu lo desees click derecho, por linea de comandos tu directorio de trabajo se comportará 
igual que cualquier carpeta contenedora.

![screenshot](http://i.imgur.com/lQW9aHM.png)

Luego de borrado `git status` no mostrará ningún cambio.

![screenshot](http://i.imgur.com/8oWgmqx.png)

### Tu archivo ya habia pasado al index con `git add`.

como viste en la imagen que te muestra como esta conformado tu repositorio local. supongamos 
que el archivo perro-malo.txt esta en el index y no lo queremos ahi pero veamos como fué que llegó 
ahí.

![screenshot](http://i.imgur.com/wFqvJiJ.png)

Git te dice que si deseas "unstage" o quitar de el index hagas el comando `git reset HEAD <file>`
para el caso sería `git reset HEAD perro-malo.txt`, ok vamos a probar.

![screenshot](http://i.imgur.com/aKadvkZ.png)

Claramente puedes ver que sacamos a perro-malo.txt del index y muestra la modificación al Readme.md 
que es el archivo que estoy editando para hacer ésta guia.
Basta con borrar el archivo de forma normal y tendras nuevamente limpio tu directorio de trabajo.

Hay formas mas seguras de remover archivos con los comandos 

`git rm` y `git rm --cached [archivo]` pero ya que le vas agarrando ritmo veremos eso en capítulos 
siguientes.

### Hice commit `git commit -m "mensaje" ` y meti la pata.

Ok vamos a meter la pata de verdad haciendo commit de perro-malo.txt.

![screenshot](http://i.imgur.com/OoVIn8G.png)

En la medida que vas estudiando git te vas dando cuenta que complicar las cosas no es tan sencillo, pero
puede pasar asi que lo mejor es revisar bien antes de agregar y commitear.

Hice commit `git commit -m "metiendo la pata de verdad"` para borrar o revertir ese cambio hacemos el comando 

`git reset --hard <sha1-commit-id>`  donde <sha1-commit-id> es el identificador del commit para saber cual es
basta con hacer `git lg` o `git log` para saber que id tiene el commit que deseamos borrar.

![screenshot](http://i.imgur.com/LwV2nGO.png)

Este es el commit que deseamo sacar:
`* 6efede1 - (HEAD, master) metiendo la pata de verdad (10 minutes ago) <woofshahenzup>`

entonces hacemos el comando:
`git reset --hard 6efede1`

![screenshot](http://i.imgur.com/TT1msFh.png)

Muy bien ahora borramos normalmente perro-malo.txt de nuestro directorio `git rm perro-malo.txt` y `git checkout perro-malo.txt`
muy bien, podemos hacer commit de nuestras modificaciones arregladas.

### Removí el archivo de mi repositorio local pero se muestra en mi repositorio remoto.

Bien ya que tenemos una idea mas clara de como aplicar cambios partiendo de que 

- los repositorios se diferencian por ese único archivo `perro-malo.txt`

entonces lo mas lógico sería.

1- traer ese archivo a nuestro repositorio local `git pull`

2- borrar el archivo en el repo local            `git rm perro-malo.txt`

3- hacer el commit notificando lo que borramos   `git commit -m "removiendo archivos"`

4- hacer el envio al repositorio remoto          `git push`

Esta forma no es exclusiva puede haber mas de una pero como usuario común resulta mas comodo así.
De esa manera tendrás tus repositorios sincronizados, limpios, y en orden.

##La Manada en acción 

Ya tenemos claros algunos conceptos básicos sobre como trabajar git en Puppy, ahora
la pregunta es: Como puedo contribuir con un proyecto donde no soy un desarrollador 
directo, no conozco a ninguno del grupo de trabajo, no puedo pedirles que me hagan
colaborador asi que es ahi donde entra en acción la palabra FORK.

Veamos una definición simple entre clonar y hacer fork.

Clonar un repositorio es descargar un repositorio remoto a tu pc en el cual tú eres el 
propietario de ese repositorio o proyecto, tú decides que cambia y que no, tú decides a 
quien pones como Colaboradores, recuerda un colaborador tiene los mismos privilegios 
que el propietario de dicho repositorio/proyecto.

Hacer fork quiere decir que tu vas a crear una copia exacta de un proyecto X el cual le 
pertenece a otra persona, dicha copia exacta estará asociada a tu cuenta de Github lo que 
significa que habrán 2 proyectos con el mismo nombre, el repositorio original y la copia 
asociada a tu cuenta, ahora en adelante tu puedes hacer los cambios que quieras en tu 
Fork, cambiar, borrar, editar, estropear lo que tu quieras sin que eso afecte al repositorio
original, eso es muy bueno por la independencia que hay aun trabajando un mismo proyecto, y así 
tu puedes si haces cambios y mejoras notables a dicho proyecto hacer PULL REQUEST, los 
desarrolladores del proyecto revisan y prueban tus cambios y si eso mejora el repositorio 
lo incorporan al proyecto o simplemente lo ignoran si no les parecen esos cambios y sí así lo desean. 

Lo cual está bien, si alguien hace FORK de un repositorio es por que piensa que le puede 
servir o puede colaborar, también por que piensa que puede mejorarlo o adaptarlo a sus necesidades y tú eres libre 
de mejorar tu FORK de otro proyecto, sin importar si tus cambios son o no
agregados al proyecto original.

Para hacer un Fork lo primero que debes haces es: 
- Logearse, debes estar logeado para poder hacer un Fork
- Estando logeado, escoger el proyecto al cual quieres hacerle un fork. 
- Presionamos el botón de `Fork´ 

![screenshot](http://i.imgur.com/MctffGV.png)

- Luego Github nos pregunta donde deberíamos hacer fork de dicho repositorio, lo voy a 
asociar a mi cuenta woofshahenzup

![screenshot](http://i.imgur.com/Azxnt6D.png)

- Listo! Si se fijan en los recuadros rojos, en mi cuenta Woofshahenzup he hecho un fork
del proyecto Clamvtk el cual pertenece a josejp2424. 

![screenshot](http://i.imgur.com/ySX4rOE.png)

- Ahora solo me haría falta clonar a mi PC mi fork de clamvtk.

`git clone https://github.com/Woofshahenzup/Clamvtk.git`

![screenshot](http://i.imgur.com/ug63oRz.png)

### El término Upstream ( Wikipedia )

En desarrollo de software, el término inglés upstream (que traducido al español 
significa algo como «aguas arriba») se refiere al envío de un parche o corrección 
al autor original del software o, en su defecto, a sus mantenedores principales, 
para que éste se integre al código fuente del software.

Por ejemplo, un parche enviado upstream es ofrecido a los autores o mantenedores 
del software. Si es aceptado, será incluido en la aplicación, ya sea inmediatamente o en 
una versión futura.

El desarrollo en upstream permite a otras distribuciones beneficiarse del parche al 
utilizar el software. Si por ejemplo se encuentra un error en una aplicación, y 
los mantenedores de cierta distribución lo corrigen pero no lo envían a upstream, ni 
las otras distribuciones ni desarrolladores podrán beneficiarse de la corrección 
sin tener que volver a implementar el parche de manera separada. 

- Para colaborar con el usuario josejp2424 entonces necesito hacer upstream desde mi repositorio
de la siguiente manera.

`git remote add upstream https://github.com/josejp2424/Clamvtk.git`

Si no hay ningun problema la terminal no les va a tirar ningun error

SIEMPRE antes de trabajar en el proyecto, debemos actualizarlo. 

`git pull upstream master`

![screenshot](http://i.imgur.com/yYzMC1a.png)

MUY BIEN!! ahora trabajo normal agregando cambios a mi FORK.

- `git add archivos` o `git add .`
- `git commit -m "Mensaje de mis cambios realizado"`
- `git push` o `git push origin master`

- Despues nos dirigimos al sitio web de nuestro repositorio y pulsamos el botón 
Pull Request

![screenshot](http://i.imgur.com/P96glf4.png)

- Luego seguimos los pasos que nos indiquen la página, llenamos la información que 
nos solicite, completamos y le mandamos la información a josejp2424 con los cambios
que hemos añadido.

- Ok ahora aclarando bien el concepto para trabajar colaborando con otros desarrolladores lo que 
hay que hacer es:

1- Hacer fork de cualquier proyecto ( botón de fork desde el navegador )

2- Clonar el fork de ese proyecto a nuestra pc ( carpeta local )

3- Hacer add upstream para nuestro repositorio ( traer el repositorio original a nuestro proyecto )
   
   nótese el cambio al hacer upstream 
   
![screenshot](http://i.imgur.com/QQYIGYR.png)

4- Actualizar los repositorios con nuestra carpeta local

 `git fetch upstream`
 
5- Cambiar a nuestra rama principal 

 `git checkout master` 

6- Hacer merge del master upstream con nuestro master 

 `git merge upstream/master`
 
7- Hacer el push a nuestro repositorio en github 
 
 `git push origin master`
 
- Es muy importante estar actualizando nuestro repositorio con el original para evitar problemas de sincronía y 
hacer nuestros pull request sin afectar al desarrollador 'fetch upstream y merge upstream/master' antes de empezar 
a trabajar en nuestro repositorio local y hacer pull request.

Continuará....
