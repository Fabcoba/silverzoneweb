# SilverZone — Guía de Despliegue

## Estructura del proyecto

```
silverzone/
├── index.html          ← Página principal del catálogo
├── data/
│   └── products.json   ← Datos de los productos
├── images/             ← Fotos de los productos (subir aquí)
├── admin/
│   ├── index.html      ← Panel de administración (Decap CMS)
│   └── config.yml      ← Configuración del CMS
├── netlify.toml        ← Configuración de Netlify
└── DEPLOY.md           ← Esta guía
```

---

## Paso 1 — Subir el código a GitHub

1. Ve a https://github.com y crea una cuenta (si no tienes).
2. Crea un repositorio nuevo → llámalo `silverzone-web`.
3. Desde tu computadora, abre una terminal en la carpeta `silverzone/` y ejecuta:

```bash
git init
git add .
git commit -m "SilverZone website - primer commit"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/silverzone-web.git
git push -u origin main
```

> Reemplaza `TU_USUARIO` con tu usuario de GitHub.

---

## Paso 2 — Conectar con Netlify

1. Ve a https://netlify.com y crea una cuenta gratis.
2. Haz clic en **"Add new site"** → **"Import an existing project"**.
3. Elige **GitHub** → selecciona el repositorio `silverzone-web`.
4. En "Build settings" deja todo en blanco (no hay build step).
5. Haz clic en **"Deploy site"**.

Tu sitio estará vivo en minutos en una URL como `https://silverzone-web.netlify.app`.

> Puedes cambiar el nombre de la URL en Site settings → Domain management.

---

## Paso 3 — Activar el panel de administración (para tu mamá)

El panel está en `tudominio.com/admin` — aquí tu mamá puede agregar/editar productos sin tocar código.

**Activar Netlify Identity:**
1. En Netlify → tu sitio → **"Integrations"** → busca **"Identity"** → Enable.
2. Ve a **"Identity"** → **"Invite users"** → escribe el email de tu mamá.
3. Ella recibirá un email para crear su contraseña.

**Activar Git Gateway:**
1. En Netlify → **"Integrations"** → **"Git Gateway"** → Enable.

Listo. Tu mamá entra a `tudominio.com/admin`, hace login, y ve una interfaz para:
- Agregar nuevos productos
- Subir fotos
- Editar descripciones
- Marcar productos como destacados

Cada cambio que haga se guarda en GitHub automáticamente y el sitio se actualiza en segundos.

---

## Paso 4 — Cambiar el número de WhatsApp

Abre `index.html` y busca esta línea (cerca del final, en el `<script>`):

```js
const WA_NUMBER = '18295550000'; // ← Change this!
```

Cámbiala por el número real con código de país, sin `+` ni espacios:
```js
const WA_NUMBER = '18091234567';
```

---

## Paso 5 — Agregar fotos de los productos

Las fotos deben ir en la carpeta `images/` con el nombre del SKU del producto.

Ejemplo: para el producto `MSR3538SL`, la foto debe llamarse `MSR3538SL.jpg`.

Tu mamá puede subir fotos directamente desde el panel de admin (`/admin`) sin tocar archivos.

---

## Dominio personalizado (opcional)

Si quieres un dominio propio como `silverzone.com`:
1. Compra el dominio en Namecheap, GoDaddy, etc.
2. En Netlify → **"Domain management"** → **"Add custom domain"**.
3. Sigue los pasos para apuntar el DNS.

---

## Para ver el sitio localmente (sin subir a internet)

Instala Node.js y ejecuta:

```bash
npx serve .
```

Luego abre http://localhost:3000 en tu navegador.

---

## Ayuda

Cualquier duda con el código o el despliegue, pídele ayuda a Claude en Cowork.
