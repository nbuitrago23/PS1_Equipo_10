# PS1_EQUIPO_10 — Big Data & Machine Learning para Economía Aplicada

Repositorio del Proyecto Set 1 (Grupo 10). Analizamos el mercado laboral y la **brecha salarial de género** usando R: limpieza de datos, imputación de salario por hora, perfil edad–salario, FWL, bootstrap e inferencia, y evaluación predictiva (holdout 70/30 y LOOCV).

> **Repositorio:** [https://github.com/nbuitrago23/PS1_Equipo_10](https://github.com/nbuitrago23/PS1_Equipo_10)

---

## Estructura del repositorio

- `document/` — Documento final, y presentaciones.  
- `scripts/` — Códigos en R.  
- `stores/` — Salidas del proyecto (tablas, figuras, reportes).

---

## Scripts (orden de ejecución)

1. **Initial configuration**  
   - Carga/instala paquetes, fija opciones (p. ej. `options(scipen=999)`), rutas y semillas.

2. **Web Scrapping (loading data)**  
   - Lee los 10 “chunks” del repositorio de datos brindado y arma un dataset conjunto: `master_data`.

3. **Data cleaning**  
   - Filtra edad ≥ 18, ocupados, crea dummies (educación, estrato, tamaño firma, relab), `age2`, etc.

4. **Hourly wage imputation**  
   - Imputa `y_ingLab_m` con `impa`+`isa`, filtra salarios > 0 y crea `ingreso_hora`.

5. **Descriptive Statistics**  
   - Resumen para numéricas y frecuencias para categóricas.  
   - Exporta tablas (Word/HTML) con `stargazer` y `flextable`.

6. **Age wage profile**  
   - Modelo `log(ingreso_hora) ~ age + age^2`.  
   - Bootstrap del pico de salario por edad y bandas de confianza, se generan gráficos utilizando `ggplot2`.

7. **Gender earnings gap**  
   - Modelo simple por género, FWL con controles, bootstrap del coef. de `female`.  
   - Curvas edad×género con ICs.

8. **Predicting wages**  
   - Partición 70/30, cálculo de **Test RMSE** por modelo.  
   - **LOOCV** para especificaciones clave y comparación de errores.  
   - Exporta tablas comparativas (RMSE holdout vs LOOCV).

---

## Replicación

1. **Clonar o descargar** este repo.  
2. Abrir en **R/RStudio**.  
3. Verificar la ruta de trabajo.  
4. Ejecutar los scripts de `scripts/` en el orden 1 al 8.  
5. Las salidas se guardan en `stores/`.

**Paquetes usados (principales):**
```r
# instalar si hace falta:
packages <- c(
  "pacman","rio","tidyverse","skimr","visdat","corrplot","stargazer",
  "rvest","readr","lubridate","openxlsx","stringr","readxl","ggplot2",
  "boot","sandwich","lmtest","caret","flextable","officer"
)

