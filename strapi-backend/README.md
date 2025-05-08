# 🧠 Automat Backend – Ficha de Producto con Strapi

Este proyecto forma parte del sistema **Automat**, una solución de automatización que centraliza la gestión de fichas de producto y pedidos desde varias tiendas **Shopify**, con integración de flujos inteligentes mediante **n8n** y servicios de **IA** (como OpenAI).

El backend está construido con **Strapi (v5)** y actúa como una **API headless** conectada a una base de datos PostgreSQL (alojada en Render). Sirve como núcleo de datos para alimentar varias plataformas frontend desarrolladas en paralelo.

---

## ⚠️ Nota sobre el entorno Render

Actualmente este backend está desplegado en **Render.com** como solución temporal durante la fase de pruebas. Aunque Render es muy útil para prototipado rápido, **no admite nativamente el despliegue de n8n**, ya que requiere contenedores personalizados o servicios privados.

🧱 Por eso, el entorno final recomendado será un **servidor con sistema operativo (Ubuntu) y Docker**, donde se instalarán:
- Strapi
- PostgreSQL
- n8n
- y otros servicios de automatización o IA

Esto proporcionará mayor flexibilidad, control y escalabilidad para el proyecto real en producción.

---

## 🔗 Tecnologías usadas

- [Strapi](https://strapi.io) – API y CMS headless
- PostgreSQL – Base de datos relacional (Render)
- TypeScript – Tipado y escalabilidad
- Render – Despliegue temporal en la nube
- GitHub – Control de versiones
- n8n (próximamente) – Automatización de procesos
- OpenAI (opcional) – IA para análisis de fichas

---

# 🗄️ Configuración de PostgreSQL en Render

Para permitir que Strapi se conecte correctamente a PostgreSQL desde un entorno externo (como tu máquina local o Render Web Service), se configuró lo siguiente:

1. **Base de datos PostgreSQL creada en Render** desde `Dashboard → New → PostgreSQL`.
2. Se habilitó el acceso mediante la **External Database URL**, con formato: postgresql://USER:PASSWORD@HOST:PORT/DB_NAME?sslmode=require
3. Esta URL se definió como variable de entorno `DATABASE_URL` tanto en:
- El archivo `.env` local.
- El panel de configuración del Web Service de Render (Environment → Add Environment Variable).

4. En el archivo `config/database.ts`, se usó esta configuración simplificada:

```ts
export default ({ env }) => ({
  connection: {
    client: 'postgres',
    connection: {
      connectionString: env('DATABASE_URL'),
      ssl: {
        rejectUnauthorized: false,
      },
    },
  },
});
```

⚠️ Importante: Render solo resuelve correctamente los nombres de host internos entre sus propios servicios. Si trabajas desde local, usa siempre la URL externa que Render proporciona.


# 🚀 Getting started with Strapi

Strapi comes with a full featured [Command Line Interface](https://docs.strapi.io/dev-docs/cli) (CLI) which lets you scaffold and manage your project in seconds.

### `develop`

Start your Strapi application with autoReload enabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-develop)

```bash
npm run develop
# or
yarn develop



# 🚀 Getting started with Strapi

Strapi comes with a full featured [Command Line Interface](https://docs.strapi.io/dev-docs/cli) (CLI) which lets you scaffold and manage your project in seconds.

### `develop`

Start your Strapi application with autoReload enabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-develop)

```
npm run develop
# or
yarn develop
```

### `start`

Start your Strapi application with autoReload disabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-start)

```
npm run start
# or
yarn start
```

### `build`

Build your admin panel. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-build)

```
npm run build
# or
yarn build
```

## ⚙️ Deployment

Strapi gives you many possible deployment options for your project including [Strapi Cloud](https://cloud.strapi.io). Browse the [deployment section of the documentation](https://docs.strapi.io/dev-docs/deployment) to find the best solution for your use case.

```
yarn strapi deploy
```

## 📚 Learn more

- [Resource center](https://strapi.io/resource-center) - Strapi resource center.
- [Strapi documentation](https://docs.strapi.io) - Official Strapi documentation.
- [Strapi tutorials](https://strapi.io/tutorials) - List of tutorials made by the core team and the community.
- [Strapi blog](https://strapi.io/blog) - Official Strapi blog containing articles made by the Strapi team and the community.
- [Changelog](https://strapi.io/changelog) - Find out about the Strapi product updates, new features and general improvements.

Feel free to check out the [Strapi GitHub repository](https://github.com/strapi/strapi). Your feedback and contributions are welcome!

## ✨ Community

- [Discord](https://discord.strapi.io) - Come chat with the Strapi community including the core team.
- [Forum](https://forum.strapi.io/) - Place to discuss, ask questions and find answers, show your Strapi project and get feedback or just talk with other Community members.
- [Awesome Strapi](https://github.com/strapi/awesome-strapi) - A curated list of awesome things related to Strapi.

---

<sub>🤫 Psst! [Strapi is hiring](https://strapi.io/careers).</sub>
```


# ✨ Strapi en Local ✨

![Logo](logo.jpg)