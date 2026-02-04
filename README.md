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


### 📍 Historial

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
git restore --source <id-commit> <nombre-del-archivo>

# alternativa al id, utilizar HEAD~1
git restore --source=HEAD~1 nombre-del-archivo # ~1 indica que se quiere volver 1 commit anterior
```

💡 Nota importante: Al ejecutar esto, el archivo en tu Working Directory cambiará automáticamente a la versión vieja. Luego deberás hacer git add y git commit para "confirmar" que querés quedarte con esa versión recuperada.

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
# -i para que no sea case-sensetive
```

### 📍 Buscar en los archivos actuales (git grep)

Para buscar un texto rapidamente en los archivos actuales se puede usar

```bash
git grep -n "texto_a_buscar"
```


## 📍 Alias

```bash
git config --global alias.gl "log --online --graph" # entre comillas lo que queremos ejecutar
```

Luego usamos el comando "git gl", y se ejecutara lo que pusimos como alias, para verificar que ese alias fue agregado usamos el comando `git config --global -e`, se podra ver una nueva sesion llamada "alias" seguido el comando y lo que se va a ejecutar.

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

### 📍 El estado "Detached HEAD" (Cabezal desprendido)

Si usás checkout para ir a un ID de commit específico en lugar de a una rama:

```bash
git checkout a1b2c3d

# Entrarás en un estado donde Git te avisa que el "HEAD" se desprendió.
```

** ⚠️ Significa que no estás parado en ninguna rama. Podés mirar el código y hacer pruebas, pero si hacés commits ahí, se perderán cuando te muevas a otra rama, a menos que crees una rama nueva en ese momento.
** 💡 Se sale de ahi simplemente volviendo a una rama con git checkout main