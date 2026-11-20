# Daily Store (Flutter)

Panel administrativo nativo para tablet y celular. Comparte catálogo, pedidos y usuarios con la web.

## Correr

```bash
cd daily_store
flutter pub get
flutter run
```

## APK

```bash
flutter build apk --release
```

Salida: `build/app/outputs/flutter-apk/app-release.apk`.

El paquete Android es `pe.dailystore.admin`. El login con Google usa el Firebase que esté en `google-services.json`. Hoy ese archivo sigue siendo el de NaNa hasta que registres la app en un proyecto nuevo.
