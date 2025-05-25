# Gestor de Contraseñas Web Local y Seguro

Un gestor de contraseñas sencillo pero robusto que se ejecuta completamente en tu navegador. Tus contraseñas se almacenan cifradas en el almacenamiento local de tu navegador y solo se pueden acceder mediante una contraseña maestra que tú estableces. ¡Ningún dato sale de tu ordenador!

## Características Principales

* **Totalmente Local y Privado:** No requiere conexión a internet ni envía tus datos a ningún servidor. Todo se procesa y almacena en tu navegador.
* **Cifrado Fuerte:** Utiliza el algoritmo AES-GCM de 256 bits para cifrar tu bóveda de contraseñas.
* **Contraseña Maestra Segura:** La clave para cifrar/descifrar tu bóveda se deriva de tu contraseña maestra usando PBKDF2 con 100,000 iteraciones y un salt único, lo que dificulta los ataques de fuerza bruta.
* **Gestión Completa:**
    * Añade, visualiza, edita (próximamente) y elimina entradas de contraseñas.
    * Organiza por nombre de sitio/app, nombre de usuario, contraseña y categoría.
    * Añade notas adicionales a cada entrada.
* **Generador de Contraseñas:** Crea contraseñas seguras y aleatorias directamente desde la aplicación.
* **Copiar al Portapapeles:** Copia fácilmente las contraseñas para usarlas.
* **Búsqueda Rápida:** Filtra tus contraseñas al instante.
* **Interfaz Limpia:** Interfaz de usuario amigable y responsiva creada con Tailwind CSS.
* **Sin Dependencias Externas (para el core):** Solo un archivo HTML con JavaScript y CSS incorporado (Tailwind vía CDN).

## Tecnologías Utilizadas

* **HTML5**
* **CSS3** (con [Tailwind CSS](https://tailwindcss.com/) vía CDN)
* **JavaScript (ES6+)**
    * **Web Crypto API:** Para todas las operaciones de cifrado y derivación de claves.

## Cómo Usar

1.  **Descarga:**
    * Clona este repositorio: `git clone https://github.com/tu-usuario/tu-repositorio.git`
    * O descarga directamente el archivo `gestor_contrasenas.html`.
2.  **Abre el Archivo:**
    * Abre `gestor_contrasenas.html` en cualquier navegador web moderno (Firefox, Chrome, Edge, Brave, Vivaldi, Zen Browser, etc.).
3.  **Configura tu Contraseña Maestra:**
    * La primera vez que abras la aplicación, se te pedirá que establezcas una contraseña maestra.
    * **¡MUY IMPORTANTE!** Esta contraseña es la única forma de acceder a tus datos. Si la olvidas, no podrás recuperar tus contraseñas, ya que no se almacena en ningún sitio y no hay mecanismo de recuperación.
4.  **Añade y Gestiona tus Contraseñas:**
    * Una vez configurada la contraseña maestra, podrás empezar a añadir, ver y gestionar tus credenciales de forma segura.
5.  **Bloqueo:**
    * Puedes bloquear la bóveda en cualquier momento usando el botón "Bloquear". Esto requerirá que vuelvas a introducir tu contraseña maestra para acceder.

## Integración como Aplicación de Escritorio en Linux

Puedes integrar este gestor de contraseñas en tu entorno de escritorio Linux para que se comporte como una aplicación más, utilizando un archivo `.desktop`.

1.  **Crea un archivo `.desktop`:**
    Crea un archivo de texto (por ejemplo, `gestor-contrasenas.desktop`) en `~/.local/share/applications/`. Si la carpeta `applications` no existe, créala.

2.  **Contenido del archivo `.desktop`:**
    Pega el siguiente contenido y ajústalo según tus necesidades:

    ```ini
    [Desktop Entry]
    Version=1.0
    Name=Gestor de Contraseñas Web
    Comment=Gestor de contraseñas local y seguro
    # Modifica la línea 'Exec' según tu navegador y la ruta al archivo HTML
    # ¡ASEGÚRATE DE USAR LA RUTA ABSOLUTA AL ARCHIVO HTML!

    # Opción 1: Firefox
    # Exec=firefox /ruta/absoluta/a/tu/gestor_contrasenas.html

    # Opción 2: Navegadores basados en Chromium (Chrome, Chromium, Brave, Vivaldi, Edge) en modo aplicación
    # Exec=chromium --app=file:///ruta/absoluta/a/tu/gestor_contrasenas.html
    # O para Google Chrome:
    # Exec=google-chrome-stable --app=file:///ruta/absoluta/a/tu/gestor_contrasenas.html

    # Opción 3: Zen Browser (u otros navegadores que abren archivos directamente)
    Exec=zen-browser /ruta/absoluta/a/tu/gestor_contrasenas.html

    # (Opcional) Ruta a un icono para la aplicación
    # Icon=/ruta/absoluta/a/un/icono.png

    Terminal=false
    Type=Application
    Categories=Utility;Security;Office;
    ```

    **Ejemplo de Ruta Absoluta:** Si guardaste `gestor_contrasenas.html` en tu carpeta `Documentos`, la ruta podría ser `/home/tu_usuario/Documentos/gestor_contrasenas.html`.

3.  **Hazlo Ejecutable (Recomendado):**
    Abre una terminal y ejecuta: `chmod +x ~/.local/share/applications/gestor-contrasenas.desktop`

4.  **Lanza la Aplicación:**
    Ahora deberías encontrar "Gestor de Contraseñas Web" en el menú de aplicaciones de tu entorno de escritorio.

## Consideraciones de Seguridad

* **Contraseña Maestra:** La seguridad de todas tus contraseñas almacenadas depende CRUCIALMENTE de la fortaleza y confidencialidad de tu contraseña maestra. Elígela bien y no la compartas.
* **Almacenamiento Local:** Los datos cifrados se guardan en el `localStorage` de tu navegador. Esto significa que son específicos de ese navegador en ese perfil de usuario en ese ordenador.
* **Limpieza del Navegador:** Si borras los datos de navegación, el historial completo, o específicamente el `localStorage` de tu navegador, **PERDERÁS TU BÓVEDA DE CONTRASEÑAS CIFRADA**. Considera hacer copias de seguridad manuales del archivo `gestor_contrasenas.html` (aunque esto solo guarda la aplicación, no los datos) o investiga cómo hacer copia de seguridad del `localStorage` si tu navegador lo permite (esto es avanzado). Una futura mejora podría ser una función de exportación/importación de la bóveda.
* **Seguridad del Sistema:** La seguridad de esta aplicación también depende de la seguridad general de tu sistema operativo y de que no tengas malware que pueda capturar lo que escribes (keyloggers).

## Contribuciones

¡Las sugerencias y contribuciones son bienvenidas! Si tienes ideas para mejorar la aplicación, no dudes en abrir un *issue* o enviar un *pull request*.

## Futuras Mejoras (Ideas)

* Función de editar entradas existentes.
* Exportación e importación de la bóveda cifrada (para copias de seguridad y migración).
* Más opciones de personalización.
* Mejoras en la accesibilidad.

## Licencia

Este proyecto se distribuye bajo la Licencia MIT. Ver el archivo `LICENSE` para más detalles (puedes añadir un archivo LICENSE con el texto de la licencia MIT si lo deseas).

---

Hecho con ❤️ para la comunidad de Arch Linux y para cualquiera que busque una solución de gestión de contraseñas simple y autocontrolada.
