---
name: calculadora-liquidacion
description: >
  Calcula la liquidación o indemnización que corresponde a un trabajador en
  México por despido injustificado, renuncia voluntaria, o terminación de
  relación laboral, conforme a la Ley Federal del Trabajo. Usa valores
  actualizados 2026 (salario mínimo $315.04, UMA $117.31). Presenta el
  desglose completo de cada concepto con la fórmula aplicada. Distingue
  entre finiquito (renuncia) y liquidación (despido injustificado).
argument-hint: "Dime tu salario, antigüedad, y si renunciaste o te despidieron"
user-invocable: true
---

# Calculadora de Liquidación / Indemnización

## Cuándo se activa

- El usuario pregunta "cuánto me toca", "cuánto me deben", "cuánto es mi liquidación", "cómo calculo mi finiquito".
- Después de que `despido-injustificado-triage` determina que el despido fue injustificado.
- El usuario invoca `/laboral-mx:calculadora-liquidacion`.

## Paso 1: Recopilar datos

Necesitas estos datos para calcular. Pregunta lo que no tengas:

1. **Salario mensual bruto** (o diario, o quincenal — el usuario puede dar cualquiera y tú conviertes).
2. **Fecha de ingreso** (o años de antigüedad).
3. **Fecha de separación** (o "ayer", "hace una semana", etc.).
4. **Motivo de separación:** despido injustificado, renuncia voluntaria, rescisión del trabajador (art. 51 LFT), mutuo consentimiento, muerte del trabajador.
5. **¿Recibía prestaciones superiores a la ley?** (más de 15 días de aguinaldo, más de 25% de prima vacacional, fondo de ahorro, vales de despensa, bonos).
6. **¿Tiene vacaciones pendientes sin gozar?**

Si el usuario no sabe su salario exacto, pídele el aproximado. Si no recuerda la fecha exacta de ingreso, acepta "como 3 años" y calcula con eso.

## Paso 2: Calcular el Salario Diario Integrado (SDI)

El SDI es la base para indemnización y salarios caídos. Se calcula sumando al salario diario la parte proporcional de aguinaldo y prima vacacional.

```
Salario diario = Salario mensual / 30

Factor de integración = 1 + (días de aguinaldo / 365) + (días de vacaciones × prima vacacional / 365)

Para prestaciones mínimas de ley, primer año:
Factor = 1 + (15/365) + (12 × 0.25 / 365) = 1 + 0.0411 + 0.0082 = 1.0493

SDI = Salario diario × Factor de integración
```

**Factores de integración por antigüedad (prestaciones mínimas de ley):**

| Años | Días vacaciones | Factor |
|---|---|---|
| 1 | 12 | 1.0493 |
| 2 | 14 | 1.0507 |
| 3 | 16 | 1.0521 |
| 4 | 18 | 1.0534 |
| 5 | 20 | 1.0548 |
| 6-10 | 22 | 1.0562 |
| 11-15 | 24 | 1.0575 |
| 16-20 | 26 | 1.0589 |
| 21-25 | 28 | 1.0603 |
| 26-30 | 30 | 1.0616 |
| 31-35 | 32 | 1.0630 |

Si el usuario tiene prestaciones superiores, ajustar el factor con sus datos reales.

## Paso 3: Calcular según el motivo de separación

### A) DESPIDO INJUSTIFICADO — Liquidación

El trabajador elige entre reinstalación o indemnización. La gran mayoría elige indemnización. Incluye:

| Concepto | Fórmula | Base legal |
|---|---|---|
| **Indemnización constitucional** | 3 meses × SDI × 30 | Art. 48 LFT |
| **20 días por año** | (Años × 20) × SDI | Art. 50 fracc. II LFT |
| **Prima de antigüedad** | Años × 12 × min(salario diario, 2 × salario mínimo) | Art. 162 LFT |
| **Salarios caídos** | Días desde despido hasta pago o hasta 12 meses × SDI | Art. 48 LFT |
| **Vacaciones proporcionales** | (Días trabajados en el último año / 365) × días de vacaciones × salario diario | Art. 76, 79 LFT |
| **Prima vacacional proporcional** | Vacaciones proporcionales × 25% (o % superior) | Art. 80 LFT |
| **Aguinaldo proporcional** | (Días trabajados en el año / 365) × 15 días × salario diario | Art. 87 LFT |

**Notas sobre la prima de antigüedad:**

- Se calcula con 12 días de salario por cada año de servicio.
- El salario para este concepto tiene un **tope de 2 veces el salario mínimo** ($315.04 × 2 = $630.08 diarios en 2026).
- Aplica aunque el trabajador gane $100,000 mensuales — el tope siempre aplica.

**Notas sobre salarios caídos:**

- Si el juicio se resuelve en menos de 12 meses: se pagan los salarios desde el despido hasta la resolución.
- Si el juicio dura más de 12 meses (lo más común): se pagan 12 meses de salarios caídos + intereses del 2% mensual sobre 15 meses de salario, capitalizables al momento del pago.
- Para la calculadora, presentar dos escenarios: sin salarios caídos (si se llega a convenio rápido) y con 12 meses.

### B) RENUNCIA VOLUNTARIA — Finiquito

| Concepto | Fórmula | Base legal |
|---|---|---|
| **Vacaciones proporcionales** | (Días trabajados / 365) × días de vacaciones × salario diario | Art. 76, 79 |
| **Prima vacacional proporcional** | Vacaciones proporcionales × 25% | Art. 80 |
| **Aguinaldo proporcional** | (Días trabajados en el año / 365) × 15 × salario diario | Art. 87 |
| **Prima de antigüedad** | Solo si tiene 15+ años de servicio: años × 12 × min(salario, 2×SM) | Art. 162 |
| **Salarios pendientes** | Días trabajados no pagados × salario diario | Art. 82 |

**NO incluye** indemnización constitucional ni 20 días por año. Esa es la diferencia fundamental entre finiquito y liquidación.

### C) RESCISIÓN POR CULPA DEL PATRÓN (Art. 51 LFT)

Cuando el trabajador se va porque el patrón incumplió gravemente (no pagar salario, reducir salario, acoso, riesgo de salud, etc.). Le corresponde lo mismo que despido injustificado:

- Indemnización constitucional (3 meses).
- 20 días por año.
- Prima de antigüedad.
- Salarios caídos.
- Proporcionales (vacaciones, prima vacacional, aguinaldo).

## Paso 4: Presentar el resultado

### Para trabajadores (sin formación legal)

Presenta así:

> **Tu liquidación estimada**
>
> Con base en lo que me dijiste (salario de $X, antigüedad de Y años, despido injustificado el [fecha]):
>
> **Concepto por concepto:**
>
> 1. **Indemnización constitucional (3 meses de sueldo):**
>    $[SDI] × 90 días = **$[monto]**
>    *(Esto es un "castigo" al patrón por despedirte sin justificación)*
>
> 2. **20 días por cada año trabajado:**
>    [años] años × 20 días × $[SDI] = **$[monto]**
>    *(Es una compensación adicional por el tiempo que trabajaste)*
>
> 3. **Prima de antigüedad:**
>    [años] años × 12 días × $[salario topado] = **$[monto]**
>    *(Tiene un tope legal: máximo $630.08 diarios, aunque ganes más)*
>
> 4. **Vacaciones proporcionales + prima vacacional:**
>    [cálculo] = **$[monto]**
>
> 5. **Aguinaldo proporcional:**
>    [cálculo] = **$[monto]**
>
> 6. **Salarios caídos (si el juicio tarda):**
>    Hasta 12 meses × $[SDI] × 30 = **$[monto]**
>    *(Esto no se paga de inmediato; se acumula durante el juicio)*
>
> ---
>
> **TOTAL SIN salarios caídos:** $[monto]
> **TOTAL CON 12 meses de salarios caídos:** $[monto]
>
> ⚠️ **Importante:**
> - Este cálculo es una estimación. Puede variar.
> - Si tu patrón te ofrece un convenio, compara con estos números.
> - **No aceptes menos de lo que te corresponde sin consultar a un abogado.**
> - PROFEDET te asesora y calcula gratis: 800 717 2942.

### Para abogados (profesional)

Presenta en formato tabular técnico con fórmulas, artículos, y SDI desglosado. Sin explicaciones pedagógicas.

## Paso 5: Recomendaciones post-cálculo

Después del cálculo, ofrece:

1. **¿Quieres preparar la solicitud de conciliación?** → sugerir `conciliacion-prejudicial`.
2. **¿Necesitas evaluar si tu despido fue justificado?** → sugerir `despido-injustificado-triage`.
3. **¿No te han pagado y necesitas demandar?** → sugerir `demanda-laboral-drafter`.
4. **¿Quieres que un abogado revise estos números gratis?** → PROFEDET.

## Guardrails

- **Nunca redondear a favor del trabajador** para no inflar expectativas. Redondear a centavos.
- **Si el usuario dice que ya firmó un finiquito/convenio**, preguntar inmediatamente cuánto le pagaron y comparar con lo que le correspondía. Si hay diferencia significativa, informar que puede reclamar la diferencia.
- **Si la antigüedad es mayor a 20 años**, advertir que el monto de 20 días por año puede ser muy alto y que algunos patrones intentan negociar. Recomendar abogado.
- **Si el salario parece muy bajo** (inferior al mínimo), señalarlo como posible irregularidad.
- **No incluir ISR** en el cálculo. Las indemnizaciones laborales por despido están exentas de ISR hasta ciertos montos (art. 93 LISR). Señalar que el detalle fiscal lo debe verificar un contador o PROFEDET.
- **Siempre distinguir** entre finiquito (renuncia) y liquidación (despido). Es el error más común.

## Fuentes

- `references/datos-laborales-2026.md` (valores numéricos vigentes).
- `references/tabla-vacaciones-lft.md` (tabla de vacaciones).
- `CLAUDE.md` (perfil del usuario, nivel de lenguaje).

## Disclaimer

> "Este cálculo es una estimación basada en la información que proporcionaste y en los valores vigentes de la LFT para 2026. El monto final puede variar. Antes de aceptar un convenio o presentar una demanda, te recomiendo verificar estos números con PROFEDET (gratis: 800 717 2942) o con un abogado laboralista."
