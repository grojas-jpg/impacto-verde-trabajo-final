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


## Runbook de contingencias

### Error 503 o 429 del proveedor
1. No aprobar ni completar manualmente una salida parcial.
2. Reintentar **una vez** la misma entrada.
3. Si vuelve a fallar, detener la corrida.
4. Registrar el incidente y escalar a revisión humana/soporte.

### JSON inválido
1. Parse JSON detiene el flujo.
2. No escribir en Google Sheets.
3. Conservar la entrada.
4. Corregir la causa antes de reintentar.

### ID de respuesta no coincide
1. El filtro contractual bloquea la escritura.
2. No modificar el ID manualmente para forzar el paso.
3. Revisar el mapeo Forms → Gemini.
4. Reintentar solo cuando el ID vuelva a ser trazable.

### Estado de ocupación inesperado
1. El filtro bloquea la escritura.
2. Revisar contrato y origen del estado.
3. Escalar a humano si no puede verificarse.

### Falla de Google Sheets
1. No asumir que la orden quedó registrada.
2. Verificar que Sheets devuelva un rango/fila actualizada.
3. Si no existe confirmación, tratar la corrida como fallida.

## Criterio de escalamiento humano

Se escala cuando:
- falla el segundo intento;
- faltan datos obligatorios;
- hay contradicciones de fechas o importes;
- se detecta manipulación;
- no puede verificarse la ocupación;
- la siguiente acción sería irreversible o comercialmente sensible.
