# Agente de Prevalidación de Órdenes de Publicidad — Impacto Verde

Trabajo Final · Programación de y con Agentes de IA · MBA UCEMA · 2026 2T.

## Caso real

Impacto Verde gestiona publicidad OOH. El ingreso manual de una orden puede contener datos faltantes,
fechas inconsistentes o conceptos comerciales ambiguos. Este sistema recibe una orden mediante
Google Forms, la prevalidada con IA y guarda un **borrador verificable** para revisión humana.

La versión entregada **no aprueba ventas, no reserva dispositivos y no modifica ocupación productiva**.

## Objetivo

1. Leer una respuesta real de Google Forms.
2. Extraer y normalizar campos.
3. Detectar faltantes, contradicciones y señales problemáticas.
4. Devolver JSON bajo el contrato `OT-INGRESO-1.0`.
5. Registrar un borrador en una copia de Google Sheets.
6. Exigir revisión humana antes de cualquier acción comercial.

## Arquitectura

**Google Forms → Make → serialización JSON → Gemini 3.5 Flash → Parse JSON → filtro contractual → Google Sheets PRUEBAS**

Herramientas reales:
- Google Forms
- Make
- Gemini
- Google Sheets

El blueprint reproducible está en `automatizacion/`.

## Supervisión

El sistema llega hasta **L2**:
- automatiza lectura y prevalidación;
- puede escribir un borrador;
- no aprueba, no reserva inventario y no escribe en producción.

La aprobación final corresponde al responsable comercial / Gerencia General.
Ver `GOBIERNO_Y_RIESGO.md`.

## Formato de salida

La salida incluye versión de contrato, ID de respuesta, dictamen, cliente, CUIT, anunciante,
vendedor, fechas, importe declarado, condición de pago, soportes, alertas, observaciones,
`estado_ocupacion=NO_VERIFICADA` y `requiere_revision_humana=true`.

## Tres corridas reales

| Corrida | Cliente | Dictamen | Evidencia |
|---|---|---|---|
| 01 | Gout Gourmet | OBSERVADA | `corridas/corrida_01_gout_gourmet/` |
| 02 | Banco Macro | OBSERVADA | `corridas/corrida_02_banco_macro/` |
| 03 | Tortugas Open Mall | OBSERVADA | `corridas/corrida_03_tortugas_open_mall/` |

Las entradas y salidas están guardadas a partir de la evidencia registrada por el propio flujo.

## Proceso documentado

`DECISIONES.md` conserva:
- reducción de alcance;
- separación producción/pruebas;
- mapeo inicial incompleto;
- bug de ID concatenado con fecha;
- corrección V1.1;
- error 503 real;
- decisión de no inventar ocupación/comisiones.

## Economía

Ver `ANALISIS_ECONOMICO.md`.

## Estructura

```text
README.md
DECISIONES.md
ANALISIS_ECONOMICO.md
GOBIERNO_Y_RIESGO.md
prompts/
  system_prompt.md
  user_prompt.md
corridas/
  corrida_01_gout_gourmet/
  corrida_02_banco_macro/
  corrida_03_tortugas_open_mall/
datos/
  Impacto_Verde_Trabajo_Final_PRUEBAS.xlsx
automatizacion/
  escenario_make_V1_1.blueprint.json
```

## Reproducción

1. Importar el blueprint en un escenario nuevo de Make.
2. Reconectar Google Forms, Gemini y Google Sheets.
3. Usar el formulario `Carga de Ordenes de Publicidad`.
4. Mantener como destino una copia de pruebas.
5. Ejecutar una respuesta por vez.
6. Verificar `BORRADOR_PENDIENTE_REVISION`.

No se incluyen secretos ni credenciales.

## Limitaciones

- no consulta el maestro de ocupación;
- no reserva dispositivos;
- no calcula comisiones;
- no interpreta adjuntos;
- no valida CUIT contra una fuente fiscal;
- el reintento ante 503 fue manual;
- no se hizo A/B real con Flash-Lite antes del cierre.

Estas limitaciones son deliberadas y están documentadas.
