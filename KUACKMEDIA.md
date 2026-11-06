# Fork de kuackmedia

Fork de [ionic-team/cordova-plugin-ionic-webview](https://github.com/ionic-team/cordova-plugin-ionic-webview) en la versión `5.0.1` publicada en npm (Apache 2.0, ver `LICENSE`). Lo usan las apps Cordova de
Kuack Media para **el motor del WebView** en Android (`IonicWebViewEngine`, origen `https://localhost`) y en iOS (`CDVWKWebViewEngine`, origen `ionic://localhost`), donde viven localStorage e IndexedDB; `Ionic.WebView.convertFileSrc` y las URLs `/_app_file_`; con `WKSuspendInBackground=false`, el JS sigue corriendo en segundo plano en iOS.

Base: `9c11a20` (tag `v5.0.1`), idéntico al paquete `cordova-plugin-ionic-webview@5.0.1` de npm que las apps instalaban hasta noviembre de 2026.

El commit del tag `v5.0.1` dice `"version": "5.0.0"` en `package.json` (upstream cambiaba la versión al publicar). El commit siguiente trae el `package.json` del paquete de npm, la única diferencia: con él, el contenido es idéntico al de `cordova-plugin-ionic-webview@5.0.1` de npm.

**Lo publicado es el commit fijado en `_common/configTemplates/config-app*.xml`** del repo de las apps
(`github:kuackmedia-apps/cordova-plugin-ionic-webview#<sha>`), no la punta de una branch: un push a este repo no llega a ningún
binario hasta que se mueve ese pin, y mover el pin es un diff que se revisa. La branch `kuack` es la línea de
Kuack; `master` queda como el de upstream.

## Cambios respecto de upstream

Ninguno en el código: el fork existe para que el app dependa sólo de Apache Cordova y de repos de Kuack (fila A18 del RFP de Claro, CM-RFP-001).

## Para actualizar desde upstream

`git fetch upstream --tags`, en una branch merge (o rebase) de la versión nueva sobre `kuack`, revisar los
cambios de arriba, probarlo en un app con `config-app-local.xml` (path local del checkout), llevarlo a `kuack` y
mover el pin en los `config-app*.xml`. Nunca cambiar el `id` del plugin ni sus `clobbers`: el bundle remoto lo
comparten los binarios publicados.
