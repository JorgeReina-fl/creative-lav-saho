# Creative Lav Saho 🎨

E-commerce de productos personalizados (carcasas, tazas, totebags, regalos) con personalizador interactivo en tiempo real.

**Live:** https://creativelav.jorgereina.com

## Stack

- **Next.js 15** + TypeScript
- **Fabric.js** — personalizador interactivo de productos
- **Stripe** — pagos y checkout
- **Zustand** — estado global del carrito
- **PostgreSQL** — datos via Admin Panel API

## Arquitectura

El frontend consume datos dinámicos desde un Admin Panel SaaS multi-tenant:
- Productos, categorías y precios gestionados desde `admin.jorgereina.com`
- Imágenes servidas desde el volumen Docker del admin panel
- Personalizador configurable por producto via campo `customizer` (JSON)

## Variables de entorno

```env
NEXT_PUBLIC_ADMIN_API_URL=https://admin.jorgereina.com/api
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=pk_...
STRIPE_SECRET_KEY=sk_...
```

## Desarrollo local

```bash
npm install
npm run dev
```

## Deploy

Dockerizado en Oracle Cloud (ARM A1 Flex) con Nginx como proxy inverso.

```dockerfile
docker compose up -d --build creative-lav-saho
```
