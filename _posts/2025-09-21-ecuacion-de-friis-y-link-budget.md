--- 
title: Ecuación de Friis y Link Budget
description:  La ecuación de Friis es la herramienta fundamental para predecir el rendimiento de enlaces inalámbricos, integrando potencia transmitida, ganancias de antena y pérdidas de propagación. Esta nota desarrolla la ecuación completa, ejemplos de cálculo de link budget, y márgenes de diseño para sistemas WiFi confiables.
author: Piratita 
date: 2025-09-21 11:35:00 +0800 
categories: [Cálculos y Diseño RF, Link budget & Planificación RF]
tags: [friis-equation, link-budget, rf-planning, propagation-models]
math: true
mermaid:  true

---
## Introducción / Contexto

- **Definición:** La ecuación de Friis relaciona la potencia recibida con la transmitida en un enlace de radiofrecuencia:
  $$P_r = P_t G_t G_r \left(\frac{\lambda}{4\pi d}\right)^2$$
- **Forma logarítmica práctica:**
  $$P_r[\text{dBm}] = P_t[\text{dBm}] + G_t[\text{dBi}] + G_r[\text{dBi}] - \text{FSPL}[\text{dB}] - L_{\text{sistema}}[\text{dB}]$$
- **Motivación:** Permite determinar viabilidad de enlaces, calcular coberturas y optimizar diseños de red antes de la implementación.

## Detalles Principales

### Componentes del Link Budget

- **PIRE (Potencia Isotrópica Radiada Equivalente):**
  $$\text{PIRE}[\text{dBm}] = P_{TX}[\text{dBm}] + G_{TX}[\text{dBi}] - L_{TX}[\text{dB}]$$
- **Pérdida en Espacio Libre (FSPL):**
  $$\text{FSPL}[\text{dB}] = 32.45 + 20\log_{10}(f[\text{MHz}]) + 20\log_{10}(d[\text{km}])$$
- **Pérdidas adicionales:**
  - Cables coaxiales: 0.5-1 dB/m @ 2.4 GHz
  - Conectores: 0.5 dB cada uno
  - Paredes interiores: 3-5 dB
  - Pisos de hormigón: 15-20 dB

### Ejemplo Completo: Enlace Wi-Fi Interior

**Escenario:** Router a laptop, 30 metros, 2 paredes

```
TRANSMISIÓN:
- Potencia TX: 20 dBm
- Ganancia antena TX: 5 dBi
- Pérdida cable TX: 1 dB
- PIRE: 20 + 5 - 1 = 24 dBm

PROPAGACIÓN (2.4 GHz):
- FSPL @ 30m: 32.45 + 67.6 + (-30) = 70 dB
- 2 paredes @ 4 dB: 8 dB
- Pérdida total: 78 dB

RECEPCIÓN:
- Ganancia antena RX: 2 dBi
- Pérdida cable RX: 0 dB
- Potencia recibida: 24 - 78 + 2 = -52 dBm

ANÁLISIS:
- Sensibilidad RX: -85 dBm
- Margen de enlace: -52 - (-85) = 33 dB ✓
- Calidad: EXCELENTE
```

### Márgenes de Diseño Recomendados

| Tipo de Enlace | Distancia | Margen Requerido | Justificación           |
| -------------- | --------- | ---------------- | ----------------------- |
| Interior       | < 100m    | 10-15 dB         | Variaciones menores     |
| Campus         | 100m-1km  | 15-20 dB         | Clima, vegetación       |
| Punto a punto  | 1-10km    | 20-30 dB         | Lluvia, desvanecimiento |
| Largo alcance  | > 10km    | 30-40 dB         | Múltiples factores      |

### Factores de Corrección Prácticos

- **Efecto de la frecuencia:**
  - 5 GHz tiene 6.3 dB más pérdida que 2.4 GHz
  - Fórmula rápida: $\Delta\text{FSPL} = 20\log_{10}(f_2/f_1)$
- **Zonas de Fresnel:**
  - Primera zona: $r_1 = 17.3\sqrt{\frac{d_1 \cdot d_2}{\lambda \cdot D}}$ metros
  - Obstrucción > 40% causa pérdidas adicionales significativas

## Resumen de Preguntas Clave

- **¿Qué es un margen de enlace aceptable?** Mínimo 10 dB para enlaces fijos, 20 dB para móviles.
- **¿Por qué la FSPL aumenta 6 dB al duplicar la distancia?** Por la ley del cuadrado inverso (20log₂ = 6).
- **¿Cómo afecta la lluvia?** Despreciable < 10 GHz, crítica > 10 GHz (0.01-10 dB/km).

- **Herramienta útil:** Calculadora online TP-Link para link budget

**Referencias:**
- George Mason University. "Friis Free Space Loss Equation"
- LibreTexts. "Ecuación de Transmisión Friis"
- Wikipedia. "Link budget calculations"
