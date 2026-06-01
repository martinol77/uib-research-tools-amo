9# CLAUDE.md — Alfredo Martín
# Universitat de les Illes Balears
# Este archivo se copia en cada proyecto nuevo. Editar aquí para actualizar todos los proyectos futuros.

---

## Perfil

- **Nombre:** Alfredo Martínez (martinol77@gmail.com)
- **Institución:** UIB — Universitat de les Illes Balears
- **Rol principal:** Investigador en economía aplicada (econometría empírica, finanzas corporativas, crédito bancario)
- **Rol secundario:** Director, Cátedra de Empresa Familiar, UIB
- **Idioma preferido para respuestas:** Inglés

---

## Proyecto principal activo

**Impacto de reestructuraciones bancarias (MOU) sobre el acceso al crédito de PyMEs españolas**

- Datos: CIR (Central de Información de Riesgos) — **confidenciales**, alojados en Banco de España
- Los archivos `.dta` locales son **datos ficticios/sintéticos** para desarrollo. Los resultados locales no tienen validez estadística — es lo esperado.
- Flujo: desarrollar `.do` en local → enviar a Banco de España → recibir resultados en `.smcl`
- Archivo principal: `compartidos6/archivo_final.do`
- Coautores: Gabriel, Anna, Sergio (y otros)

---

## Herramientas y metodología

### Stata (herramienta principal)
- `reghdfe` para regresiones con efectos fijos de alta dimensión
- `ppmlhdfe` para variables count (Poisson preferido sobre ln(1+n))
- LPM preferido sobre logit/probit cuando hay efectos fijos de alta dimensión
- `vce(cluster id_empresa)` como estándar; `vce(cluster id_empresa cnae_2d)` para two-way clustering
- Efectos fijos habituales: empresa (`id_empresa`), año (`anual`), provincia×año (`cpro_time`), sector×año (`cnae_2d_time`)
- Local projections con `F{h}.var` y `tsset id_empresa anual`
- `esttab` / `estout` para exportar tablas

### Python (análisis complementario)
- `pyreadstat` para leer `.dta`
- `linearmodels` o regresión manual para replicar `reghdfe`
- Scripts de barrido masivo de especificaciones (outputs en `.xlsx`)

### Convenciones Stata
- Todo do-file empieza con:
  ```stata
  clear all
  set more off
  cap log close
  ```
- Rutas con `cap cd` múltiples para compatibilidad entre máquinas
- Variables etiquetadas antes de guardar datos limpios
- Nombres de do-files con fecha: `archivo_final_20260601.do`

---

## Metodología econométrica — principios

- **Diseño antes que resultados**: definir estrategia empírica antes de mirar coeficientes
- Reportar siempre coeficientes + errores estándar, no solo stars
- Significancia económica tan importante como estadística
- En modelos polinomiales: respetar el **principio de marginalidad** (incluir términos de orden inferior salvo hipótesis teórica explícita)
- IV/2SLS: solo si el primer estadio es sólido. Instrumentos débiles → reduced form directa
- Event study con leads/lags para verificar parallel trends antes de DiD

---

## Estructura de proyecto (generada por /newproject)

```
proyecto/
├── CLAUDE.md              # Copiado de este template
├── README.md              # Notas específicas del proyecto
├── code/
│   ├── stata/
│   └── python/
├── data/
│   ├── raw/               # Solo lectura — nunca modificar
│   └── clean/
├── output/
│   ├── tables/
│   ├── figures/
│   └── logs/
├── documents/             # PDFs de referencia
├── decks/                 # Presentaciones
├── notes/
└── progress_logs/         # Logs de sesión (YYYY-MM-DD_descripcion.md)
```

---

## Continuidad entre sesiones

- Al inicio de cada sesión: leer el log más reciente en `progress_logs/`
- Al final de cada sesión: escribir `progress_logs/YYYY-MM-DD_descripcion.md` con:
  - Qué se hizo
  - Decisiones tomadas
  - Qué queda pendiente

---

## Presentaciones

- Audiencia académica: metodología primero, resultados después
- Audiencia empresarial (Cátedra Empresa Familiar): mensaje económico primero, metodología al final o en apéndice
- Títulos de slides = afirmaciones, no temas ("Las firmas MOU pierden acceso al crédito", no "Resultados")
- Una idea por slide

---

## Notas para Claude

- Responder siempre en inglés salvo que el usuario escriba en español
- Al leer `archivo_final.do` (>2000 líneas), usar offset+limit por secciones
- Los datos locales son ficticios — no interpretar resultados locales como válidos
- Cuando el usuario traiga un log `.smcl` con líneas `RESULT|...`, extraerlas para construir tablas LaTeX
- Si hay duda metodológica, presentar opciones con pros/contras antes de implementar
