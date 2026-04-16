# Guía de Mirroring y Buenas Prácticas (GitLab → GitHub)

El objetivo es que trabajen en **GitLab** (donde están las herramientas de equipo) y que su perfil de **GitHub** se encuentre siempre actualizado para mostrar su portafolio de forma automática.

---

## Paso A: Preparar GitHub
1. **Crear repositorio:** Crea un repositorio vacío en GitHub con el mismo nombre que el proyecto de gitlab (sin README, sin licencia, sin `.gitignore`).
2. **Generar Token:** Ve a tú perfil  `Settings` > `Developer Settings` > `Personal Access Tokens` > `Tokens (classic)`.
3. **Permisos:** Genera un nuevo token (sugerencia de nombre: token Gitlab) con el permiso **repo** activado. 
   >  **Nota 1: Cópialo y guardalo de inmediato; no volverás a verlo.**
   >  **Nota 2: Revisa la fecha de duracion del token**

## Paso B: Configurar el Mirror en GitLab
1. En tu proyecto de GitLab, ve a **Settings** > **Repository**.
2. Expande la sección **Mirroring repositories**.
3. Completa los datos:
   * **Git repository URL:** URL de tu repo de GitHub (ej: `https://github.com/tu-usuario/tu-repo.git`).
   * **Mirror direction:** `Push`.
   * **Authentication method:** `Password` (aquí pegas el **Token** generado en el Paso A).
4. Haz clic en **Mirror repository**.

*Nota: Cada vez que hagas un push a GitLab, los cambios viajarán a GitHub automáticamente en unos minutos.*
