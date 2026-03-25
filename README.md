# Dashboard Control de Cobranza — PF & VU

Dashboard HTML autocontenido para gestión de cobranza de Protección Familiar y Valles Unidos.

## Despliegue en Netlify (paso a paso)

### 1. Subir a GitHub
```bash
git init
git add .
git commit -m "Initial deploy — Dashboard Cobranza"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/dashboard-cobranza.git
git push -u origin main
```

### 2. Conectar con Netlify
1. Ir a [app.netlify.com](https://app.netlify.com)
2. Clic en **"Add new site" → "Import an existing project"**
3. Seleccionar **GitHub** y autorizar acceso
4. Elegir el repositorio `dashboard-cobranza`
5. Configuración de build:
   - **Branch to deploy:** `main`
   - **Build command:** *(dejar vacío)*
   - **Publish directory:** `.`
6. Clic en **"Deploy site"**

### 3. URL personalizada (opcional)
En Netlify → Site settings → Domain management → Add custom domain

## Actualizar el dashboard
Cada vez que hagas push a `main`, Netlify redespliega automáticamente:
```bash
git add index.html
git commit -m "Actualización dashboard vX.X"
git push
```

## Archivos del repositorio
| Archivo | Descripción |
|---|---|
| `index.html` | Dashboard principal (autocontenido) |
| `netlify.toml` | Configuración headers y build de Netlify |
| `.gitignore` | Archivos ignorados por Git |
| `README.md` | Este archivo |

## Dependencias externas (CDN)
El dashboard carga las siguientes librerías desde CDN al abrirse:
- SheetJS (XLSX) — lectura de archivos Excel
- Chart.js — gráficas
- chartjs-plugin-datalabels — etiquetas en gráficas

## Seguridad
- Los datos Excel se procesan **100% en el navegador** del usuario
- Ningún dato se envía a servidores externos
- IndexedDB almacena datos solo localmente en el navegador
- Configurado con headers de seguridad (X-Frame-Options, nosniff)
