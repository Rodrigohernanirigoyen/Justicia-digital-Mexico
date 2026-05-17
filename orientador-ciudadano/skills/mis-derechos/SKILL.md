---
name: mis-derechos
description: >
  Explica los derechos que el usuario tiene en una situación específica, en
  lenguaje cotidiano y con ejemplos prácticos. Cubre derechos fundamentales
  (CPEUM, tratados internacionales) y derechos específicos por situación:
  como víctima, como trabajador, como consumidor, como migrante, como persona
  detenida, como paciente, como estudiante, como inquilino, como mujer en
  situación de violencia, como persona LGBT+, como persona con discapacidad,
  como adulto mayor, como niña/niño/adolescente.
argument-hint: "Dime en qué situación estás o qué derechos quieres conocer"
user-invocable: true
---

# Mis Derechos — Explicación en lenguaje claro

## Cuándo se activa

- El usuario pregunta "¿qué derechos tengo?", "¿puedo exigir esto?", "¿es legal que me hagan esto?", "¿qué dice la ley sobre mi situación?".
- El usuario describe una situación y quiere entender qué le protege.
- Otro skill del plugin necesita explicar al usuario el marco de derechos antes de entrar al detalle procesal.

## Comportamiento

### Paso 1: Identificar el contexto

Si el usuario no especifica, pregunta:

> "Para darte la información más útil, dime: ¿en qué situación o calidad quieres saber tus derechos? Por ejemplo: como trabajador, como víctima de un delito, como consumidor, como inquilino, como paciente, etc."

Si el usuario ya describió la situación, identifica internamente la(s) categoría(s) aplicable(s) y procede.

### Paso 2: Estructura de la respuesta

Para cada conjunto de derechos relevantes, explica:

1. **El derecho en una oración cotidiana** (sin tecnicismo).
2. **De dónde viene** (Constitución, ley, tratado — en lenguaje claro: "Esto lo protege la Constitución, en su artículo 14, que dice que…").
3. **Un ejemplo concreto** de cómo se aplica.
4. **Qué hacer si se viola** (a quién acudir).

### Paso 3: Catálogos de derechos por situación

#### Como persona en general (derechos fundamentales)

- **Derecho a la vida y a la integridad personal.** Nadie puede agredirte, torturarte ni amenazar tu vida. Si esto pasa, es delito y violación a derechos humanos.
- **Derecho a la libertad personal.** Nadie puede detenerte sin orden judicial, salvo en flagrancia o caso urgente. Si te detienen, debes saberlo en el momento, conocer el motivo, y ser presentado ante autoridad sin demora.
- **Derecho a la igualdad y no discriminación.** Nadie puede tratarte distinto por tu sexo, edad, raza, religión, orientación sexual, discapacidad, condición social, idioma, opiniones políticas, etc.
- **Derecho al debido proceso.** En cualquier procedimiento legal (penal, civil, administrativo), tienes derecho a: ser oído, presentar pruebas, tener abogado, conocer las acusaciones, ser informado en tu idioma.
- **Derecho a la privacidad.** Tu casa, comunicaciones, datos personales y vida privada están protegidos. Para revisarlos se requiere orden judicial.
- **Derecho a la libertad de expresión, reunión, asociación y manifestación.**
- **Derecho a la educación, salud y vivienda digna** (derechos sociales).
- **Derecho de petición.** Puedes pedir por escrito cosas a las autoridades, y deben responder por escrito en plazo razonable.

#### Como víctima de un delito (Ley General de Víctimas)

- **Derecho a ser tratada con dignidad y respeto** durante todo el proceso.
- **Derecho a asesoría jurídica gratuita** (la CEAV federal o las estatales).
- **Derecho a información** sobre el estado de tu caso, en tu idioma.
- **Derecho a la reparación integral** del daño: restitución, indemnización, satisfacción, garantías de no repetición, rehabilitación.
- **Derecho a medidas de protección** si tu vida o integridad corre peligro.
- **Derecho a que no te confronten** con quien te victimizó (especialmente en violencia familiar y delitos sexuales).
- **Derecho a coadyuvar** con el MP — aportar pruebas, sugerir diligencias, opinar.
- **Derecho a recibir copia gratuita de todas las actuaciones** del proceso.
- **Derecho a apelar** decisiones que te afecten (sobreseimiento, no ejercicio de la acción penal).
- **Derecho a estar inscrita en el RENAVI** (Registro Nacional de Víctimas) y acceder a recursos del Fondo de Ayuda.

#### Como persona detenida o imputada (Art. 20 CPEUM)

- **Presunción de inocencia.** Eres inocente hasta que se demuestre lo contrario.
- **Derecho a guardar silencio.** No estás obligado a declarar. Si declaras sin abogado, no puede usarse en tu contra.
- **Derecho a un abogado desde el momento de la detención.** Si no tienes recursos, el Estado debe darte uno (defensor público).
- **Derecho a comunicarte con tu familia.**
- **Derecho a un traductor** si no hablas español o si eres indígena.
- **No ser obligado a declararte culpable.** La confesión obtenida sin abogado o bajo coacción no vale.
- **A ser presentado ante el juez en menos de 48 horas** (96 horas en delincuencia organizada).
- **A un proceso público y oral**, con todas las garantías.

#### Como trabajadora o trabajador

- **Salario mínimo** y pago puntual (semanal/quincenal/mensual según contrato).
- **Aguinaldo** equivalente a 15 días de salario antes del 20 de diciembre.
- **Vacaciones**: a partir de 2023, 12 días al primer año, escalando hasta 22 días al sexto año.
- **Prima vacacional** del 25% del salario de vacaciones.
- **Prima de antigüedad** (12 días por año al retirarse).
- **Reparto de utilidades** (PTU) anual, si la empresa tuvo ganancias.
- **Seguridad social** (IMSS): atención médica, incapacidades, pensión.
- **Día de descanso semanal** (mínimo uno por cada seis días trabajados).
- **Jornada máxima**: 8 horas diurna, 7 nocturna, 7.5 mixta.
- **Pago de tiempo extra** (doble o triple según el caso).
- **Indemnización por despido injustificado**: 3 meses + 20 días por año + prestaciones.
- **No discriminación** por embarazo, edad, género, etc.
- **Capacitación y adiestramiento** a cargo del patrón.
- **A formar o afiliarse a sindicato**, libremente.

#### Como mujer en situación de violencia (Ley Gral. de Acceso de las Mujeres a una Vida Libre de Violencia)

- **Derecho a vivir sin violencia** en lo familiar, laboral, comunitario, institucional.
- **Medidas de protección inmediatas** del MP o del juez (orden de alejamiento, custodia provisional de hijos, salida del agresor del domicilio).
- **Acceso a refugios** seguros, gratuitos, con atención integral.
- **Atención médica, psicológica y jurídica gratuita.**
- **No ser revictimizada** con preguntas ofensivas o trato discriminatorio.
- **Acompañamiento** durante el proceso por persona de confianza.
- **Confidencialidad** sobre datos e identidad.
- **Acceso a anticoncepción de emergencia y aborto** en casos de violación (Norma 046, NOM-046).

#### Como consumidora o consumidor (PROFECO, LFPC)

- **Información clara y completa** sobre productos y servicios.
- **Precios y condiciones** anunciados deben respetarse.
- **Garantías**: por ley, mínimo legal aplica aunque la empresa no la mencione.
- **Devolución, reposición o reembolso** si el producto es defectuoso.
- **Cancelación de servicios** sin penalización si no se cumple lo ofrecido.
- **Protección contra publicidad engañosa.**
- **Protección de datos** y no uso indebido para mercadotecnia sin consentimiento.
- **Conciliación gratuita** ante PROFECO.

#### Como inquilina o inquilino

- **No ser desalojada sin juicio.** El propietario no puede sacarte por la fuerza ni cambiar la chapa. Si quiere desalojarte, debe demandar.
- **Recibo de pago de la renta.**
- **Mantenimiento estructural** a cargo del arrendador.
- **No ser cobrada por encima del contrato.**
- **A devolución del depósito** al final del contrato, si no hay daños.
- **Plazos para entregar** la propiedad razonables.

#### Como persona con discapacidad

- **Acceso al entorno físico, transporte, información, comunicaciones** sin barreras.
- **Educación inclusiva.**
- **Trabajo digno y ajustes razonables.**
- **Capacidad jurídica plena** — derecho a tomar tus propias decisiones (con apoyos si los necesitas, NUNCA por sustitución).
- **Salud accesible y sin discriminación.**
- **A no ser internado en contra de tu voluntad** sin debido proceso.
- **Comunicación accesible**: lengua de señas, lectura fácil, sistema braille.

#### Como persona adulta mayor

- **Trato preferente** en trámites públicos.
- **Pensión no contributiva** universal (a partir de cierta edad).
- **Atención médica gratuita** (INSABI/IMSS Bienestar).
- **A no ser maltratada ni abandonada** por familiares.
- **Vivienda y patrimonio** respetados (cuidado con estafas y firmas presionadas).

#### Como niña, niño o adolescente (CRC, LGDNNA)

- **Interés superior**: en cualquier decisión que les afecte, su bienestar va primero.
- **A ser escuchados** según su edad y madurez.
- **A la educación, salud, alimentación, identidad, familia.**
- **A no ser maltratados, explotados, abusados.**
- **A la justicia especializada** si entran al sistema penal (sistema integral de justicia para adolescentes).
- **A no ser separados de su familia** salvo por orden judicial fundada.

#### Como migrante (sin importar estatus)

- **Derechos humanos** son aplicables a toda persona, sin importar estatus migratorio.
- **A no ser detenido más de 36 horas** por motivos migratorios sin presentación ante autoridad.
- **A solicitar refugio** si huye de persecución (COMAR).
- **A la unidad familiar.**
- **A atención médica de urgencia.**
- **A la educación básica para sus hijos.**
- **A asistencia consular** (Convención de Viena).
- **A no ser deportado a un país donde corra peligro** (principio de no devolución).

#### Como persona LGBT+

- **Igualdad y no discriminación** por orientación sexual, identidad o expresión de género.
- **Matrimonio igualitario** (vigente en todos los estados).
- **Adopción.**
- **Reconocimiento de identidad de género** mediante procedimiento administrativo en muchos estados.
- **Servicios de salud específicos** (terapia hormonal, salud sexual, etc.).
- **Protección frente a discursos de odio.**
- **Asilo** por persecución por orientación sexual o identidad de género.

#### Como paciente

- **Información clara** sobre tu diagnóstico, tratamientos disponibles, riesgos y costos.
- **Consentimiento informado** antes de cualquier intervención.
- **Confidencialidad** del expediente clínico.
- **Acceso a tu expediente clínico** — es tuyo, no del hospital.
- **Segunda opinión.**
- **No ser sometida a estudios o experimentos** sin consentimiento.
- **Trato digno** y respetuoso de tus creencias.
- **Voluntad anticipada** (decir cómo quieres que sea tu atención al final de la vida).

#### Como persona indígena

- **Derecho a la autonomía y libre determinación** de los pueblos.
- **A la consulta previa, libre e informada** sobre proyectos que les afecten.
- **A su lengua, cultura, sistemas normativos.**
- **A traductor en cualquier procedimiento** legal.
- **Tierras y territorios** ancestrales.
- **Educación bilingüe.**

#### Como persona LGBT+ con casos de salud sexual

- **A solicitar PrEP, PEP** y otros métodos de prevención del VIH.
- **Atención sin discriminación** en hospitales públicos.
- **A no ser sometida a "terapias de conversión"** (ahora prohibidas en CDMX y varios estados).

### Paso 4: Cierre

Termina con:

1. **Si alguno de tus derechos está siendo violado, [acción concreta].**
2. **Si quieres saber a dónde acudir, puedo ayudarte** (sugerir `donde-acudo`).
3. **Si necesitas un abogado, en [tu estado] hay servicios gratuitos** (sugerir `servicios-gratuitos-mapper`).
4. **Disclaimer.**

## Guardrails

- **No omitas derechos por incomodidad.** Si la persona pregunta como migrante indocumentada, dile sus derechos completos sin moralizar.
- **No dramatices.** Explica los derechos con claridad, sin retórica de indignación.
- **No confundas derechos con expectativas.** El derecho existe; lograr que se respete es otra cosa. Sé honesta sobre la diferencia.
- **Conecta con acción.** Cada derecho que mencionas debe venir con "y si te lo violan, haces X."
- **Verifica jurisdicción.** Algunos derechos varían por estado (por ejemplo, identidad de género autodeterminada está en algunos estados, no en todos).

## Fuentes

- `references/glosario-ciudadano.md` (para traducir términos).
- `references/instituciones-mexico.md` (a dónde reclamar).
- `references/servicios-gratuitos-estados.md` (apoyos gratuitos).
- `CLAUDE.md` (estado y perfil del usuario).

## Disclaimer

> "Esta orientación es informativa. Para hacer valer tus derechos en un caso específico, te recomiendo apoyarte en un abogado. Si no tienes recursos, hay opciones gratuitas en tu estado."
