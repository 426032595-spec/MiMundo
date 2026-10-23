# Bóveda de apuntes para Android

Proyecto Capacitor listo para compilar. La app web está en `www/index.html`.

## Opción A: compilar gratis en GitHub (sin instalar nada)

1. Crea una cuenta en https://github.com y un repositorio nuevo, privado si quieres.
2. Sube todo el contenido de esta carpeta al repositorio (en la web: «Add file» > «Upload files»).
   Importante: sube también la carpeta oculta `.github`.
3. En el repositorio abre la pestaña «Actions» > «Compilar APK» > «Run workflow».
4. Cuando termine (unos 5 a 10 minutos), entra a esa ejecución y descarga `boveda-de-apuntes-apk` (es un zip con `app-debug.apk`).

## Opción B: compilar en tu PC con Linux

```
sudo apt install openjdk-21-jdk unzip
mkdir -p ~/android-sdk/cmdline-tools && cd ~/android-sdk/cmdline-tools
# Descarga «Command line tools only» (Linux) de https://developer.android.com/studio#command-line-tools-only
unzip ~/Descargas/commandlinetools-linux-*_latest.zip
mv cmdline-tools latest
export ANDROID_HOME=~/android-sdk
yes | $ANDROID_HOME/cmdline-tools/latest/bin/sdkmanager --licenses
$ANDROID_HOME/cmdline-tools/latest/bin/sdkmanager "platform-tools" "platforms;android-36" "build-tools;36.0.0"
```

Luego, dentro de esta carpeta (necesitas Node 22 o más nuevo):

```
echo "sdk.dir=$HOME/android-sdk" > android/local.properties
npm install
npm run build:apk
```

El APK queda en `android/app/build/outputs/apk/debug/app-debug.apk`.

## Instalarlo en el celular

1. Pasa `app-debug.apk` al teléfono (cable, Drive o correo).
2. Ábrelo desde el administrador de archivos. Android pedirá permiso para «instalar apps de origen desconocido».
3. Acepta e instala. Aparece como «Bóveda de apuntes».

Es un APK de depuración firmado con la llave de prueba de Android. Sirve para uso personal.

## Respaldo

Tus notas se guardan en el teléfono. «Respaldo > Exportar» genera un `.json` y abre el menú de compartir para guardarlo en Drive o enviarlo. Si desinstalas la app, se borran las notas del teléfono, así que exporta antes.
