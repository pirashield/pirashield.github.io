--- 
title: Sistema de Potencia en RF dB y dBm
description:  Los decibeles constituyen el lenguaje universal de las telecomunicaciones, permitiendo expresar rangos dinámicos extremos de manera manejable. Esta nota explica las diferencias entre dB, dBm y dBi, sus aplicaciones prácticas en WiFi, y las reglas de cálculo mental que todo ingeniero RF debe dominar.
author: Piratita 
date: 2025-09-21 11:34:00 +0800 
categories: [Cálculos y Diseño RF, Link budget & Unidades de potencia]
tags: [power-units , dbm , rf-calculations , wifi-power] 
math: true
mermaid:  true

---
## Introducción / Contexto

- **Definición dB:** Unidad logarítmica que expresa la relación entre dos potencias:
  $$\text{dB} = 10 \log_{10}\left(\frac{P_2}{P_1}\right)$$
- **Definición dBm:** Potencia absoluta referenciada a 1 milivatio:
  $$P_{\text{dBm}} = 10 \log_{10}\left(\frac{P_{\text{mW}}}{1\text{ mW}}\right)$$
- **Motivación:** Los sistemas RF manejan rangos de potencia de 12 órdenes de magnitud (picowatts a kilowatts). La escala logarítmica hace estos cálculos manejables.

## Detalles Principales

### Conversiones Fundamentales
- **De mW a dBm:**
  $$P_{\text{dBm}} = 10 \log_{10}(P_{\text{mW}})$$
- **De dBm a mW:**
  $$P_{\text{mW}} = 10^{P_{\text{dBm}}/10}$$
- **Reglas de cálculo rápido:**
  - +3 dB = ×2 en potencia
  - +10 dB = ×10 en potencia
  - -3 dB = ÷2 en potencia
  - -10 dB = ÷10 en potencia
- **Analogía:** Como la escala Richter para terremotos, cada unidad representa un cambio multiplicativo.

### Diferencias Críticas: dB vs dBm vs dBi
| Unidad | Tipo     | Uso                  | Ejemplo             |
| ------ | -------- | -------------------- | ------------------- |
| dB     | Relativo | Ganancias/pérdidas   | Cable pierde 3 dB   |
| dBm    | Absoluto | Potencia transmitida | Router emite 20 dBm |
| dBi    | Ganancia | Antenas              | Antena de 5 dBi     |

### Valores Típicos en Wi-Fi
```
Potencia TX router doméstico: 20 dBm (100 mW)
Sensibilidad receptor típica: -80 dBm (10 nW)
Señal excelente: > -50 dBm
Señal mínima útil: -80 dBm
Ruido térmico (20°C, 20 MHz): -101 dBm
```

### Operaciones con Decibeles
- **Suma de ganancias en cascada:**
  $$G_{\text{total}}[\text{dB}] = G_1 + G_2 + G_3 + ...$$
- **INCORRECTO - Suma de potencias:**
  $$P_{\text{total}}[\text{dBm}] \neq P_1[\text{dBm}] + P_2[\text{dBm}]$$
- **CORRECTO - Suma de potencias:**
  1. Convertir a mW: $P_1 = 10^{P_1[\text{dBm}]/10}$
  2. Sumar: $P_{\text{total}} = P_1 + P_2$
  3. Reconvertir: $P_{\text{total}}[\text{dBm}] = 10\log_{10}(P_{\text{total}})$

## Resumen de Preguntas Clave

- **¿Por qué usar logaritmos?** Comprimen rangos enormes y convierten multiplicaciones en sumas.
- **¿Cuándo usar factor 10 vs 20?** Factor 10 para potencia, factor 20 para voltaje/campo.
- **¿Se pueden sumar dBm directamente?** No, solo las ganancias/pérdidas en dB se suman directamente.

- **Tip práctico:** Memorizar: 0 dBm = 1 mW, 30 dBm = 1 W, -30 dBm = 1 μW

**Referencias:**
- Wikipedia. "dBm - Decibel-milliwatt"
- FiberMall. "dB, dBm and mW conversion guide"
- LibreTexts. "Cálculos de potencia de RF"
