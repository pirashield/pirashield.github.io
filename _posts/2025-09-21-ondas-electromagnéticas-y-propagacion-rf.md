--- 
title: Ondas Electromagnéticas y Propagación RF
description: Las ondas electromagnéticas constituyen el fundamento físico de todas las comunicaciones inalámbricas, desde Wi-Fi hasta telefonía móvil. Esta nota explora las ecuaciones de Maxwell, la relación frecuencia-longitud de onda, y cómo estas propiedades determinan el comportamiento de propagación en sistemas RF reales.
author: Piratita 
date: 2025-09-21 11:33:00 +0800 
categories: [Fundamentos / Teoría, Electromagnetismo y Propagación]
tags: [electromagnetics , wave-propagation , maxwell-equations , wifi-physics] 
math: true
mermaid: true

---
## Introducción / Contexto

- **Definición clave:** Una onda electromagnética es la propagación de campos eléctricos y magnéticos perpendiculares que se autosustentan según las ecuaciones de Maxwell.
- **Ecuaciones de Maxwell en el vacío:**
  - $\nabla \cdot \vec{E} = 0$ (Ley de Gauss)
  - $\nabla \cdot \vec{B} = 0$ (No existen monopolos magnéticos)
  - $\nabla \times \vec{E} = -\frac{\partial \vec{B}}{\partial t}$ (Ley de Faraday)
  - $\nabla \times \vec{B} = \mu_0 \epsilon_0 \frac{\partial \vec{E}}{\partial t}$ (Ley de Ampère Maxwell)
- **Motivación:** Comprender la propagación electromagnética es esencial para diseñar sistemas WiFi eficientes, predecir coberturas y optimizar ubicación de antenas.

## Detalles Principales

### Velocidad de Propagación y Relación Fundamental
- La velocidad en el vacío surge de las constantes fundamentales:
  $$c = \frac{1}{\sqrt{\mu_0 \epsilon_0}} = 299,792,458 \text{ m/s}$$
- En medios materiales:
  $$v = \frac{c}{n}$$
  donde $n$ es el índice de refracción
- **Relación fundamental frecuencia-longitud de onda:**
  $$c = \lambda \cdot f$$
- **Analogía:** Como olas en el agua, pero los campos E y B se generan mutuamente sin necesitar un medio.

### Longitudes de Onda en Wi-Fi
- **2.4 GHz:** 
  $$\lambda = \frac{3 \times 10^8}{2.4 \times 10^9} = 0.125 \text{ m} = 12.5 \text{ cm}$$
- **5 GHz:**
  $$\lambda = \frac{3 \times 10^8}{5 \times 10^9} = 0.06 \text{ m} = 6 \text{ cm}$$
- **Implicación práctica:** Las antenas y obstáculos interactúan diferentemente con cada banda debido a estas dimensiones.

### Propagación en Diferentes Medios

| Material | Índice de Refracción | Efecto en Wi-Fi     |
| -------- | -------------------- | ------------------- |
| Aire     | 1.0003               | Propagación ideal   |
| Agua     | 1.33                 | Absorción alta      |
| Hormigón | ~2.5                 | Atenuación 10-20 dB |
| Metal    | -                    | Reflexión total     |

## Resumen de Preguntas Clave

- **¿Por qué c = λf?** Porque la velocidad de propagación es constante en un medio dado, y el producto frecuencia × longitud de onda debe mantenerse.
- **¿Por qué 5 GHz penetra menos que 2.4 GHz?** Longitudes de onda más cortas interactúan más con obstáculos de tamaño comparable.
- **¿Qué determina la velocidad de propagación?** Las propiedades electromagnéticas del medio (permitividad y permeabilidad).

- **Pendiente:** Investigar efectos de dispersión en materiales de construcción modernos

**Referencias:**
- OpenStax. "Física universitaria volumen 2 - Ecuaciones de Maxwell y ondas electromagnéticas"
- LibreTexts. "Ecuaciones de Maxwell y ondas electromagnéticas"
- Universidad del País Vasco. "Propagación de ondas electromagnéticas"
