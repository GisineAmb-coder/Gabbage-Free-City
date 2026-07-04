# Garbage Free City (GFC)

A smart waste management platform for **Kampala Capital City Authority (KCCA)** that connects residents, waste collectors, and administrators.

## Problem

Kampala faces widespread illegal dumping and poor waste collection coordination. Residents lack a direct channel to report garbage pile-ups, collectors operate inefficiently without real-time routing, and KCCA has limited visibility into collection completion.

## Solution

GFC bridges residents, collectors, and KCCA admins through a mobile app with:

- **Report garbage** — pin pile-up locations with photos, type, and volume
- **Pay via mobile money** — integrated MarzPay for MTN/Airtel Money
- **Smart assignment** — PostGIS spatial queries dispatch the nearest collector
- **Verify collection** — collectors scan QR codes to confirm completion
- **Notifications** — SMS (EGO SMS / Africa's Talking) and in-app alerts
- **Subscription plans** — prepaid weekly/monthly packages

**Roles:** Resident → Collector → Admin, each with dedicated app screens.

## Setup

### Backend

```bash
cd backend
npm install
cp .env.example .env   # fill in Supabase, MarzPay, EGO SMS, JWT_SECRET
npm run dev            # nodemon on port 3000
npm test               # Jest + Supertest
```

### Database

Run `database/schema.sql` against a **PostgreSQL + PostGIS** instance (Supabase recommended), then apply migrations in `database/migrations/` in order. `database/demo_pricing.sql` seeds sample pricing data.

### Mobile App

```bash
cd mobile_app
flutter pub get
flutter run            # Android/iOS device or emulator
```

Update `lib/services/api_service.dart` with your backend URL.

### Deployment

A `render.yaml` is provided for deployment on Render. Set all environment variables per `.env.example`.
