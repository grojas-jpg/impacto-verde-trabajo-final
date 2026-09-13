# Corrida 01

- **Cliente / razón social:** NIESI RICARDO MAXIMILIANO
- **Anunciante / marca:** GOUT GOURMET
- **ID respuesta:** `ACYDBNhIw8AA5r78d3HykzkoZ-k14ORGYyK4W-b-C_SqqKdMLUmy5OR2b_W84-vWSofGj90`
- **N.º OT generado:** `OT-ACYDBNhIw8AA5r78d3HykzkoZ-k14ORGYyK4W-b-C_SqqKdMLUmy5OR2b_W84-vWSofGj90`
- **Fecha de procesamiento:** 2026-09-13T20:07:14+00:00
- **Modelo configurado:** `gemini-3.5-flash`
- **Dictamen:** `OBSERVADA`
- **Estado de ocupación:** `NO_VERIFICADA`
- **Tokens entrada:** 2896
- **Tokens salida visibles:** 574
- **Tokens totales informados por proveedor:** 6269
- **Estado de registro:** `BORRADOR_PENDIENTE_REVISION`

## Resultado operativo

La corrida terminó en un **borrador pendiente de revisión humana**.
El agente no aprobó la venta, no reservó dispositivos y no modificó ocupación productiva.

## Observación del agente

La pauta se declara del 2026-08-11 al 2026-09-10, pero el formulario se envió el 2026-09-12. Requiere confirmación humana de si se trata de una regularización de pauta ya emitida. No posee orden adjunta para cotejar.

## Reproducibilidad de la corrida

- **Versión del agente:** V1.1
- **Contrato:** `OT-INGRESO-1.0`
- **Modelo:** `gemini-3.5-flash`
- **Orquestador:** Make
- **Entrada original:** `corridas/corrida_01_gout_gourmet/entrada.json`
- **Salida original:** `corridas/corrida_01_gout_gourmet/salida.json`
- **System prompt:** `prompts/system_prompt.md`
- **User prompt operativo:** `prompts/user_prompt.md`
- **Blueprint:** `automatizacion/escenario_make_V1_1.blueprint.json`
- **Ruta:** Google Forms → Make → JSON → Gemini → Parse JSON → filtro contractual → Google Sheets PRUEBAS

Un tercero puede reconstruir esta corrida importando el blueprint, reconectando credenciales propias,
inyectando una entrada equivalente y verificando que el resultado termine como
`BORRADOR_PENDIENTE_REVISION`.

La evidencia original de esta corrida se conserva sin reescribir en `entrada.json` y `salida.json`.
