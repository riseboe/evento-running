# Montevideo Running 2026 - Documentación y Lecciones Aprendidas

Este documento recopila las lecciones, técnicas de desarrollo y estándares de trabajo implementados durante la creación de este proyecto.

## 1. Técnicas de CSS Moderno y UI

### Tipografía Responsiva con `clamp()`
En lugar de depender exclusivamente de múltiples *media queries*, implementamos la función `clamp(MIN, PREFERRED, MAX)` para los textos principales (como el H1 del Hero). Esto permite que el tamaño de la fuente escale fluidamente según el ancho de la pantalla (`vw`), manteniéndose siempre dentro de unos límites legibles (mínimo y máximo en `rem`).

### Textos con Gradientes
Para aplicar gradientes sobre texto, utilizamos la técnica de recorte de fondo en lugar de colores sólidos. Los pasos esenciales son:
1. Aplicar el degradado a la propiedad `background` del elemento.
2. Utilizar `background-clip: text` (incluyendo su versión `-webkit-`) para que el fondo solo se dibuje dentro de los caracteres.
3. Hacer que el color original del texto sea transparente (`color: transparent` y `-webkit-text-fill-color: transparent`).
> **Consideración importante:** Al aplicar este efecto en elementos en línea (como etiquetas `<span>`), es necesario forzar un `display: inline-block;` para que el navegador calcule correctamente la caja delimitadora (bounding box) y el gradiente se renderice sin parpadeos o cortes.

### Efectos de Fundido en Imágenes (Masking)
Para lograr que la imagen principal del Hero se funda suavemente con el color de fondo oscuro de la página, utilizamos la propiedad `mask-image` (y `-webkit-mask-image`). Mediante un `linear-gradient` de negro sólido a transparente, logramos ocultar gradualmente la parte inferior de la imagen.

---

## 2. Estandarización del Flujo de Trabajo (Git)

### Conventional Commits
Para mantener un historial limpio y profesional, estandarizamos nuestros mensajes de commit usando prefijos semánticos:
* `feat:` Nueva característica o sección.
* `fix:` Solución de errores o bugs.
* `style:` Cambios en la interfaz, diseño visual o CSS que no afectan la lógica.
* `refactor:` Mejoras en la estructura del código sin cambiar su comportamiento.
* `docs:` Modificaciones en archivos como este README.

### Procedimiento Estándar de Guardado
Cada bloque de trabajo finalizado debe seguir este ciclo:
1. `git status` -> *Verificar archivos modificados.*
2. `git add .` -> *Preparar los cambios (o añadir archivos específicos).*
3. `git commit -m "tipo: descripción clara del cambio"` -> *Registrar usando el estándar.*
4. `git pull origin main` -> *Sincronizar cambios remotos (opcional/recomendado en equipo).*
5. `git push origin main` -> *Subir al servidor remoto.*

---
*Proyecto desarrollado por Sparrows 🐦‍⬛.*