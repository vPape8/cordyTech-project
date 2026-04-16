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

---
# Guia de branch y commits
##  1. Nomenclatura de Ramas (Branching)
Las ramas deben ser descriptivas y estar vinculadas a una **Issue**.
**Estructura:** `tipo/nro-issue-descripcion-breve`

| Prefijo | Uso | Ejemplo |
| :--- | :--- | :--- |
| `feature/` | Nueva funcionalidad | `feature/12-login-jwt` |
| `bugfix/` | Corrección de error en desarrollo | `bugfix/45-error-cors-react` |
| `hotfix/` | Parche crítico para producción | `hotfix/99-fuga-memoria-ec2` |
| `refactor/` | Mejora de código sin cambios funcionales | `refactor/30-limpieza-hooks-perfil` |

---

##  2. Mensajes de Commit (Conventional Commits)
Adoptaremos el estándar **Conventional Commits** para facilitar el entendimiento del historial.

**Formato:** `<tipo>: <descripción en presente>`

### Tipos permitidos:
* `feat`: Una nueva característica para el usuario.
* `fix`: Solución de un error.
* `docs`: Cambios solo en la documentación (README, Swagger).
* `style`: Cambios de formato (espacios, punto y coma) que no afectan la lógica.
* `refactor`: Cambio de código que no arregla un error ni añade una función.
* `test`: Añadir o corregir pruebas unitarias (JUnit, Jest).
* `chore`: Actualizar dependencias de Maven o npm.

**Ejemplos:**
* ✅ `feat: agregar validación de RUT en el registro de usuarios`
* ✅ `fix: corregir parpadeo en el navbar al recargar React`
* ❌ `cambios en el login` (Muy vago)
* ❌ `borré archivos que no servían` (No especifica impacto)

---

## 3. Anatomía de un Commit Perfecto
Si el cambio es complejo, usa el **cuerpo del commit** para dar contexto:

```text
feat: implementar integración con AWS S3 para fotos de perfil

- Se añade el SDK de AWS al pom.xml de Spring Boot.
- Se crea el Service para subir y eliminar objetos en el bucket.
- Se actualiza el controlador de usuario para recibir MultipartFile.

Closes #15