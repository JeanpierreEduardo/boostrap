# 🧁 Dulce Aurora — Pastelería online (DEMO)

Sitio web de e-commerce **ficticio** para una pastelería. Hecho con **HTML5, CSS3, JavaScript y Bootstrap 5.3.8**, totalmente adaptable a celulares, tablets y escritorio.

> ⚠️ **Importante:** Es un proyecto de demostración/portafolio. **No cobra, no envía pedidos y no tiene autenticación de producción.** Todos los precios y contactos son ficticios. No ingreses contraseñas reales.

## Vista general

- Interfaz de pastelería con portada, menú, historia, reseñas ficticias y pie de página.
- **12 productos** con fotos, ilustraciones alternativas, precios en **soles peruanos (PEN)** y botón para agregar al carrito.
- Búsqueda, filtros de categoría y ordenamiento por precio o nombre.
- Carrito lateral (offcanvas de Bootstrap) con eliminación, cantidades y subtotal.
- Cupón **`DULCE10`** que descuenta 10%; delivery simulado de **S/ 9.90** o gratis desde **S/ 90** de subtotal.
- Registro e inicio de sesión *locales* de prueba (PBKDF2 y `localStorage`). Una cuenta de prueba incluida.
- Formulario de checkout y opciones **Tarjeta demo / Yape demo / Contraentrega demo**, sin solicitar datos bancarios.
- Confirmación del pedido con código ficticio; historial asociado a la cuenta de prueba en ese mismo navegador.
- Ilustraciones SVG propias como respaldo si falla la descarga de las fotografías.
- Compatible con publicación estática en **GitHub Pages** mediante GitHub Actions.

## Probar en tu computadora

1. Descomprime el ZIP.
2. Si solo quieres ver el diseño, abre `index.html` con tu navegador. Para **probar las cuentas y pagos simulados correctamente**, te recomendamos ejecutar un servidor local.
3. Con Python instalado, dentro de la carpeta del proyecto ejecuta:

   ```bash
   python -m http.server 8000
   ```

4. Visita `http://localhost:8000/`.

El navegador necesita **conexión a Internet** para cargar Bootstrap, Bootstrap Icons, tipografías Google y fotografías Unsplash. Las imágenes tienen respaldo local en `assets/img/`.

## Acceso de prueba

En **Mi cuenta → Iniciar sesión → Entrar con una cuenta de prueba** se completa automáticamente:

- **Correo:** `demo@dulceaurora.test`
- **Contraseña:** `Demo12345!`

También puedes registrarte con un correo inventado y una contraseña **que no uses en ningún servicio real**.

### Nota sobre seguridad

El registro, la sesión y los pedidos solo se guardan en el almacenamiento de tu navegador (`localStorage`). La contraseña de prueba se deriva usando PBKDF2 con salt aleatorio, pero **esto NO convierte al navegador en un servidor seguro**. Todo el estado del carrito, cuentas y pedidos se puede modificar manualmente desde el navegador.

Para una tienda real necesitas backend, autenticación segura (p. ej. Supabase Auth), base de datos con permisos por usuario, reglas de validación del servidor, integración de pagos y controles de privacidad. **GitHub Pages solo aloja sitios estáticos y no proporciona backend**.

## Publicar en GitHub Pages

1. Ve a [github.com/new](https://github.com/new), crea un repositorio (por ejemplo, `pasteleria-dulce-aurora`) y, si quieres usar GitHub Pages gratis con cuenta personal Free, publícalo como **público**.
2. Sube **el contenido de esta carpeta** al repositorio, manteniendo `index.html` en la raíz y la carpeta `.github/workflows` (no subas el archivo ZIP dentro del repositorio).
3. Asegúrate de que la rama principal sea `main`.
4. En tu repositorio, abre **Settings → Pages → Build and deployment → Source** y selecciona **GitHub Actions**.
5. Abre la pestaña **Actions** y verifica el workflow *Publicar Dulce Aurora en GitHub Pages*; se ejecuta automáticamente al hacer push a `main`.
6. Tu web quedará en una dirección similar a:

   `https://TU_USUARIO.github.io/pasteleria-dulce-aurora/`

La URL exacta depende del nombre de tu usuario y repositorio. Si GitHub Pages no publica, revisa los logs en Actions y la configuración de Pages del repositorio.

### Subir con Git (alternativa a arrastrar archivos)

```bash
git init
git add .
git commit -m "Sitio de pastelería con carrito y checkout demo"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/pasteleria-dulce-aurora.git
git push -u origin main
```

Sustituye `TU_USUARIO` por tu nombre real de usuario de GitHub y crea antes el repositorio vacío.

## Estructura del proyecto

```text
pasteleria-dulce-aurora/
├── index.html                    # Página única + componentes de Bootstrap
├── assets/
│   ├── css/styles.css            # Estilos adaptativos personalizados
│   ├── js/app.js                 # Productos, cuenta demo, carrito y compra ficticia
│   └── img/                      # Logo + 14 ilustraciones SVG originales
├── .github/workflows/deploy.yml  # Publicación automática en GitHub Pages
├── .nojekyll                     # Compatibilidad Pages
├── .gitignore
└── README.md
```

## Personalizar productos, precios y marca

- **Catálogo y precios:** edita `const PRODUCTS` dentro de `assets/js/app.js`.
- Los precios se configuran **en céntimos**, para evitar errores de decimales: `7990` = `S/ 79.90`.
- **Envío gratis:** cambia el umbral `9000` en la función `totals()` y en `renderCart()`.
- **Descuento:** cambia el cupón `DULCE10` en `app.js`.
- **Colores:** modifica las variables al inicio de `assets/css/styles.css`.
- **Contenido:** cambia los textos, secciones y títulos de `index.html`.
- **Imágenes:** las URLs Unsplash están en `app.js` y el `index.html`, con SVG locales como respaldo.

## Tecnologías y créditos

- [Bootstrap 5.3.8](https://getbootstrap.com/docs/5.3/) — Framework CSS/JS.
- [Bootstrap Icons](https://icons.getbootstrap.com/) — Iconos.
- [Google Fonts](https://fonts.google.com/) — DM Sans y Playfair Display.
- [Unsplash](https://unsplash.com/) — Fotografías externas ilustrativas. Consultar [licencia de Unsplash](https://unsplash.com/license). Las ilustraciones SVG de respaldo fueron diseñadas para este proyecto.

**Dulce Aurora** es una marca ficticia creada como ejemplo educativo.
