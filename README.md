# FisicoquimIA

Sistema de aprendizaje de **Propiedades fisico-químicas de alimentos (1536)**, Grado en Ciencia y Tecnología de los Alimentos (UMH, EPSO). Aplicación web de un solo fichero (`index.html`), sin servidor. Español, inglés y portugués (`?lang=en`, `?lang=pt`).

**Usar la app:** https://fborrasumh.github.io/fisicoquimia/

## Qué hace
- Diagnóstico inicial de 7 preguntas (una por resultado de aprendizaje, RA) y ruta adaptativa que muestra **por qué** toca cada actividad.
- 20 plantillas de problemas con datos distintos en cada variante; **la solución la calcula el código** y los errores típicos se diagnostican recalculando. Ejemplo resuelto la primera vez que se practica una plantilla.
- 20 preguntas de test (4 opciones, opciones barajadas, análisis de distractores).
- Laboratorio con tres gráficas: isoterma GAB/BET, curva de flujo (Herschel-Bulkley) y cremado (Stokes).
- Dominio estimado por RA con olvido y repaso espaciado (cajas de 1, 3, 7 y 21 días).
- Panel del profesorado: analítica de ítems (acierto, discriminación, distractores), propuestas de mejora generadas por código y decididas por el profesorado, informe de cambios, exportación a Moodle XML / GIFT / CSV y exámenes individualizados reproducibles con semilla.
- Guía y nota: ficha de la guía, RA y unidades, carga de trabajo y calculadora de las reglas de evaluación de la guía.
- Currículo como datos: `src/curriculum.js`. Otra asignatura o universidad la adopta cambiando ese fichero y el banco de ítems.

## Cómo se usa la IA
Opcional, con la clave propia (OpenAI, Gemini o Claude). Solo sirve para pedir una **pista** en un problema. La IA no calcula ni pone nota: antes del primer envío se muestra lo que sale (enmascarado) y el código elimina de la respuesta las frases que contengan el resultado.

## Privacidad
Todo el progreso se guarda en el navegador (IndexedDB). Compartir datos con el profesorado es voluntario: el estudiante exporta un JSON con un identificador aleatorio, las respuestas y una huella SHA-256 (detecta ediciones; no prueba autoría). No contiene nombre, correo ni texto libre.

## Investigación
La app produce el dataset y el panel, pero **no sustituye** la aprobación del comité de ética (OEP en la UMH), el consentimiento informado ni un diseño de estudio con grupo de comparación (idealmente preregistrado).

## Límites
- El modelo adaptativo (habilidad tipo Rasch con olvido) es simplificado y **no está validado con datos reales**.
- Las fórmulas son las habituales de manual; el profesorado debe revisarlas antes de usarlas en evaluación.
- Banco inicial pequeño: los RA 03, 05 y 06 tienen 3 ítems cada uno; el RA 07 no tiene unidades asociadas en la guía.
- Los textos de los RA 01 y 02 se reconstruyeron porque el PDF de la guía los mezclaba con un aviso de cookies: contrástense con la guía original.
- Accesibilidad: comprobada con axe-core (WCAG 2.2 A/AA, 0 infracciones en las pantallas probadas) y con teclado; no sustituye una auditoría con personas usuarias.
- No se ha probado con una clave de IA real ni con estudiantes reales. No hay LTI ni inicio de sesión institucional (necesitan servidor).

## Pruebas
`node tests/logic_test.js` (lógica pura, oráculos independientes) y `python3 tests/fq_test.py` (Chromium con IA simulada: flujo, exportaciones, idiomas, sin red, gama baja, teclado, axe, móvil).

## Autoría
Fernando Borrás Rocher (Universidad Miguel Hernández de Elche), Juana Fernández López (Universidad Miguel Hernández de Elche) y Luis Noguera Artiaga (Universidad Miguel Hernández de Elche).

A partir de la Guía Docente de la asignatura 1536 (Grado en Ciencia y Tecnología de los Alimentos, EPSO-UMH, curso 2026-2027), cuya responsable es Juana Fernández López.

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · Juana Fernández López [0000-0002-4771-8437](https://orcid.org/0000-0002-4771-8437). Luis Noguera Artiaga [0000-0001-9269-1125](https://orcid.org/0000-0001-9269-1125).

## Cómo citar
Borrás Rocher, F., Fernández López, J. y Noguera Artiaga, L. (2026). *FisicoquimIA* (v1.0.0) [Software]. (DOI en trámite)

## Licencia
MIT (software). Véase [LICENSE](LICENSE). Los contenidos pedagógicos y los datos suelen publicarse con CC BY 4.0; si se mantiene MIT para todo, se respeta.
