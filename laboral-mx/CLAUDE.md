# Perfil de uso — Laboral MX

> Se llena con `/laboral-mx:cold-start-interview`. Editable directamente.

## Datos de quien usa el plugin

- **Tipo de usuario:** [trabajador | abogado | clínica jurídica | OSC | PROFEDET | sindicato | otro]
- **Estado de la República:** [llenar]
- **Familiaridad con temas laborales:** [ninguna | básica | intermedia | profesional]
- **Para quién usa el plugin:** [para mí | para alguien que ayudo | profesionalmente]

## Configuración de lenguaje

### Si el usuario es trabajador sin formación legal

- Lenguaje cotidiano, sin tecnicismos.
- Los artículos de la LFT se citan entre paréntesis como referencia, no como argumento principal.
- Los cálculos se explican paso a paso con el razonamiento visible.
- Se usan analogías cotidianas cuando ayuden.
- Se traduce todo latinismo y todo acrónimo la primera vez que aparece.

### Si el usuario es abogado o profesional de RRHH

- Lenguaje técnico laboral, con citas a artículos específicos de la LFT.
- Los cálculos se presentan con fórmula y resultado, sin explicación paso a paso salvo solicitud.
- Se mencionan tesis y jurisprudencia relevante cuando fortalezcan el argumento.
- Se distingue entre prestaciones de ley y superiores a la ley.

## Sistema jurídico laboral mexicano — Contexto obligatorio

### Jurisdicción

El derecho laboral mexicano es **federal** (la LFT aplica en todo el país), pero la competencia para resolver conflictos puede ser **federal o local**:

- **Federal:** Empresas de jurisdicción federal (ferrocarriles, minería, petroquímica, eléctrica, cinematografía, banca, seguros, empresas administradas por el gobierno federal, IMSS, Infonavit). También cuando el conflicto afecta trabajadores de dos o más entidades federativas.
- **Local:** Todo lo demás (comercio, servicios, manufactura, construcción, agricultura).

### Reforma procesal laboral (2019-2022)

- Las Juntas de Conciliación y Arbitraje están en proceso de desaparición.
- Los nuevos **Tribunales Laborales** (del Poder Judicial) las sustituyen.
- La **conciliación prejudicial obligatoria** ante el Centro Federal de Conciliación y Registro Laboral (o centros locales) es requisito previo a la demanda.
- La transición es gradual. En algunos estados siguen operando las Juntas. Verificar.

### Plazos críticos

- **Despido injustificado:** Prescripción de **2 meses** para demandar reinstalación. **1 año** para demandar indemnización.
- **Prestaciones devengadas:** Prescripción de **1 año**.
- **Acciones derivadas del despido:** Prescripción de **1 año** desde la fecha de separación.
- **Conciliación prejudicial:** El Centro tiene **45 días naturales** para concluir la etapa. Si no hay acuerdo, emite constancia de no conciliación que habilita la demanda.
- **Salarios caídos:** Máximo **12 meses** si el juicio se alarga. Después, se generan intereses del 2% mensual sobre 15 meses de salario, capitalizables.

### Reformas recientes a considerar

- **Vacaciones Dignas 2023:** 12 días mínimos desde el primer año (antes 6). Escala progresiva hasta 32.
- **Ley Silla 2025:** Derecho a asiento con respaldo para trabajadores que están de pie. Vigente desde junio 2025.
- **Plataformas Digitales 2025-2026:** Regulación de trabajadores de apps (Uber, Rappi, DiDi). Fase piloto julio 2025, vigencia plena enero 2026. IMSS e Infonavit obligatorio si ganan al menos 1 salario mínimo mensual.
- **Desconexión Digital 2026:** Derecho de todos los trabajadores a no recibir comunicaciones fuera de horario laboral. Aprobada por la Cámara de Diputados.
- **Propuestas en discusión (no vigentes aún):** Reducción de jornada a 40 horas semanales, aumento de aguinaldo a 30 días, permisos por luto (5 días), nuevos feriados obligatorios (1-2 noviembre, 12 diciembre).

## Valores numéricos vigentes (2026)

Estos valores son los que usa la calculadora y todos los skills que hagan cálculos. **Se deben actualizar cada enero** cuando cambian el salario mínimo y cada febrero cuando cambia la UMA.

- **Salario mínimo general 2026:** $315.04 MXN/día.
- **Salario mínimo ZLFN 2026:** $440.87 MXN/día.
- **UMA diaria 2026 (desde 1 feb):** $117.31 MXN.
- **UMA mensual 2026:** $3,566.74 MXN.
- **UMA anual 2026:** $42,801.24 MXN.
- **SBC mínimo 2026 (zona general):** $330.57 MXN/día (factor de integración 1.0493 × $315.04).
- **Factor de integración mínimo (primer año, prestaciones de ley):** 1.0493.

## Tabla de vacaciones vigente (reforma 2023)

| Años de servicio | Días de vacaciones |
|---|---|
| 1 | 12 |
| 2 | 14 |
| 3 | 16 |
| 4 | 18 |
| 5 | 20 |
| 6-10 | 22 |
| 11-15 | 24 |
| 16-20 | 26 |
| 21-25 | 28 |
| 26-30 | 30 |
| 31-35 | 32 |

## Instituciones clave

- **PROFEDET:** 800 717 2942 y 800 911 7877. Asesoría y representación legal gratuita para trabajadores. Oficinas en cada estado.
- **Centro Federal de Conciliación y Registro Laboral (CFCRL):** www.centrolaboral.gob.mx. Conciliación obligatoria antes de demandar.
- **STPS:** www.gob.mx/stps. Inspección laboral, denuncia de violaciones.
- **IMSS:** 800 623 2323. Seguridad social, incapacidades, pensiones.
- **Infonavit:** 800 008 3900. Créditos de vivienda, devolución del fondo.
- **CONSAR:** 800 728 7835. Información sobre Afore y SAR.

## Guardrails generales del plugin

1. **No firmar nada.** Si el usuario menciona que le están pidiendo firmar algo (renuncia, convenio, finiquito), la primera instrucción es SIEMPRE: "No firmes nada sin que un abogado lo revise primero."
2. **Cálculos conservadores.** En caso de duda sobre si una prestación aplica, calcular sin ella y mencionarla como posible incremento. Nunca inflar expectativas.
3. **Conciliación primero.** Siempre mencionar que la conciliación prejudicial es obligatoria antes de demandar (salvo excepciones: discriminación por embarazo, acoso sexual, trata, trabajo infantil — art. 685 Ter LFT).
4. **PROFEDET siempre.** En cada respuesta donde se sugiera acción legal, mencionar PROFEDET como opción gratuita.
5. **Prescripción.** Si el usuario describe hechos que podrían estar prescritos, advertir inmediatamente y recomendar consulta urgente.
6. **Sin promesas.** No decir "te van a pagar X" o "vas a ganar." Decir "podrías tener derecho a X" o "la ley establece X."
7. **Gate de revisión** obligatorio para `demanda-laboral-drafter`. El borrador no se entrega sin advertencia clara de que requiere revisión profesional.

## Notas del usuario

> Espacio libre para notas personalizadas:

- [Ejemplo: "Esta clínica solo atiende casos de Puebla y Tlaxcala."]
- [Ejemplo: "Para casos de construcción, considerar el régimen especial del IMSS."]
