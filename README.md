# Daily Store

Tienda pública (web) y panel administrativo nativo (Flutter). Copia de partida a partir de NaNa, con nombre, paquete de Android y claves del navegador propios.

- **Web:** catálogo, carrito y admin en el navegador (`npm run dev`)
- **Admin móvil/tablet:** app Flutter en `daily_store/`
- **Datos:** sigue apuntando al Firebase de NaNa (`nana-store-8b0ab`). Crea un proyecto Firebase nuevo antes de vender, y reemplaza `src/infrastructure/firebase/firebase.ts`, `daily_store/lib/core/constants/nana_firebase.dart`, `vercel.json` y `daily_store/android/app/google-services.json`.
- **Android:** el paquete es `pe.dailystore.admin`, así que se instala al lado de NaNa Admin. Hay que registrar ese paquete en el Firebase nuevo y volver a descargar `google-services.json`.

## Requisitos

- Node.js 20 o superior
- Flutter 3.32 o superior (canal estable)
- Android SDK (para la app)

## Web

```bash
npm install
npm run dev
```

Build de producción:

```bash
npm run build
```

## Admin Flutter

```bash
cd daily_store
flutter pub get
flutter run
```

APK:

```bash
cd daily_store
flutter build apk --release
```

El APK queda en `daily_store/build/app/outputs/flutter-apk/app-release.apk`.

### Google Sign-In en Android

Cada computadora tiene un SHA-1 de debug distinto. Si el login con Google falla:

1. Obtén el SHA-1:

```bash
keytool -list -v -keystore %USERPROFILE%\.android\debug.keystore -alias androiddebugkey -storepass android -keypass android
```

2. En Firebase Console → app Android `pe.dailystore.admin` → agrega ese SHA-1 (y SHA-256).
3. Descarga de nuevo `google-services.json` si Firebase lo pide y reemplaza `daily_store/android/app/google-services.json`.

PIN de la POS58: **0000**. Empareja la impresora en Bluetooth del dispositivo antes de cobrar.

## Qué hay en cada carpeta

| Ruta | Contenido |
| --- | --- |
| `src/` | Tienda y admin web (Vite + React + TypeScript) |
| `daily_store/` | Admin nativo Flutter |
| `public/` | Assets estáticos de la web |
