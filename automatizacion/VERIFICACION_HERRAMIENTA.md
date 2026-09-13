# Verificación de herramienta real y operable

## Flujo verificado

El sistema fue ejecutado de punta a punta con conectores reales:

**Google Forms → Make → serialización JSON → Gemini 3.5 Flash → Parse JSON → filtro contractual → Google Sheets**

El formulario usado fue `Carga de Ordenes de Publicidad`.

El escenario final de Make fue:

`Impacto Verde - OT - PRUEBAS V1.1 - mensaje corregido`

El destino de escritura fue exclusivamente la copia:

`Impacto Verde - Trabajo Final - PRUEBAS`

## Evidencia observable

Las tres corridas finales dejaron una fila nueva en Google Sheets:

- fila 6: Gout Gourmet
- fila 7: Banco Macro
- fila 8: Tortugas Open Mall

Cada fila conserva:
- ID de respuesta de Google Forms;
- estado de registro;
- dictamen IA;
- observaciones;
- JSON original de Gemini;
- modelo configurado;
- tokens de entrada, salida y total;
- fecha de procesamiento;
- respuestas originales del formulario.

La planilla completa está en:

`datos/Impacto_Verde_Trabajo_Final_PRUEBAS.xlsx`

El blueprint reproducible está en:

`automatizacion/escenario_make_V1_1.blueprint.json`

## Permisos efectivos

- **Google Forms:** lectura de respuestas.
- **Make:** orquestación y transformación; no aprueba ventas.
- **Gemini:** prevalidación semántica y salida JSON.
- **Google Sheets:** escritura únicamente en la copia de PRUEBAS.

## Control previo a la escritura

Google Sheets se ejecuta solo si se cumplen simultáneamente:

1. `version_contrato = OT-INGRESO-1.0`
2. `id_respuesta` coincide exactamente con el ID original de Google Forms
3. `estado_ocupacion = NO_VERIFICADA`

Si alguna condición falla, el registro no se escribe.

## Resultado

La herramienta quedó verificada mediante tres corridas reales distintas y escritura efectiva en Google Sheets.

La versión entregada:
- no escribe en producción;
- no reserva inventario;
- no aprueba ventas;
- no calcula comisiones.
