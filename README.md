Proyecto: Análisis de Migración de Conspiraciones en Reddit

En el presente documento se detalla la intención y estructura del trabajo

## 1. Intención del trabajo
Investigamos la hipótesis de que  
> **“Creer en teorías conspirativas aparentemente inofensivas puede llevar a aceptar otras que representen un riesgo real para la salud.”**  
Para demostrarlo, extraemos datos de Reddit con PRAW, construimos un grafo de usuarios y subreddits, y aplicamos métricas de teoría de grafos para:

- Detectar subreddits “inofensivos” desde los que migran usuarios hacia foros “peligrosos”.  
- Identificar los usuarios que actúan como puentes entre distintas conspiraciones.  
- Analizar la velocidad de propagación de nuevos mitos.  

Todo el pipeline está documentado en **trabajo_completo.ipynb** (scraping, grafo, métricas y visualización).

---

## 2. Estructura del repositorio