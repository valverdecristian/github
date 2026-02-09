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
- Atajo Pro: -am Combina git add y git commit en un solo paso: git commit -am "mensaje". (Solo funciona con archivos que Git ya rastrea)


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
git push origin nombre-etiqueta

# Subir TODAS las etiquetas que tengas localmente
git push origin --tags

# si quiero eliminar la etiqueta subida
git push origin --delete nombre-etiqueta
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
# Forma clasica
git checkout -b nueva-rama # -b significa branch

# Forma moderna
# -c (minúscula): Crea una rama nueva. Si ya existe, Git da error para proteger tu trabajo.
git switch -c nueva-rama

# -C (MAYÚSCULA): Crea la rama o la RESETEA si ya existía.
# Útil para "reiniciar" una rama desde tu posición actual.
git switch -C rama-existente
```

⚠️ Advertencia sobre -C: Usalo con cuidado, ya que si la rama existía, "teletransporta" el puntero a donde estás parado ahora y perdés los commits previos que tuviera esa rama.

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

#### 🌱 Nomenclatura de Ramas (El estándar profesional)

* **feat/**: para nuevas funcionalidades.
* **fix/**: para correccion de errores.
* **docs/**: solo cambios en documentación.
* **refactor/**: mejoras en el código que no cambian la lógica.


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

## 🔀 Gestion de Ramas (Branching)

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


### 📍 Aplicar commits específicos (git cherry-pick)

Permite traer un commit puntual de cualquier rama a nuestra rama actual sin necesidad de hacer un merge completo.

```bash
# 1. Identificar el commit en la otra rama
git log --oneline

# 2. Ir a la rama destino, por ej: main
git checkout main

# 3. Hacer el Cherry-pick
git cherry-pick id-commit
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


### 📍 Diccionario de Punteros

Cuando ves un git log, los nombres en colores entre paréntesis indican:
* HEAD: Mi ubicación actual (donde estoy parado).
* nombre-rama: El último commit de esa rama en mi computadora.
* origin/nombre-rama: El último commit que se subió a GitHub (el servidor remoto).

📢 Estado Ideal: Cuando ves (HEAD -> main, origin/main), significa que tu trabajo local y el remoto coinciden. ¡Estás al día!


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

📢 Para resolverlo se debe limpiar y marcar como resuelto, y finalmente ejecutar git commit (sin el flag -m, para que git use el mensaje de merge automatico).
📢 En VSCode podemos resolverlo tambien apretando "Resolve in Merge Editor"


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

# limpieza local (opcional)
git branch -d nombre-de-rama

# limpieza remota
git push origin -d nombre-de-rama
```


### 📍 Deshacer un Merge ya publicado (git revert -m 1)

Si fusionaste una rama a main por error y ya hiciste push a GitHub, no podés borrar el historial. Debés crear un commit que deshaga la fusión.

Mientras que git revert se usa para deshacer un commit normal, git revert -m 1 HEAD se utiliza específicamente para deshacer un Merge Commit (un commit de fusión) que ya fue enviado al repositorio remoto.

Cuando haces un commit normal, este tiene un solo "padre" (el commit anterior). Pero un Merge Commit tiene dos padres: uno de la rama principal (ej. main) y otro de la rama que integraste (ej. feature/login).

* -m 1: Le indica a Git que debe mantener como línea principal (mainline) al primer padre. Casi siempre, el padre 1 es la rama en la que estabas parado cuando hiciste el merge (generalmente main).

```bash
# Revertir el merge commit actual manteniendo la línea de 'main'
git revert -m 1 HEAD
```

📢 Dato clave: Usá esto solo si el merge ya está en GitHub. Si el error es solo local, es más fácil usar git reset --hard para volver atrás.

🛠️ ¿Cuándo usarlo?: Imagina que fusionaste la rama de un compañero a main, hiciste push a GitHub, y de repente la aplicación de NestJS deja de compilar o el Angular explota en producción.

Como ya subiste los cambios, no puedes usar reset porque borrarías el historial de tus compañeros. Debes usar revert


### 📍 Reorganizar la Historia (git rebase)

* Significa cambiar la base de tu rama a la punta de otra rama (generalmente main)
* Usarlo solo si un solo desarrollador esta usando esa rama.

Cuando hacés un rebase de tu rama sobre main, lo que hacés es tomar todos tus commits, "despegarlos" temporalmente, actualizar tu rama para que empiece desde el último commit de main, y luego volver a "pegar" tus cambios uno por uno encima.

Mientras que el merge crea un commit extra para unir las historias (un historial ramificado), el rebase reescribe la historia para que parezca que siempre estuviste trabajando sobre la versión más nueva de main.

⚠️ "Nunca hagas rebase de una rama que ya subiste a GitHub y que otros están usando".

```bash
# Estando en nuestra rama de funcionalidad:
git rebase main
```

* ✅ Ventaja: Evita los "Merge Commits" innecesarios y deja un historial fácil de seguir.
* ❌ Peligro: Reescribe la historia. Solo se debe usar en ramas locales que no hayan sido compartidas en GitHub.


### 📍 Squash Merge (El Compactador)

El Squash Merge es una técnica de fusión que funciona como un "compactador" de commits. En lugar de traer toda la historia detallada de una rama, toma todos los commits que hiciste en ella y los combina en un solo commit nuevo en la rama de destino (generalmente main).

Toma todos los commits de una rama y los une en uno solo al fusionarlos con main.

* Ventaja: Mantiene el historial principal limpio de commits innecesarios o mensajes poco descriptivos.

* Desventaja: Se pierde el detalle de los pasos intermedios que se realizaron en la rama de funcionalidad.

* Comando local: `git merge --squash rama`

* En GitHub: Se activa al cerrar un Pull Request con la opción "Squash and merge".

📢 Dato de oro: Es la opción favorita en entornos profesionales para que el historial de producción sea impecable y fácil de auditar.


## ☁️ GitHub y Colaboración

### 📍 Fork: Tu propio laboratorio

Se utiliza para copiar un repositorio ajeno a tu cuenta de GitHub. Esto te permite experimentar sin afectar el proyecto original.

* Flujo de trabajo:

1) En GitHub seleccionar `Fork` (esto creara una copia)
2) Clonar el fork: `git clone url-de-tu-fork`
3) Configurar el remoto original (upstream): para poder traer las actualizaciones que se hagan en el repo original.

```bash
# Agregar el repositorio original como una fuente llamada 'upstream'
git remote add upstream URL_DEL_REPO_ORIGINAL

# Verificar tus remotos (deberías ver origin y upstream)
git remote -v
```

4) Si el repo original cambia, sincronizar los cambios en mi PC

```bash
git pull upstream main
```

💡 Fetch vs Pull (Diferencia clave)
* fetch: Trae la información pero no toca tu código. Actualiza upstream/main.
* pull: Trae la información y la fusiona inmediatamente (fetch + merge).

5) Una vez que termino algo en mi fork, uso un **Pull Request (PR)** para pedirle al dueño del repo que incorpore mis cambios.

#### 📢 Tip de "Cultura Dev"

A veces, si el cambio es muy pequeño (como corregir un error de ortografía en el README), se usa "LGTM concept", que significa: "Me parece bien la idea, pero revisá este detalle mínimo antes de mergear".

La tradición: A menudo se acompaña de emojis como un barco (🚢) que significa "Ship it!" (¡Enviálo/Publicalo!) o un pulgar arriba (👍).

### 📍 Clonar un repositorio

```bash
git clone url-repositorio opcional-nuevo-nombre
```

### 📍 Inspección Remota (git fetch)

Descarga el historial y los cambios del repositorio remoto pero no los fusiona con tu trabajo local. Es una forma segura de ver qué hicieron los demás antes de integrar.

```bash
# Descargar cambios de mi fork
git fetch origin
```

📢 **Diferencia técnica:** `git pull` hace un `fetch` y un `merge` al mismo tiempo. Usar `fetch` primero te permite revisar los cambios con `git log` o `git diff` antes de afectar tu código.

💡 Recordá que cuando hacés fetch, el puntero que se mueve es el de origin/main. Tu puntero main se queda donde estaba hasta que hagas el merge.

### 📍 Listado Detallado de Ramas (git branch -v)

A diferencia del comando git branch seco (que solo te da los nombres), el flag -v te muestra una "radiografía" rápida de tus ramas.

🚀 El "Siguiente Nivel": git branch -vv

```bash
# Listar ramas (solo nombres)
git branch

# Listar ramas con su último commit y mensaje (Verbose)
git branch -v

# Listar ramas con info de seguimiento remoto (Very Verbose)
# Ideal para saber si te falta hacer un push o un pull
git branch -vv
```

### ⚠️ Nota de Seguridad

* Nunca uses git push -f en ramas compartidas (como main o develop).

El comando git push -f (o --force) es como el botón de "borrón y cuenta nueva" para el repositorio remoto. En el contexto de tus proyectos en la UTN, es una herramienta que debés manejar con muchísimo cuidado porque puede generar caos en el trabajo de tus compañeros.

📢 Regla de oro: Si necesitás deshacer algo que ya está en GitHub, es mucho más profesional y seguro usar git revert, ya que crea un commit nuevo que deshace el anterior sin borrar el historial.


### 📍 Autenticación: Personal Access Token (PAT)

El Personal Access Token (PAT) es, esencialmente, tu contraseña para que Git pueda comunicarse con GitHub desde la terminal. Desde hace un tiempo, GitHub ya no permite usar tu contraseña de usuario para operaciones de Git (como push o pull) por motivos de seguridad; ahora exige este token.

#### 🛠️ Cómo crearlo

1) En GitHub: Vas a Settings (tu perfil) > Developer settings > Personal access tokens.
2) Elegir tipo: * Fine-grained tokens: Son los modernos y más seguros (podés elegir exactamente a qué repositorio darle acceso).
  - Tokens (classic): Son los tradicionales y más fáciles de configurar para empezar.
3) Configurar permisos: Si usás el Classic, asegurate de marcar la casilla repo (para poder hacer push/pull).
4) Generar y Guardar: Al final hacés clic en Generate token.

* Copiar y Guardar: GitHub solo te mostrará el token una vez. Si cerrás la pestaña sin copiarlo, lo perdés y tenés que crear uno nuevo.
* No compartir, ni subir el token a un repo.
* Se puede configurar para que el token expire en 30, 60 o 90 dias.
* 📢 Este token se usa cuando te pide la contraseña.


### 📍 Lanzamientos y Versiones del Proyecto (GitHub Releases)

El botón de Releases en GitHub es el paso final que convierte tu código en un "producto" terminado. Mientras que los Tags son marcas técnicas en tu historial, una Release es una forma elegante y organizada de entregar tu software a otros usuarios.

Una Release en GitHub es un "envoltorio" que se coloca sobre un Git Tag existente. Sirve para empaquetar una versión específica de tu proyecto.

#### 🌟 ¿Qué beneficios tiene sobre un simple Tag?

* Notas de Lanzamiento (Changelog): Podés escribir una descripción detallada de qué hay de nuevo, qué errores se corrigieron y qué funcionalidades se agregaron.
* Archivos Adjuntos (Assets): Podés subir archivos compilados, como un .exe de tu juego, un archivo .apk o un ZIP con documentación extra que no querés que ensucie el código fuente.
* Etiqueta "Latest": GitHub marca automáticamente la versión más reciente como "Latest" para que nadie se confunda de versión.
* Pre-releases: Podés marcar versiones como "Pre-release" (betas) si el código todavía es inestable.

#### 🛠️ Cómo crear una Release desde la web

1) En tu repositorio de GitHub, buscá la sección Releases a la derecha y hacé clic en "Create a new release".
2) Choose a tag: Podés elegir un tag que ya hayas subido con git push --tags o crear uno nuevo en ese momento.
3) Título y Descripción: Dale un nombre (ej: v1.0.0 - Entrega Final) y detallá los cambios.
4) Adjuntar: Si tenés algún manual de usuario en PDF o un ejecutable, arrastralo a la zona de carga.
5) Publicar: Hacé clic en Publish release.


### 📍 Gestión de Tareas (Issues)

Las Issues (Incidencias) son el "To-Do list" del proyecto. Se usan para debatir ideas, reportar errores y asignar tareas al equipo.

Para que una Issue sea útil para el grupo, se debe usar estos tres elementos:

* **Assignees (Asignados):** Define quién trabaja en la tarea.
* **Labels (Etiquetas):** Categoriza la tarea (Bug, Feature, Docs).
* **Milestones (Hitos):** Agrupa tareas por fechas de entrega (ej: "Final Mayo").

📢 **Tip de Automatización:** Si en un Pull Request escribís `Closes #numero_issue`, GitHub cerrará la tarea automáticamente cuando se haga el merge.

#### 📍 ¿Cómo cerrar una Issue?

* Manual: Botón Close issue en la web.
* Por Commit: Usar Closes #nro en el mensaje del commit (ej: git commit -m "feat: login closes #5").
* Por Pull Request: Escribir Closes #nro en la descripción del PR.

📢 Dato: Usar el número de la issue vincula automáticamente el código con la tarea, dejando un rastro claro de por qué se hizo ese cambio.