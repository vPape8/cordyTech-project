# Cheat Sheet de Git

Esta guía contiene los comandos esenciales para el flujo de trabajo diario en el desarrollo de microservicios.

---

### Fase 1: Inicio del día y Sincronización
Antes de empezar a programar, asegúrate de tener la última versión del código del equipo.

* **Cambiar a la rama principal:**
    `git checkout main`
* **Descargar cambios del servidor:**
    `git pull origin main`
* **Crear una nueva rama para tu tarea:**
    `git checkout -b feature/id-descripcion`
* **Listar tus ramas locales:**
    `git branch`

---

### Fase 2: Desarrollo y Guardado (Local)
Utiliza estos comandos mientras avanzas en tu código de Spring o React.

* **Ver qué archivos has modificado:**
    `git status`
* **Ver cambios específicos línea por línea:**
    `git diff`
* **Preparar todos los cambios para guardar:**
    `git add .`
* **Guardar cambios con un mensaje profesional:**
    `git commit -m "feat: descripción del cambio"`

---

### Fase 3: Envío al Servidor (Remote)
Una vez que tu código funciona localmente, súbelo a GitLab.

* **Subir tu rama por primera vez:**
    `git push origin nombre-de-tu-rama`
* **Actualizar info de ramas remotas:**
    `git fetch --all`
* **Borrar rama local (tras aceptar el Merge Request):**
    `git branch -d nombre-rama`

---

### Fase 4: Resolución de Conflictos
Si Git te avisa de un conflicto al intentar unir tu código con `main`:

1.  **Asegura tu `main`:** `git checkout main` -> `git pull origin main`
2.  **Vuelve a tu rama:** `git checkout mi-rama`
3.  **Fusiona los cambios:** `git merge main`
4.  **Limpia el código:** Abre VS Code, busca las marcas de conflicto (<<<<<<< HEAD), elige el código correcto y guarda.
5.  **Finaliza:**
    `git add .`
    `git commit -m "fix: resolver conflictos con main"`
    `git push origin mi-rama`

---

> **Tip:** No satures el repositorio.Usa siempre `git status` antes de hacer un `add` para confirmar que no estás subiendo archivos temporales o carpetas pesadas como `node_modules`.