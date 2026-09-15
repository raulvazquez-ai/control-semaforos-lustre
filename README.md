# Control de Semáforos mediante Programación Síncrona en Lustre 🚦

Este repositorio contiene la especificación, diseño y simulación de un sistema de control de tráfico utilizando **Lustre**, un lenguaje de programación síncrona basado en el flujo de datos, ideal para la verificación de sistemas críticos en tiempo real.

## 🚦 Escenarios Implementados

El proyecto se divide en dos fases de complejidad incremental basadas en la detección de vehículos mediante sensores paramétricos:

### 1. Cruce Básico (2 Vías)
*   **Archivo:** `semaforo.lus`
*   **Lógica:** Controla un semáforo principal ($S1$) y uno secundario ($S2$)[cite: 20]. El sistema mantiene la vía principal en verde hasta que el `carSensor` detecta un vehículo, activando un ciclo seguro de 8 *ticks* (evaluando el estado previo mediante el operador `pre`) con transiciones en ámbar antes de devolver el flujo a la normalidad.

### 2. Intersección Compleja con Prioridades (3 Vías)
*   **Archivo:** `semaforo2.lus`
*   **Lógica:** Gestiona tres semáforos ($S1$, $S2$, $S3$) en un cruce donde confluyen tres carriles hacia una única dirección. 
*   **Gestión de Casos:** Implementa un sistema de 14 *ticks* que evalúa 4 estados combinacionales posibles. El algoritmo otorga prioridad estricta de paso al `carSensor3` sobre el `carSensor2` en caso de concurrencia, garantizando que los ciclos en ejecución no se interrumpan para evitar colisiones.

## 🛠️ Tecnologías Utilizadas

*   **Lustre (V4):** Lenguaje declarativo para la definición de los estados transicionales y ecuaciones lógicas.
*   **Luciole:** Interfaz gráfica para la inyección de señales (sensores) y pruebas interactivas.
*   **Sim2Chro:** Herramienta de renderizado cronogramático para la verificación visual de los estados (verde, ámbar, rojo) en cada iteración de reloj.

## 🚀 Ejecución y Simulación

Para visualizar el comportamiento del sistema y probar los diferentes casos lógicos, utiliza las herramientas del entorno de Lustre en tu terminal:

```bash
# Simular el cruce básico (2 vías)
luciole semaforo.lus SEMAFORO

# Simular la intersección con prioridades (3 vías)
luciole semaforo2.lus SEMAFORO2
