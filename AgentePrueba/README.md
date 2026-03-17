# AgentePrueba

Repositorio de demo para un **agente de mantenimiento de Power BI** centrado en un problema real: cambios en columnas del origen de datos que rompen queries.

## Caso de uso real
En el equipo llegan muchos cambios de PBI (PBIs de trabajo) y fallos en consultas cuando:
- una columna cambia de nombre,
- una columna desaparece,
- cambia el tipo de dato,
- hay pasos en M que referencian columnas antiguas.

Este agente se conecta por terminal a los entornos `pbis mlps`, detecta el error y propone/aplica la corrección controlada.

## Qué demuestra en una demo
1. **Diagnóstico automático** de errores de schema en Power Query (M).
2. **Mapa de renombres** entre esquema esperado y esquema real.
3. **Parche sugerido** sobre la query (sin tocar lógica de negocio no relacionada).
4. **Validación posterior** y resumen para el ticket/PBI.

## Estructura
- `AGENTS.md`: instrucciones operativas del agente técnico.
- `PROMPTS.md`: prompts para ejecutar una demo de punta a punta.

## Flujo de demo recomendado
1. Se ejecuta una query rota con error de columna no encontrada.
2. El agente inspecciona esquema actual de origen.
3. Detecta correspondencias (por similitud + historial de renombres).
4. Genera parche M y lo muestra en diff.
5. Revalida y emite reporte final (cambios + riesgos + próximos pasos).
