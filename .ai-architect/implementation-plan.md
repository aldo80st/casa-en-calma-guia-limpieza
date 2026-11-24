# Architecture-Driven Implementation Plan — Casa en calma 2.0

## Accepted decisions
ADR-001 a ADR-012, contrato revisión 1. Aprobados por el propietario el 24/11/2026. Este plan prepara ejecución; no autoriza por sí mismo cambios de aplicación ni publicación.

## Milestones
| ID | Resultado y alcance | Dependencias y restricciones | Verificación |
|---|---|---|---|
| S0 | Línea base, rama independiente, inventario, plan y pruebas iniciales. Verificar Paseo, Umbral, OpenProject y revisión. | ADR-007,010,012. No tocar main de aplicación. | Baseline SHA, inventario 44/11, reproducción de defectos y herramientas con evidencia. |
| S1 | Saneamiento: IDs estables, stock desconocido/agotado, navegación y cálculo sin ambigüedad. | S0; ADR-003,005,006,008. | Pruebas de precios duplicados, stock, prioridades, almacenamiento y migración. |
| S2 | Enriquecer catálogo y evidencia por SKU: precio, fecha, vendedor, garantía, consumibles, opiniones, stock. | S0; ADR-005,007. Investigación en lotes independientes; no extrapolar variantes. | 44/44 fichas con datos verificados o ausencia explícita; matriz de cobertura y revisión de muestra. |
| S3 | Implementar vistas y diseño editorial: Inicio, Explorar, Asistente, Favoritos, Comparar, Opiniones. | S1; ADR-001–004,011. Figma como referencia, collage existente. | URLs hash, teclado/foco, responsive 320/390/1440, revisión visual, sin desbordamiento. |
| S4 | Motor multicriterio explicable, restricciones previas, incertidumbre separada y pesos editables. | S1,S2; ADR-006. | Pruebas de pesos, presupuesto, compatibilidad, stock, datos faltantes y casos sin resultados; tres gamas solo cuando elegibles. |
| S5 | Comparador por IDs, favoritos, costo de propiedad y fichas de evidencia. | S3,S4; ADR-005,008. | Persistencia, borrado, costos comparables, supuestos editables y fuentes accesibles. |
| S6 | Validación integral, revisión independiente y candidato de publicación. | S1–S5; ADR-009–012. | Gates CI, accesibilidad, rendimiento medido, revisión visual, privacidad y rollback; publicación solo bajo autorización de ejecución y gates. |

## Cross-cutting constraints
- Una sola entrega estática; módulos ES y JSON; evitar dependencia de Ánima en runtime.
- Separar responsabilidades conforme al contrato. Datos de investigación nunca se promueven sin revisión.
- Usar Paseo para delegación cuando esté operativo: investigación por lotes, implementación y revisión independiente en tareas separadas; Umbral para conformidad y OpenProject para seguimiento. Si faltan herramientas, declarar bloqueo, no simular resultados.
- Cada sprint registra evidencia, commit y criterios. Las pruebas no ejecutadas quedan pendientes; sin reclamos de éxito inferidos.
- Objetivos propuestos de calidad para S6: cero errores JS en flujos principales; cero overflow en resoluciones objetivo; WCAG 2.2 AA como objetivo con comprobaciones automáticas y manuales; medir LCP y CLS sin declarar cumplimiento antes de medir.

## Explicit non-goals
Backend dedicado, cuentas, pagos, chatbot generativo, sincronización remota de preferencias, monetización, exposición de infraestructura, publicación de fotografías adicionales y cambios de alcance sin decisión nueva.

## Unresolved questions
Q-001: S0 verificará herramientas y revisores. Q-002: S2 registrará disponibilidad real de fuentes y datos no verificables. El diseño Figma será refinado durante S3; no sustituye pruebas de la implementación.
