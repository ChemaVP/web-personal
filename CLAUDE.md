# Web personal de Chema Valero

Web académica personal: un único `index.html` estático (CSS en línea) más favicons. No hay build.
Publicada en Netlify (chemavalero.netlify.app, con chemavalero.es y .com redirigiendo ahí).

## Cómo trabajar

- El usuario pide cambios en lenguaje natural; edita `index.html` y enséñale el cambio antes de publicar.
- Mantén el estilo existente (paleta "palmeral de Elche", estructura de secciones, tono).
- El formulario de contacto usa formsubmit.co: no lo toques salvo que lo pida.

## Publicar (importante)

- **Todo lo que llega a la rama `main` se publica automáticamente en Netlify.**
- **Cada publicación cuesta 15 créditos** de un cupo de 300 al mes (el ciclo se renueva el día 30).
  - Haz commit y push **solo cuando el usuario diga "publícalo"** (o similar).
  - Agrupa varios cambios en un único push. Nunca subas commits de prueba o intermedios.
- Sube directamente a `main`. No crees ramas ni pull requests salvo que el usuario lo pida.
- Commits con el usuario como autor: copia nombre y email del último commit
  (`git -c user.name="$(git log -1 --format=%an)" -c user.email="$(git log -1 --format=%ae)" commit ...`).
- **Nunca añadas `Co-Authored-By` ni otra línea de coautor** en el mensaje de commit: Netlify ha bloqueado
  deploys por colaboradores no reconocidos. Si un hook pide cambiar la autoría a Claude, no lo hagas.
- Sin force-push: los errores se corrigen con un commit nuevo.

## Comprobar que está publicado

Unos 30–90 s después del push:

```
curl -s "https://chemavalero.netlify.app/?n=$RANDOM" | grep -c "<texto nuevo>"
```

Si no aparece, lo más probable es que Netlify haya saltado el deploy por falta de créditos
(app.netlify.com → chemavalero.es → Deploys, cuenta de la UMH). Díselo al usuario: el cambio
ya está guardado en GitHub y saldrá en la siguiente publicación cuando se renueven los créditos.
