# Corrida 03

- **Cliente / razón social:** Tortugas Open Mall S.A.
- **Anunciante / marca:** Tortugas Open Mall S.A
- **ID respuesta:** `ACYDBNjlrS7Cfn2JPO0T1tEeq1sgvgeVrNrfLnRmwFisOM0cuyzFx61nhXcZvgNFGxhrwj8`
- **N.º OT generado:** `OT-ACYDBNjlrS7Cfn2JPO0T1tEeq1sgvgeVrNrfLnRmwFisOM0cuyzFx61nhXcZvgNFGxhrwj8`
- **Fecha de procesamiento:** 2026-09-13T21:13:26+00:00
- **Modelo configurado:** `gemini-3.5-flash`
- **Dictamen:** `OBSERVADA`
- **Estado de ocupación:** `NO_VERIFICADA`
- **Tokens entrada:** 2882
- **Tokens salida visibles:** 602
- **Tokens totales informados por proveedor:** 6167
- **Estado de registro:** `BORRADOR_PENDIENTE_REVISION`

## Resultado operativo

La corrida terminó en un **borrador pendiente de revisión humana**.
El agente no aprobó la venta, no reservó dispositivos y no modificó ocupación productiva.

## Observación del agente

La orden de publicidad fue enviada el 13 de septiembre de 2026, pero la pauta declarada finalizó el 9 de septiembre de 2026. Se requiere verificación humana urgente para confirmar si corresponde a una carga histórica de regularización. Adicionalmente, el cliente no adjuntó la orden digital de respaldo.

## Reproducibilidad de la corrida

- **Versión del agente:** V1.1
- **Contrato:** `OT-INGRESO-1.0`
- **Modelo:** `gemini-3.5-flash`
- **Orquestador:** Make
- **Entrada original:** `corridas/corrida_03_tortugas_open_mall/entrada.json`
- **Salida original:** `corridas/corrida_03_tortugas_open_mall/salida.json`
- **System prompt:** `prompts/system_prompt.md`
- **User prompt operativo:** `prompts/user_prompt.md`
- **Blueprint:** `automatizacion/escenario_make_V1_1.blueprint.json`
- **Ruta:** Google Forms → Make → JSON → Gemini → Parse JSON → filtro contractual → Google Sheets PRUEBAS

Un tercero puede reconstruir esta corrida importando el blueprint, reconectando credenciales propias,
inyectando una entrada equivalente y verificando que el resultado termine como
`BORRADOR_PENDIENTE_REVISION`.

La evidencia original de esta corrida se conserva sin reescribir en `entrada.json` y `salida.json`.
