# Análisis económico

## Modelo utilizado

Las tres corridas finales se ejecutaron con **Gemini 3.5 Flash** mediante Make.

Fuente de precios consultada el 13/09/2026:
https://ai.google.dev/gemini-api/docs/pricing

Tarifa estándar paga usada para presupuestar:
- entrada: **USD 1,50 por 1 millón de tokens**
- salida: **USD 9,00 por 1 millón de tokens**, incluyendo tokens de pensamiento

La proyección usa tarifa paga para no depender del nivel gratuito.

## Costos observados

La metadata distingue tokens de entrada, salida visible y total. Como la tarifa de salida incluye
tokens de pensamiento, se usa `tokens_totales - tokens_entrada` como aproximación conservadora
del volumen de salida/pensamiento facturable.

| Corrida | Entrada | Salida visible | Total proveedor | Salida/pensamiento estimada | Costo estimado |
|---|---:|---:|---:|---:|---:|
| 01 | 2,896 | 574 | 6,269 | 3,373 | USD 0.0347 |
| 02 | 2,879 | 592 | 6,339 | 3,460 | USD 0.0355 |
| 03 | 2,882 | 602 | 6,167 | 3,285 | USD 0.0339 |

**Costo medio estimado por corrida: USD 0.0347.**

## Proyección operativa

Supuesto base: **20 órdenes por semana**.
- costo semanal estimado: **USD 0.69**
- costo anual estimado (52 semanas): **USD 36.07**

Sensibilidad:
- 10 órdenes/semana: USD 0.35/semana; USD 18.03/año
- 50 órdenes/semana: USD 1.73/semana; USD 90.17/año

## Elección del modelo

Gemini 3.5 Flash fue el modelo **efectivamente validado** en las tres corridas reales.
Se eligió una variante Flash por velocidad y costo para una tarea de extracción/prevalidación.

**Limitación:** antes del cierre no se realizó una comparación A/B real con Gemini 3.5 Flash-Lite.
Por eso la conclusión defendible es que 3.5 Flash es el modelo más chico **validado en este proyecto**,
no que Flash-Lite necesariamente falle. Una próxima iteración debe compararlos y migrar al menor
si conserva la calidad.


## Fórmula explícita por corrida

La estimación se calculó con:

`costo = tokens_entrada × (USD 1,50 / 1.000.000) + tokens_salida_estimados × (USD 9,00 / 1.000.000)`

donde:

`tokens_salida_estimados = tokens_totales_proveedor - tokens_entrada`

Se usa esta aproximación porque la tarifa publicada de salida incluye tokens de pensamiento.

- **Moneda:** USD
- **Unidad:** USD por corrida
- **Fuente:** página oficial de precios de Gemini consultada el 13/09/2026  
  https://ai.google.dev/gemini-api/docs/pricing
- **Naturaleza:** estimación presupuestaria; no es una factura emitida por Google.

Los costos individuales ya están calculados en la tabla superior:
- Corrida 01: **USD 0,0347**
- Corrida 02: **USD 0,0355**
- Corrida 03: **USD 0,0339**

Costo medio observado: **USD 0,0347 por corrida**.

## Justificación de modelo

`gemini-3.5-flash` es el modelo más pequeño **validado empíricamente en este proyecto antes del cierre**:
produjo salida JSON válida, completó tres corridas reales y mantuvo un costo del orden de centavos.

No se afirma que Flash-Lite sea peor: no se realizó A/B antes del cierre. Esa comparación queda
documentada como siguiente experimento.
