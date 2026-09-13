# Corrida 02

- **Cliente / razón social:** Banco Macro 
- **Anunciante / marca:** Banco Macro S.A.
- **ID respuesta:** `ACYDBNhSTHAfuXA9k029dlB-sMwpwTtDE2OmD-r2pZrFPyim-2vUHUK40aqhss3woIkzCLg`
- **N.º OT generado:** `OT-ACYDBNhSTHAfuXA9k029dlB-sMwpwTtDE2OmD-r2pZrFPyim-2vUHUK40aqhss3woIkzCLg`
- **Fecha de procesamiento:** 2026-09-13T21:09:18+00:00
- **Modelo configurado:** `gemini-3.5-flash`
- **Dictamen:** `OBSERVADA`
- **Estado de ocupación:** `NO_VERIFICADA`
- **Tokens entrada:** 2879
- **Tokens salida visibles:** 592
- **Tokens totales informados por proveedor:** 6339
- **Estado de registro:** `BORRADOR_PENDIENTE_REVISION`

## Resultado operativo

La corrida terminó en un **borrador pendiente de revisión humana**.
El agente no aprobó la venta, no reservó dispositivos y no modificó ocupación productiva.

## Observación del agente

El período de la campaña ya transcurrió en su totalidad con respecto a la fecha de recepción del formulario (2026-09-13). Adicionalmente, no se adjuntó el documento físico/digital de la Orden de Publicidad. Requiere confirmación comercial urgente del vendedor sobre las fechas cargadas y la provisión del adjunto correspondiente. La ocupación de los soportes no ha sido verificada.

## Reproducibilidad de la corrida

- **Versión del agente:** V1.1
- **Contrato:** `OT-INGRESO-1.0`
- **Modelo:** `gemini-3.5-flash`
- **Orquestador:** Make
- **Entrada original:** `corridas/corrida_02_banco_macro/entrada.json`
- **Salida original:** `corridas/corrida_02_banco_macro/salida.json`
- **System prompt:** `prompts/system_prompt.md`
- **User prompt operativo:** `prompts/user_prompt.md`
- **Blueprint:** `automatizacion/escenario_make_V1_1.blueprint.json`
- **Ruta:** Google Forms → Make → JSON → Gemini → Parse JSON → filtro contractual → Google Sheets PRUEBAS

Un tercero puede reconstruir esta corrida importando el blueprint, reconectando credenciales propias,
inyectando una entrada equivalente y verificando que el resultado termine como
`BORRADOR_PENDIENTE_REVISION`.

La evidencia original de esta corrida se conserva sin reescribir en `entrada.json` y `salida.json`.
