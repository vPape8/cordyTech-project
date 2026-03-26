# Guía de Mirroring y Buenas Prácticas (GitLab → GitHub)

El objetivo es que trabajen en **GitLab** (donde están las herramientas de equipo) y que su perfil de **GitHub** se encuentre siempre actualizado para mostrar su portafolio de forma automática.

---

## Paso A: Preparar GitHub
1. **Crear repositorio:** Crea un repositorio vacío en GitHub con el mismo nombre que el proyecyo de gitlab (sin README, sin licencia, sin `.gitignore`).
2. **Generar Token:** Ve a `Settings` > `Developer Settings` > `Personal Access Tokens` > `Tokens (classic)`.
3. **Permisos:** Genera un nuevo token con el permiso **repo** activado. 
   >  **Nota: Cópialo de inmediato; no volverás a verlo.**

## Paso B: Configurar el Mirror en GitLab
1. En tu proyecto de GitLab, ve a **Settings** > **Repository**.
2. Expande la sección **Mirroring repositories**.
3. Completa los datos:
   * **Git repository URL:** URL de tu repo de GitHub (ej: `https://github.com/tu-usuario/tu-repo.git`).
   * **Mirror direction:** `Push`.
   * **Authentication method:** `Password` (aquí pegas el **Token** generado en el Paso A).
4. Haz clic en **Mirror repository**.

*Nota: Cada vez que hagas un push a GitLab, los cambios viajarán a GitHub automáticamente en unos minutos.*

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
