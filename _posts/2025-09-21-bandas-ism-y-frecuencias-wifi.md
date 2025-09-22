--- 
title: Bandas ISM y Frecuencias Wi-Fi
description: Las bandas ISM (Industrial, Scientific, Medical) proporcionan espectro sin licencia para aplicaciones inalámbricas como WiFi. Esta nota detalla la organización del espectro en 2.4 GHz y 5 GHz, canalización, regulaciones regionales y consideraciones de diseño para redes WLAN eficientes.
author: Piratita 
date: 2025-09-21 11:37:00 +0800 
categories: [Espectro y Regulación, Bandas ISM & Gestión de canales]
tags: [ism-bands, wifi-channels, spectrum-management, 2.4ghz, 5ghz, regulation]
math: true
mermaid:  true

---
## Introducción / Contexto

- **Definición ISM:** Bandas de radiofrecuencia reservadas internacionalmente para uso industrial, científico y médico sin requerir licencia individual.
- **Bandas principales Wi-Fi:**
  - 2.400-2.500 GHz (100 MHz de ancho de banda)
  - 5.150-5.875 GHz (~700 MHz disponibles regionalmente)
  - 6.000-7.125 GHz (Wi-Fi 6E, adoptación en progreso)
- **Motivación:** El espectro es un recurso finito y valioso. Comprender su organización es esencial para diseñar redes sin interferencias.

## Detalles Principales

### Banda 2.4 GHz - Estructura y Canales

- **Canalización IEEE 802.11:**
  $$f_c = 2412 + 5(n-1) \text{ MHz, donde } n = 1...14$$
- **Ancho de banda:** 20 MHz por canal (22 MHz ocupados)
- **Canales no solapados:** 1, 6, 11 (separación 25 MHz)

```
Canal 1:  2.401-2.423 GHz ━━━━━━
Canal 6:  2.426-2.448 GHz       ━━━━━━
Canal 11: 2.451-2.473 GHz             ━━━━━━
```

- **Analogía:** Como carriles en una autopista - usar canales solapados es como conducir entre dos carriles.

### Banda 5 GHz - Organización U-NII

| Subbanda | Canales | Frecuencias (GHz) | Potencia Máx | Restricciones           |
| -------- | ------- | ----------------- | ------------ | ----------------------- |
| U-NII-1  | 36-48   | 5.180-5.240       | 23 dBm       | Interior principalmente |
| U-NII-2A | 52-64   | 5.260-5.320       | 23 dBm       | DFS requerido           |
| U-NII-2C | 100-144 | 5.500-5.720       | 30 dBm       | DFS + TPC               |
| U-NII-3  | 149-165 | 5.735-5.835       | 30 dBm       | Sin restricciones       |

- **DFS (Dynamic Frequency Selection):** Detecta y evita radares meteorológicos
- **TPC (Transmit Power Control):** Ajusta potencia automáticamente

### Comparación 2.4 vs 5 GHz

| Característica | 2.4 GHz                      | 5 GHz        |
| -------------- | ---------------------------- | ------------ |
| Alcance        | Mayor (↑30-40%)              | Menor        |
| Penetración    | Mejor                        | Peor (-6 dB) |
| Canales libres | 3                            | 25+          |
| Interferencia  | Alta (Bluetooth, microondas) | Baja         |
| Velocidad máx  | 600 Mbps                     | 6.9 Gbps     |
| Dispositivos   | Universal                    | Modernos     |

### Regulaciones Regionales Clave

- **FCC (América):**
  - 2.4 GHz: 30 dBm EIRP máximo
  - 5 GHz: 30-36 dBm según subbanda
  - Canales 12-14 no permitidos

- **ETSI (Europa):**
  - 2.4 GHz: 20 dBm EIRP
  - 5 GHz: 23 dBm interior, 30 dBm exterior con restricciones
  - Canal 14 solo Japón (2.484 GHz)

- **Consideraciones especiales:**
  - Aeropuertos: restricciones adicionales cerca de radares
  - Hospitales: límites más estrictos en equipos médicos
  - Fronteras: coordinación internacional requerida

## Resumen de Preguntas Clave

- **¿Por qué solo 3 canales en 2.4 GHz?** El solapamiento de 22 MHz en canales de 5 MHz de separación.
- **¿Qué es DFS?** Sistema que detecta radares y cambia canal automáticamente en 5 segundos.
- **¿Por qué 5 GHz tiene menos interferencia?** Más espectro disponible y menos dispositivos legacy.

- **Pendiente:** Investigar adopción Wi-Fi 6E en México y requisitos regulatorios

**Referencias:**
- IEEE 802.11 Standard Specification
- Wikipedia. "List of WLAN channels"
- FCC Part 15 Rules for Unlicensed Operation
