--- 
title: FSPL - Pérdida en Espacio Libre
description: La pérdida en espacio libre (Free Space Path Loss) cuantifica la atenuación natural que sufre una onda electromagnética al propagarse, resultado directo de la dispersión esférica de la energía. Esta nota deriva la ecuación FSPL, presenta formas simplificadas para Wi-Fi y analiza sus implicaciones prácticas en diseño de enlaces.
author: Piratita 
date: 2025-09-21 11:36:00 +0800 
categories: [Cálculos y Diseño RF, Pérdidas (FSPL) y Modelos de Propagación]
tags: [fspl, path-loss, propagation, rf-theory, wifi-coverage]
math: true
mermaid:  true

---
## Introducción / Contexto

- **Definición:** FSPL es la pérdida de potencia de una onda electromagnética propagándose en línea recta a través del espacio libre, sin obstáculos ni reflexiones.
- **Principio físico:** La densidad de potencia disminuye con el cuadrado de la distancia debido a la expansión esférica del frente de onda.
- **Motivación:** FSPL establece el límite teórico mínimo de pérdida - cualquier escenario real tendrá pérdidas adicionales.

## Detalles Principales

### Derivación de la Ecuación FSPL

1. **Densidad de potencia a distancia d:**
   $$P_d = \frac{P_t G_t}{4\pi d^2} \text{ [W/m²]}$$

2. **Área efectiva de antena receptora:**
   $$A_e = \frac{\lambda^2 G_r}{4\pi}$$

3. **Potencia recibida:**
   $$P_r = P_d \cdot A_e = P_t G_t G_r \left(\frac{\lambda}{4\pi d}\right)^2$$

4. **FSPL (con antenas isotrópicas, G=1):**
   $$\text{FSPL} = \left(\frac{4\pi d}{\lambda}\right)^2 = \left(\frac{4\pi d f}{c}\right)^2$$

5. **Forma logarítmica práctica:**
   $$\text{FSPL}[\text{dB}] = 32.45 + 20\log_{10}(f[\text{MHz}]) + 20\log_{10}(d[\text{km}])$$

### Fórmulas Simplificadas para Wi-Fi

- **2.4 GHz:**
  $$\text{FSPL}_{2.4}[\text{dB}] = 100.13 + 20\log_{10}(d[\text{km}])$$
  
- **5.0 GHz:**
  $$\text{FSPL}_{5.0}[\text{dB}] = 106.45 + 20\log_{10}(d[\text{km}])$$

- **5.8 GHz:**
  $$\text{FSPL}_{5.8}[\text{dB}] = 107.77 + 20\log_{10}(d[\text{km}])$$

### Tabla de Pérdidas Típicas

| Distancia | FSPL @ 2.4 GHz | FSPL @ 5 GHz | Diferencia |
| --------- | -------------- | ------------ | ---------- |
| 1 m       | 40.1 dB        | 46.4 dB      | 6.3 dB     |
| 10 m      | 60.1 dB        | 66.4 dB      | 6.3 dB     |
| 100 m     | 80.1 dB        | 86.4 dB      | 6.3 dB     |
| 1 km      | 100.1 dB       | 106.4 dB     | 6.3 dB     |

**Observación clave:** La diferencia es constante (6.3 dB) independiente de la distancia.

### Reglas de Cálculo Rápido

- **Duplicar distancia:** +6 dB de pérdida
- **Distancia ×10:** +20 dB de pérdida  
- **Duplicar frecuencia:** +6 dB de pérdida
- **Frecuencia ×10:** +20 dB de pérdida

**Ejemplo mental:** 
- FSPL @ 2.4 GHz, 100m = 80 dB
- FSPL @ 2.4 GHz, 200m = 80 + 6 = 86 dB
- FSPL @ 5 GHz, 200m = 86 + 6 = 92 dB

### Limitaciones del Modelo FSPL

- **Asume:** Propagación en línea recta, sin obstáculos, antenas en campo lejano
- **No considera:** Reflexiones, difracción, absorción atmosférica, desvanecimiento
- **Validez:** d >> λ y d >> dimensiones de antena
- **Analogía:** Como calcular tiempo de viaje asumiendo velocidad constante - útil para estimación inicial, pero simplificado

## Resumen de Preguntas Clave

- **¿Por qué FSPL ∝ d²?** Por conservación de energía en expansión esférica.
- **¿Por qué frecuencias altas pierden más?** Área efectiva de antena disminuye con λ².
- **¿Es FSPL la pérdida real?** No, es el mínimo teórico. La pérdida real siempre es mayor.

- **Calculadora Python:**
```python
def fspl_db(freq_mhz, dist_km):
    return 32.45 + 20*np.log10(freq_mhz) + 20*np.log10(dist_km)
```

**Referencias:**
- George Mason University. "Friis Free Space Loss Equation"
- Universidad de Las Palmas. "Propagación de ondas electromagnéticas"
- SciELO. "Modelo para pérdidas de propagación en WLAN"
