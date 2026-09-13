# DECISIONES — historia real de construcción

## Punto de partida

El proyecto surgió como evolución de una Entrega 1 y de un sistema operativo más amplio de Impacto Verde.
El alcance original contemplaba órdenes, ocupación, campañas, vendedores, comisiones, facturación y cobranzas.

## Reducción deliberada de alcance

Para el Trabajo Final se decidió entregar un circuito menor pero demostrable:
**prevalidación de órdenes publicitarias y registro de borradores para revisión humana**.

Se dejaron fuera:
- reserva automática de dispositivos;
- actualización del maestro de ocupación;
- cálculo automático de comisiones;
- altas/bajas/modificaciones en producción;
- facturación y cobranzas.

La decisión priorizó un flujo que corriera de verdad antes que un producto más grande sin evidencia.

## Separación de producción y pruebas

Se creó una copia de la planilla llamada:
`Impacto Verde - Trabajo Final - PRUEBAS`.

El escenario final escribe únicamente allí.

## Falla 1 — mapeo inicial incompleto

La primera versión enviaba una instrucción genérica a Gemini y Google Sheets tenía campos mal
mapeados o vacíos. Se incorporó serialización JSON y un contrato de salida explícito.

## Falla 2 — ID concatenado con fecha

El ID de Google Forms, la fecha y las respuestas llegaban concatenados. Gemini devolvía el ID unido
a la fecha y un filtro de seguridad impedía la escritura.

La V1.1 separó explícitamente ID, fecha, diccionario y JSON del formulario. El filtro se mantuvo:
solo se escribe si el `id_respuesta` coincide exactamente con el ID original.

## Falla 3 — disponibilidad del modelo

Una prueba recibió **HTTP 503 por alta demanda de Gemini**. Se preservó la falla, se esperó y se
reintentó sin cambiar la entrada. El reintento completó el circuito.

## Tres corridas finales

1. Gout Gourmet.
2. Banco Macro.
3. Tortugas Open Mall.

Las tres recorrieron Google Forms → Make → Gemini → JSON → Google Sheets y terminaron como
`BORRADOR_PENDIENTE_REVISION`.

## Decisión de gobierno

El agente no recibe en esta versión el inventario de ocupación ni reglas verificadas de comisiones.
Por eso no se le permite inferir disponibilidad, reservar espacios o calcular comisiones.

## Próximas iteraciones

- conectar maestro de dispositivos/ocupación;
- incorporar IDs de campaña y vendedor;
- modelar comisiones con reglas explícitas;
- alta/modificación/baja lógica con autorización;
- benchmark Flash vs Flash-Lite;
- reintentos automáticos ante 429/503.
