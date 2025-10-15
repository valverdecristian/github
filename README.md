# Ultimate Git + GitHub 🚀 ✅ 📢 👉 💡

## 📌 Git

### 📍 ¿Qué es Git?
Es un sistema de control de versiones, que nos permite gestionar cambios en los archivos de código de forma eficiente.

### 📍 Beneficios de Git
* ✔ Guardar el historial de cambios.
* ✔ Recuperar versiones anteriores.
* ✔ Permitir colaboración en equipo.
* ✔ Permite trabajar de forma remota o local.

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

### 📂 Primeros Pasos con Git

1️⃣ Crear un Repositorio
```bash
git init nombre-del-repo
cd nombre-del-repo
```
📢 Esto crea un repositorio vacío en la carpeta indicada.
📢 Si ya estoy en la carpeta donde voy a trabajar solo uso 'git init'

<br>

2️⃣ Agregar Archivos al Repositorio
```bash
git add archivo.txt
```

<br>

3️⃣ Hacer un Commit (Guardar Cambios en nuestro repositorio)
```bash
git commit -m "mensaje descriptivo del cambio"
```

<br>

4️⃣ Ver el Estado del Repositorio
```bash
git status
```

<br>

5️⃣ Ver el Historial de Cambios
```bash
git log
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

- desde la Terminal.
- desde nuestro editor de codigo/IDE.
- desde nuestras herramientas graficas (GUI).

<br>

### 📍