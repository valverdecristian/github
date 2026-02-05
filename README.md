# 🚀 Ultimate Git + GitHub

## 📌 Git

### 📍 ¿Qué es Git?
Es un sistema de control de versiones, que nos permite gestionar cambios en los archivos de código de forma eficiente.

### 📍 Beneficios de Git
* ✅ Guardar el historial de cambios.
* ✅ Recuperar versiones anteriores.
* ✅ Permitir colaboración en equipo.
* ✅ Permite trabajar de forma remota o local.

<br>

### 🔧 Instalación y Configuración Básica
1️⃣ Instalar Git. [ir a Git](https://git-scm.com/)

Luego de la instalación viene la configuracion:
- **Sistema**: es para todos los usuarios y todos los repositorios. Que van a usar el nombre, correo y editor de texto que nosotros decidamos configurar.
- **Global**: todos los repositorios del usuario.
- **Local**: todos los datos que nosotros configuremos en Nombre, Correo y Editor es para ese repositorio en especifico.

📢 Lo que vamos a configurar es el Nombre del usuario, su correo y el editor de texto que vamos a utilizar con git.

<br>

2️⃣ Configurar Git (solo la primera vez)
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
git config --global core.editor "code --wait"
```
📢 no es extrictamente necesario ejecutar este ultimo comando para usar Git. Este comando configura "VS Code" como el editor predeterminado de Git. Si no configuramos un editor, Git usará el predeterminado del sistema.

<br>

### 📂 Flujo de Trabajo y Staging Area

#### 1. Creación e inicialización

```bash
# Esto crea un repositorio vacío en la carpeta indicada.
# Si ya estoy en la carpeta donde voy a trabajar solo uso 'git init'
git init nombre-del-repo
cd nombre-del-repo
```

#### 2. Zona de Preparación (Staging Area)

La Zona de Preparación (o Índice) es un paso intermedio donde seleccionamos exactamente qué cambios queremos incluir en el próximo commit.

```bash
# Ver el estado de los archivos (cuáles están modificados, cuáles en Staging).
git status

# Agregar Cambios a la Zona de Preparación (Staging Area)
git add archivo.txt

# Tomar una fotografía instantánea (Commit)
# El commit SOLO incluye los cambios que están en el Staging Area.
# el mensaje no puede superar los 50 caracteres (sino usar git commit + enter y agregar descripcion desde la tercera linea)
git commit -m "mensaje descriptivo del cambio"
```

<br>

### 📍 Control de versiones
Es la practica de gestionar y realizar un seguimiento de los cambios en archivos y proyectos a lo largo del tiempo.

Tipos de control de versiones:
1) **Local**: se guarda el historial en un solo equipo.
2) **Centralizado (CVCS)**: un servidor central gestiona todas las versiones.
3) **Distribuido (DVCS)**: cada usuario tiene una copia completa del repositorio, permitiendo trabajar sin conexión. <br>
📢 Git: es un excelente ejemplo de un sistema de control de versiones distribuido.

<br>

### 📍 ¿Como usar Git?

- ✅ desde la Terminal.
- ✅ desde nuestro editor de codigo/IDE.
- ✅ desde nuestras herramientas graficas (GUI).

<br>

### 📍 Conectar con el repositorio Remoto

- Se configura un remoro llamado "origin" que apunte a la URL del repositorio en GitHub.
- 👉 PRIMERO: se debe obtener la URL (generalmente termina en .git)
- 👉 SEGUNDO: conectar el repositorio local con el remoto usando el comando "git remote add"

```bash
# Reemplaza <URL_DEL_REPOSITORIO> con la URL que copiaste de GitHub
git remote add origin <URL_DEL_REPOSITORIO>

# Enviar los cambios, la primera vez se usa la opcion -u
git push -u origin main
```

- `git push`: El comando de envío.
- `-u`: Configura el remoto por defecto (origin) y la rama por defecto (main) para futuros push y pull
- `origin`: El nombre del remoto que se acaba de configurar.
- `main`: El nombre de la rama (local) que se esta enviando (verificar que no sea master).

- 💡 Para futuros envios desde la rama main, solo se necesita usar el comando simple

```bash
git push
```

### 📍 Renombrar la rama local

```bash
# Renombra la rama local de master a main
git branch -M main

# Empuja la rama renombrada
git push -u origin main
```

### 📍 Estados de los Archivos (Short status)

Se refiere a una forma concisa que Git utiliza para mostrar el estado de tus archivos al ejecutar el comando:

```bash
git status -s
```

Esto permite ver que cambios realizamos y donde estan (Directorio de trabajo vs Área de preparación)
Se muestra una linea por cada archivo modificado, con **dos columnas de letras** que representan los estados de ese archivo.
El formato es XY, donde:
- X (columna izquierda): Muestra el estado del archivo en el Staging Area. (en verde)
- Y (columna derecha): Muestra el estado en el Working Directory. (en rojo)


| Símbolo | Significado               | Ubicación                                      | Significado                                    |
|--------:|---------------------------|------------------------------------------------|------------------------------------------------|
| `M`     | Modified (Modificado)     | El archivo ha sido modificado.                | `git add` ya ejecutado. Listo para `git commit` // `git add` pendiente
| `A`     | Added (Añadido)           | El archivo está añadido al Staging Area.      | Archivo listo, falta `git commit` //
| `D`     | Deleted (Eliminado)       | El archivo ha sido eliminado.                 | falta `git commit` // `git add` para confirmar
| `??`    | Untracked (Sin seguimiento)| Git no está rastreando este archivo.          | usar `git add` para empezar a rastrearlo
| `R`     | Renamed (Renombrado)      | El archivo ha sido renombrado.                |
| `C`     | Copied (Copiado)          | El archivo ha sido copiado.                   |
| _(espacio)_ | Sin cambios           | El archivo no ha sido modificado.             |


### 📍 Revisar Cambios (git diff)

Antes de hacer un `git commit`, es una buena práctica revisar los cambios que están a punto de guardarse.
- git diff tiene dos modos principales

1) Ver cambios aun NO PREPARADOS: este comando muestra los cambios que todavia NO se agregaron al Staging Area.
2) Ver cambios YA PREPARADOS: muestra los cambios que SI estan en el Staging Area.

```bash
# 1
git diff

# 2 ambas opciones hacen exactamente lo mismo
git diff --cached
git diff --staged
```

### 📍 Ver cambios de forma Visual (git difftool)

Si los cambios son muchos o complejos, la terminal se vuelve difícil de leer. Para eso usamos herramientas gráficas (como VS Code) que permiten ver los archivos lado a lado.

- Comandos: Son idénticos a los anteriores, pero cambiando diff por difftool.

```bash
git difftool          # Ver cambios no preparados visualmente
git difftool --staged # Ver cambios preparados visualmente
```

### 💡 Configuración para VS Code

Para que Git sepa que debe abrir VS Code al usar este comando, ejecutá estas líneas una sola vez:

```bash
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'
```

Para verificar esta configuracion usamos el comando: git config --global -e. Deberiamos ver como abrio vscode y ver las dos variables, sino agregarlas manualmente.

### 📍 Confirmar cambios (commits)

El "commit" es el comando que toma todos los cambios que están en el "Staging Area" (los que están en verde / columna izquierda) y los guarda permanentemente en el historial de Git con un mensaje.

- **Atajo**
- -a (de all): combina dos pasos en uno (automaticamente agrega al staging area todos los archivos que Git ya rastrea)


## 📍 Historial

Para poder ver el historial de nuestros commits utilizamos el comando `git log`.
- `(HEAD)` indicara en que rama estamos parados.

### 📍 Ver contenido de commits

- Se debe usar el id del commit o al menos una parte, por ejemplos los primeros 4 caracteres
- Si quiero ver algun archivo en especifico le agrego dos puntos y el nombre
- con el comando show puedo ver commits, blob, tree y tags

```bash
git show id-commit:archivo-especifico.txt

# alternativa
git show HEAD~3 # 3 commits hacia atras
```

### 📍 Etiquetas (Tags)

Existen dos tipos principales de etiquetas, pero para nuestro caso las más recomendadas son las **anotadas**, ya que guardan mucha información.

📌 **Etiquetar commits pasados** No es necesario estar parado en el commit para etiquetarlo. Solo necesitás su ID (hash)

1) **Crear una etiqueta anotada**
Este tipo de etiqueta incluye el nombre de quien la creó, la fecha y un mensaje explicativo.

```bash
git tag -a v1.0 -m "Versión estable del proyecto"

# para un commit pasado agregar el id-commit antes del -m
git tag -a v1.0 8cf31b2 -m "Version estable"
```

2) **Crear una etiqueta ligera**
Es simplemente un marcador que apunta a un commit específico, sin más información.

```bash
git tag v1.0-beta
```

3) **Listar y ver etiquetas**

```bash
# Ver todas las etiquetas creadas
git tag

# Ver etiquetas con mensaje
git tag -n

# Ver la información de una etiqueta específica y su commit
git show v1.0
```

4) **Subir etiquetas a GitHub**
Por defecto, git push no envía las etiquetas al servidor remoto. Debes hacerlo explícitamente:

```bash
# Subir una etiqueta específica
git push origin v1.0

# Subir TODAS las etiquetas que tengas localmente
git push origin --tags
```

### 📍 Resumen por Autores (git shortlog)

Si git log es para ver el detalle, git shortlog es para ver el panorama general del equipo. Agrupa los commits por autor.

```bash
# Ver quién trabajó más y cuántos commits hizo
# -s oculta los mensajes de los commits; -n orden descendente
git shortlog -sn
```

** 📢 Este comando solo mostrara los commits de la rama donde estamos parados, para ver el resumen completo (del grupo) se debe pasar el nombre: git shortlog main

### 📍 Sacando archivos del Staging Area

- Para deshacer un `git add`, el comando es:

```bash
git restore --staged nombre-del-archivo
git restore nombre-del-archivo #elimina los cambios completamente
```

📢 Es importante no olvidar ``--staged` porque sino descarta por completo todos los cambios que se hizo en ese archivo y lo revierte a la version del último commit. (es irreversible).

Para forzar la eliminacion de un archivo se usa el comando git clean -f (opcion peligrosa)

### 📍 Restaurar archivos a versiones anteriores

Si cometiste un error y necesitás que un archivo vuelva a ser exactamente como era en un commit pasado, usamos git restore con el flag --source. Source se entiende en este contexto como "fuente"

```bash
# 1. Buscás el ID del commit donde todo estaba bien
git log --oneline

# 2. Restaurás el archivo desde esa "fuente" (source)
git restore --source id-commit nombre-del-archivo

# alternativa al id, utilizar HEAD~1
git restore --source=HEAD~1 nombre-del-archivo # ~1 indica que se quiere volver 1 commit anterior
```

💡 Nota importante: Al ejecutar esto, el archivo en tu Working Directory cambiará automáticamente a la versión vieja. Luego deberás hacer git add y git commit para "confirmar" que querés quedarte con esa versión recuperada.


### 📍 Historial de un archivo específico

Si querés ver la evolución de un solo archivo a través del tiempo (quién lo tocó y cuándo), podés filtrar el log:

```bash
git log -- nombre-del-archivo

# Para ver qué cambió exactamente en cada commit de ese archivo
git log -p -- nombre-del-archivo
```

** 💡 El "Pro-Tip": Si el archivo cambió de nombre en el pasado (usando git mv), el historial normal se cortará. Para ver TODO el historial incluso antes del cambio de nombre, usá: git log --follow -- nombre-del-archivo.


### 📍 Recuperar un archivo eliminado

Si borraste un archivo y ya hiciste commit de esa eliminación, no te preocupes: el archivo sigue en el historial. Para traerlo de vuelta, el proceso tiene dos pasos.

1) encontrar el último commit donde existia el archivo

```bash
git log --oneline -- nombre-del-archivo
```

** Este comando muestra la lista de commits donde se encuentra ese archivo, el primero que aparece suele ser el de la eliminacion, se debe tomar el ID del commit anterior para poder restaurarlo usando el comando restore

```bash
git restore --source id-commit -- nombre-del-archivo
```

### 📍 Responsabilidad y Contexto (git blame)

git blame te permite ver, línea por línea, quién fue la última persona en modificar un archivo, en qué commit lo hizo y en qué fecha.

```bash
git blame nombre-del-archivo
```

### 📍 Control Granular (--patch o -p)

El flag `--patch` permite trabajar por "hunks" (fragmentos de código) en lugar de archivos completos.
En un mismo archivo podemos realizar varios cambios y cuando hacemos un commit con --patch podemos decidir que parte agregar al Staging Area.
Lo mas comun es usar `git add -p`, al ejecutarlo Git mostrara un trozo de código y una pregunta `Stage this hunk [y,n,q,a,d,j,J,g,/,e,?]?`

- y (yes): Agrega ese pedazo al Staging Area.
- n (no): No lo agrega.
- s (split): Si el bloque es muy grande, lo divide en partes más pequeñas.
- q (quit): Sale del proceso.


### 📍 Resumen de Cambios (--stat)

Mientras que git diff te muestra cada línea que cambió, --stat te da un resumen estadístico.

Es ideal para cuando querés saber "qué tanto" cambió el proyecto sin leer todo el código. Te muestra:

1) Qué archivos fueron modificados.
2) Cuántas líneas se insertaron (+) y cuántas se borraron (-) por archivo.
3) Un conteo total al final.

Se puede usar principalmente con diff y con log:

```bash
git diff --stat # Resumen de lo que cambiaste en tu carpeta.
git log --stat # Resumen de cambios en cada commit del historial.
```

## 📍 Búsqueda Avanzada

### 📍 Buscar en el historial (The Pickaxe)

Si recordás una función o una línea de código específica, pero no sabés en qué commit se agregó o se borró, podés usar el flag -S.

```bash
git log --oneline -S"nombre_de_la_funcion" -i -p # -p o -patch, para mostrar el diff (código exacto)
# -i para que no sea case-isensitive
```

### 📍 Buscar en los archivos actuales (git grep)

Para buscar un texto rapidamente en los archivos actuales se puede usar

```bash
git grep -n "texto_a_buscar"
```


## 📍 Navegación y Ramas (git checkout)

git checkout se usa principalmente para moverte entre las diferentes "líneas de tiempo" (ramas) de tu proyecto o para recuperar versiones específicas de archivos. Aunque hoy existen git switch y git restore.

1) Cambiar de rama: Si querés saltar de tu rama actual a otra ya existente.

```bash
git checkout nombre-de-la-rama
```

** 💡 Nota moderna: Ahora se recomienda usar git switch nombre-de-la-rama porque es más descriptivo.

2) Crear y cambiar a una rama nueva (atajo): uno de los comandos que mas voy a utilizar.

```bash
git checkout -b nueva-rama # -b significa branch
```

3) Volver a una versión anterior de un archivo: si modificamos un archivo y queremos volver a estar exactamente como en el ultimo commit (descartando los cambios actuales)

```bash
git checkout -- nombre-del-archivo
```

** ⚠️ Cuidado: Este comando borra tus cambios actuales de forma irreversible.
** 💡 Nota moderna: Se prefiere usar git restore nombre-del-archivo (el que ya tenemos en el resumen).

**Eliminar ramas**

```bash
# Eliminar una rama local (después de haberla fusionado)
git branch -d nombre-de-la-rama

# Forzar la eliminación (si no se fusionó)
git branch -D nombre-de-la-rama
```

### 📍 El estado "Detached HEAD" (Cabezal desprendido)

Si usás checkout para ir a un ID de commit específico en lugar de a una rama:

```bash
git checkout a1b2c3d

# Entrarás en un estado donde Git te avisa que el "HEAD" se desprendió.
```

** ⚠️ Significa que no estás parado en ninguna rama. Podés mirar el código y hacer pruebas, pero si hacés commits ahí, se perderán cuando te muevas a otra rama, a menos que crees una rama nueva en ese momento.
** 💡 Se sale de ahi simplemente volviendo a una rama con git checkout main


### 📍 Guardado Temporal (git stash)

Imaginate que estás en medio de una funcionalidad compleja en tu rama feature/cristian, tenés código que todavía no termina de funcionar (no querés hacer commit de algo roto), y de repente un compañero te pide que revises un error urgente en la rama main. No podés cambiar de rama con git checkout porque tenés cambios pendientes. Ahí es donde entra el stash.

Se usa para "apartar" cambios que todavía no están listos para un commit, permitiéndote cambiar de rama con un directorio de trabajo limpio.

```bash
# 1. Guardar de forma organizada (RECOMENDADO)
git stash push -m "descripción de lo que estabas haciendo"

# 2. Guardar incluyendo archivos nuevos (??)
git stash push -u -m "incluye archivos nuevos de la sala de juegos"

# 3. Guardado rápido (sin etiqueta personalizada)
git stash

# Guardar TODO (incluyendo archivos nuevos ??)
git stash -u

# Ver la lista de cosas guardadas
git stash list

# Recuperar los cambios y limpiar el cajón
git stash pop

# Recuperar los cambios pero mantenerlos en el cajón
git stash apply
```

📢 Escenario común: Estás trabajando en un componente de Angular, no terminaste la lógica, pero tenés que saltar a main para un fix urgente. Usás git stash, hacés el fix, volvés a tu rama y usás git stash pop.

## 📍 Alias

```bash
git config --global alias.gl "log --oneline --graph" # entre comillas lo que queremos ejecutar
```

Luego usamos el comando "git gl", y se ejecutara lo que pusimos como alias, para verificar que ese alias fue agregado usamos el comando `git config --global -e`, se podra ver una nueva sesion llamada "alias" seguido el comando y lo que se va a ejecutar.


### 📍 Encontrar el origen de un Bug (git bisect)

git bisect se usa para encontrar exactamente qué commit introdujo un error (bug) en tu código utilizando una búsqueda binaria.

Es especialmente útil cuando tenés cientos de commits y sabés que ayer el proyecto funcionaba bien, pero hoy algo se rompió y no sabés en qué momento pasó.

En lugar de revisar cada commit uno por uno, git bisect divide el historial a la mitad, te pide que pruebes si el código funciona, y descarta la mitad donde el error no está. Es mucho más rápido que buscar manualmente.

**Flujo**

```bash
# 1 iniciar el proceso
git bisect start

# 2 marcar el estado actual como "malo"
git bisect bad

# 3 marcar un punto en el pasado como "bueno"
git bisect good id-commit-o-tag

# 4 Git te lleva a la mitad. Probás el código y respondés:
git bisect good   # (si funciona)
# O...
git bisect bad    # (si sigue roto)

# 5 Al terminar, volvés a la normalidad con:
git bisect reset
```

## Gestion de Ramas (Branching)

En Git, una rama es basicamente una **linea de tiempo paralela**. En lugar de tener un solo camino de commits, podés bifurcar el proyecto para trabajar en cosas distintas sin que se molesten entre sí.

**Beneficios**

1) Aislamiento: se puede probar ideas locales o corregir errores criticos sin tocar la version estable
2) Colaboracion: cada integrante del grupo puede trabajar en su propia funcionalidad.
3) Orden: se mantiene el historial limpio y organizado por tareas.

### 📍 Conceptos fundamentales

Para gestionar ramas con éxito en nuestros proyectos, necesitamos entender estos tres pilares:

1) La rama "Main" (o Master): Es la rama sagrada. Siempre debe tener codigo que funcione y compile. NUNCA SE DEBERIA TRABAJAR DIRECTAMENTE SOBRE ELLA SI ESTAMOS TRABAJANDO EN EQUIPO.
2) Ramas de Funcionalidad (Feature Branches): Son ramas temporales, para una tarea especifica. Una vez que la tarea termina y se prueba, se une a la rama principal y la rama temporal se borra.
3) Fusión (Merge): Git toma los cambios de nuestra rama de funcionalidad y los integra en `main`

```bash
# listar ramas
git branch

# crear una rama
git branch nombre-rama

# convencion: funcionalidad -> feature; error -> bugfix
# lo mejor es utilizar el numero de ticket

# para cambiarme a la rama creada
git switch nombre-rama

# cambiar nombre de la rama
git branch -m nombre-rama nuevo-nombre
```

## 📍 Tipos de Merge

Cuando ejecutás el comando git merge, Git analiza la historia de ambas ramas y decide qué técnica usar para unirlas.

### 📍 Fast-forward Merge

Es el tipo de unión más simple y limpia. Ocurre cuando la rama a la que querés fusionar (ej: main) no ha recibido ningún commit nuevo desde que creaste tu rama de funcionalidad.

* **Cómo funciona**: Git no crea un commit nuevo; simplemente "mueve el puntero" de main hasta el último commit de tu rama.
* **Resultado**: Un historial lineal, como si nunca te hubieras separado de la rama principal.
* **A tener en cuenta**: Es el escenario ideal porque nunca genera conflictos.

### 📍 3-way Merge (Merge de 3 vías)

Ocurre cuando las ramas han divergido. Es decir, vos hiciste commits en tu rama feature, pero tus compañeros también subieron cambios a main mientras tanto.

* **Cómo funciona**: Git busca tres puntos para crear la unión:
  1) El último commit de la rama main.
  2) El último commit de tu rama feature.
  3) El ancestro común (el punto donde ambas se separaron).

* **Resultado**: Git crea automáticamente un nuevo commit llamado "Merge commit" que une ambas historias.
* **A tener en cuenta**: Aquí es donde Git intenta fusionar el código automáticamente. Si no hay cambios en las mismas líneas, se soluciona solo.


### 📍 Conflictos de Merge (El momento de la verdad)

Si en un 3-way Merge vos y un compañero modificaron la misma línea del mismo archivo (por ejemplo, el app.component.ts de tu proyecto Angular), Git se detendrá y te dirá: "¡Auxilio! No sé qué versión elegir".

🔍 Cómo identificar un conflicto

Al abrir el archivo en conflicto, verás estas marcas:

```bash
<<<<<<< HEAD
// Tu código que está en la rama actual (ej: main)
console.log("Versión de mis compañeros");
=======
// El código que viene de la rama que querés fusionar
console.log("Mi nueva funcionalidad");
>>>>>>> feature/cristian
```

* <<<<<<< HEAD: Indica dónde empieza el conflicto en tu rama actual.
* =======: Es el separador entre ambas versiones.
* <>>>>>> nombre-rama: Indica el final del conflicto.

* Para resolverlo se debe limpiar y marcar como resuelto, y finalmente ejecutar git commit (sin el flag -m, para que git use el mensaje de merge automatico)


### 💡 Flujo de Trabajo Grupal (Workflow)

Para integrar una funcionalidad terminada al proyecto principal:

```bash
# ir a la rama principal
git switch main

# traer lo ultimo del grupo (p/ evitar conflictos)
git pull origin main

# unir mi trabajo
git merge mi-rama

# subir todo a gitHub
git push origin main

# limpieza (opcional)
git branch -d nombre-de-rama
```