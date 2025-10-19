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
```

### 📍 Sacando archivos del Staging Area

- Para deshacer un `git add`, el comando es:

```bash
git restore --staged nombre-del-archivo
```

📢 Es importante no olvidar ``--staged` porque sino descarta por completo todos los cambios que se hizo en ese archivo y lo revierte a la version del último commit. (es irreversible).

