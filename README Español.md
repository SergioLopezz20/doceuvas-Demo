<div align="center">
  <h1>🍇 Doce Uvas 🥂</h1>
  <p><strong>La aplicación definitiva para la Nochevieja española.</strong></p>
</div>

## 📖 ¿Qué es este proyecto?

**Doce Uvas** es una aplicación móvil nativa (Android & iOS) diseñada para acompañar a los usuarios durante la tradicional noche de fin de año en España. Su objetivo principal es ofrecer un **reloj sincronizado y preciso**, proporcionando la experiencia audiovisual completa de los "cuartos" y las doce campanadas, asegurando que nadie pierda la cuenta de sus uvas. 

Desarrollada con un fuerte enfoque en el rendimiento, funcionamiento sin conexión a red,  la sincronización de audio de baja latencia y una interfaz inmersiva, esta aplicación sirve como una alternativa digital fiable a las tradicionales retransmisiones televisivas.

---

## ⚙️ ¿Cómo funciona?

El flujo de la aplicación se divide en dos fases principales, garantizando una transición suave hacia la medianoche:

1. **Fase de Preparación (Countdown):** La pantalla principal (`CountdownPage`) muestra una cuenta atrás precisa hasta la medianoche del 31 de diciembre. Cuenta con una estética nocturna elegante (`ThemeStyle.goldDark`) para adaptarse al contexto festivo y evitar la fatiga visual.
2. **Fase de Evento (`EventPage`):**
   - **Los Cuartos:** Al llegar el momento, la aplicación inicia el motor de audio y reproduce automáticamente los 4 tonos precursores (cuartos).
   - **Las Campanadas:** A continuación, se ejecuta una secuencia temporizada de 12 campanadas, calculando el margen de tiempo exacto entre cada una para poder comer la uva sin pausas indeseadas.
   - **Celebración:** Al finalizar el ciclo de audio, se despliega una animación festiva de partículas (Confetti) a 60 FPS para celebrar la entrada del nuevo año.

---

## 🚀 Características Principales

- ⏱️ **Cuenta atrás de alta precisión:** Sincronización optimizada para evitar _lag_ o bloqueos en el hilo principal durante el momento crítico.
- 🔔 **Sistema de Audio Sincronizado:** Reproducción secuencial y espaciada utilizando buffers precargados en memoria.
- 🎉 **Feedback Visual Inmersivo:** Animaciones de partículas generadas directamente sobre el canvas.
- 📱 **Monetización Integrada:** Implementación de Google Mobile Ads de forma asíncrona y no intrusiva.
- 🎨 **UI/UX Premium:** Interfaz fija en modo retrato (_Portrait-only_) implementada desde `main.dart` para evitar giros accidentales del dispositivo.
- ⚡ **Splash Screen Nativo:** Carga optimizada e integrada a nivel de sistema operativo para Android e iOS.

---
<img width="390" height="792" alt="image" src="https://github.com/user-attachments/assets/50284189-8725-4504-89e0-ad1c1fa1febc" />
<img width="395" height="805" alt="image" src="https://github.com/user-attachments/assets/051633e9-20f8-482f-9cbd-2e5e6ed60b8d" />


## 🛠️ Arquitectura y Tech Stack (Technical Overview)

Este proyecto está construido bajo los estándares modernos de desarrollo de aplicaciones móviles, priorizando la separación de responsabilidades y la gestión eficiente de recursos.

- **Framework:** [Flutter](https://flutter.dev/) (SDK ^3.10.7) - Compilación *Ahead-of-Time* (AOT) a código de máquina nativo ARM para iOS y Android desde un único código base en Dart.
- **Reproducción de Audio:** `audioplayers` - Utilizado para la gestión de *buffers* de audio. Los archivos `.mp3` (campanadas y cuartos) se cargan como *assets* y se mantienen listos en memoria para garantizar latencia cero al llamar a la función de reproducción.
- **Animaciones:** `confetti` - Renderizado eficiente de sistemas de partículas 2D.
- **Monetización:** `google_mobile_ads` - Integración del SDK oficial de AdMob.
- **Tooling Nativo:** `flutter_native_splash` y `flutter_launcher_icons` para la inyección y configuración automatizada de *assets* en los manifiestos de Android (`AndroidManifest.xml`) e iOS (`Info.plist`).

### 📂 Estructura del Código

La arquitectura de la aplicación en el directorio `lib/` está organizada lógicamente por dominio funcional:

```text
lib/
 ├── data/        # Constantes globales, configuración estática y paleta de colores (ThemeStyle)
 ├── pages/       # Controladores de pantalla principales (countdown_page.dart, event_page.dart)
 ├── widgets/     # Componentes visuales puros y aislados para su reutilización
 └── main.dart    # Entry point, inicialización de dependencias y configuración general de la App
