# Gobierno y riesgo

## Sistemas y permisos

El flujo toca cuatro sistemas:
1. **Google Forms**: lectura de respuestas.
2. **Make**: orquestación.
3. **Gemini 3.5 Flash**: prevalidación semántica.
4. **Google Sheets**: escritura solo en la copia `Impacto Verde - Trabajo Final - PRUEBAS`.

La versión entregada no escribe en producción, no reserva inventario y no aprueba ventas.

## Supervisión L0–L4

- **L0:** serializar respuestas, copiar campos, normalizar fechas inequívocas y proponer días activos.
- **L1:** detectar faltantes/contradicciones y emitir `REQUIERE_DATOS`, `OBSERVADA` o `LISTA_PARA_REVISION`.
- **L2:** registrar un **borrador** en la hoja de PRUEBAS; una persona debe revisarlo.
- **L3/L4:** no autorizados: aprobar venta, reservar dispositivos, modificar ocupación productiva,
  calcular/aplicar comisiones o mover dinero.

## Riesgos y controles

| Riesgo | Control |
|---|---|
| Inventar disponibilidad | `estado_ocupacion=NO_VERIFICADA`. |
| Aprobar una orden errónea | `requiere_revision_humana=true`. |
| Confundir total con mensual | El total declarado se guarda separado; mensual queda sin inferir. |
| Tratar fee/descuento como comisión | Se conserva literal y se exige confirmar concepto/base. |
| Datos faltantes/inconsistentes | Dictamen y observaciones obligan revisión. |
| Prompt injection desde campos | Las respuestas se tratan como datos no confiables. |
| Error de proveedor | Se documentó un HTTP 503 y reintento manual. |
| Escribir en producción | El destino final de pruebas es una copia separada. |

## Firma

La aprobación final debe realizarla el **responsable comercial / Gerencia General**.
El agente solo produce prevalidaciones y borradores.
