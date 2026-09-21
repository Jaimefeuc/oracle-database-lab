# Preguntas de Comprobación - Laboratorio 1

1. **¿Diferencia entre Working Directory, Staging Area y Local Repository?**
   - *Working Directory:* Es el directorio de trabajo actual en el disco donde se crean y modifican archivos.
   - *Staging Area:* Zona intermedia donde se preparan y seleccionan los cambios exactos (`git add`) que formarán el próximo commit.
   - *Local Repository:* El historial permanente de cambios guardado en la carpeta `.git` tras hacer `git commit`.
   - *Ejemplo:* Creo `notas.txt` (Working Directory) -> Ejecuto `git add notas.txt` (Staging Area) -> Ejecuto `git commit` (Local Repository).

2. **Si modifico un archivo pero no hago `git add`, ¿aparece en el próximo commit?**
   No, porque `git commit` solo empaqueta los cambios que se encuentran explícitamente dentro de la Staging Area.

3. **¿Por qué `git status` no mostraba carpetas vacías y cómo lo solucionamos?**
   Git versiona archivos, no carpetas vacías. Lo solucionamos creando un archivo placeholder llamado `.gitkeep` dentro de cada carpeta vacía.

4. **Explica qué es HEAD:**
   HEAD es un puntero o referencia que indica en qué commit o rama activa te encuentras posicionado en tu Working Directory.

5. **¿Diferencia entre `git switch -c` y `mkdir`?**
   `mkdir` crea una carpeta física en el sistema de archivos. `git switch -c` crea una nueva línea de desarrollo (puntero a un commit) dentro de Git sin duplicar carpetas físicas. Lo comprobamos al ver que el contenido de las carpetas cambiaba en el disco al cambiar de rama sin crear directorios nuevos.

6. **En el conflicto de la Parte H, ¿qué representaban los marcadores?**
   - Entre `<<<<<<< HEAD` y `=======`: El contenido existente en tu rama activa (`main`).
   - Entre `=======` y `>>>>>>>`: El contenido que venía de la rama que intentabas fusionar (`fix/readme-subtitle`).

7. **¿Por qué NO hacer `git commit --amend` sobre commits ya subidos con `git push`?**
   Porque `--amend` reescribe el historial cambiando el ID (hash) del commit. Si ya se subió a GitHub, provocará divergencias e incompatibilidades con los repositorios de otros colaboradores.

8. **Si borras la carpeta `.git`, ¿qué se pierde y qué pasa con el código?**
   Se pierde todo el historial de commits, ramas y configuraciones locales de Git. El código fuente actual en el disco se mantiene intacto, pero deja de ser un repositorio de Git.

9. **Diferencia entre Git y GitHub (sin usar la palabra "nube"):**
   Git es la herramienta software local que gestiona el control de versiones en tu ordenador. GitHub es un servidor web centralizado donde alojas copias de repositorios Git para colaborar con otros desarrolladores.

10. **¿Por qué no subir un `.env` con contraseñas reales a un repositorio privado?**
    Porque los datos quedan registrados de forma permanente en el historial de commits. Además, cualquier usuario con acceso al repositorio (o si el repo se vuelve público por error) podría ver las credenciales.

11. **Error 'non-fast-forward' al hacer push:**
    Significa que el repositorio remoto tiene commits más recientes que tu copia local (por ejemplo, cambios hechos en la web). Primero ejecutaría `git pull` para traer y fusionar los cambios, y luego haríais `git push`.

12. **Tipo de Conventional Commit para los ejemplos:**
    - Añadir un índice de rendimiento a una tabla: `perf(db)` o `refactor(db)`
    - Corregir una restricción mal definida: `fix(db)`
    - Actualizar el README: `docs`