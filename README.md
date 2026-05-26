# GrokBot — Chatbot Builder con xAI Grok

Chatbot configurable con personalidad, instrucciones y archivos de contexto, desplegado en Railway.

## Stack

- **Backend**: Node.js + Express
- **Frontend**: HTML/CSS/JS puro (sin frameworks)
- **API**: xAI Grok (`api.x.ai/v1`)
- **Deploy**: Railway

## Estructura

```
grokbot/
├── server.js          # Servidor Express
├── package.json
├── .gitignore
├── README.md
└── public/
    └── index.html     # App completa del chatbot
```

## Deploy en Railway

### 1. Crear repo en GitHub

```bash
git init
git add .
git commit -m "feat: initial grokbot setup"
git remote add origin https://github.com/TU_USUARIO/grokbot.git
git push -u origin main
```

### 2. Subir a Railway

1. Ir a [railway.app](https://railway.app) y hacer login
2. Click en **New Project → Deploy from GitHub repo**
3. Seleccionar tu repo `grokbot`
4. Railway detecta automáticamente Node.js y corre `npm start`
5. En 2-3 minutos tu app está online con una URL pública

### 3. Variables de entorno (opcional)

Si querés fijar una API key del lado del servidor (para no pedirla al usuario):

En Railway → tu proyecto → Variables:
```
XAI_API_KEY=xai-tu-api-key-aqui
```

Luego en `server.js` podés leerla con `process.env.XAI_API_KEY`.

## Desarrollo local

```bash
npm install
npm run dev   # usa nodemon con hot-reload
```

Abre http://localhost:3000

## Endpoints

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | `/` | Frontend del chatbot |
| POST | `/api/chat` | Proxy hacia xAI API |
| POST | `/api/upload` | Subida de archivos de contexto |
| GET | `/health` | Health check para Railway |
