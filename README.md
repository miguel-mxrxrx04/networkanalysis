# Intención y desarrollo de la práctica 1 de Computación Social y Personalización

## Autores: Miguel Morera y Héctor Sancho, 2º CDIA UPM

El siguiente trabajo fue llamado **Social Virus** y el objetivo es el de estudiar cómo creencias aparentemente inofensivas en la red puede llevar a los usuarios 

En el documento **trabajo_completo.ipynb** hemos seguido los siguientes pasos:

1. **Recolectado datos con PRAW**  
   - Definimos una lista de subreddits asociados a cada teoría conspirativa.  
   - Para cada subreddit:  
     - Extraemos los últimos posts y sus comentarios.  
     - Creamos nodos para el subreddit y para cada autor, y aristas que conectan a los usuarios según sus interacciones (ser comentado en su post o comentar en un post ajeno).

2. **Montado el grafo de usuarios**  
   - Cada **vértice** = un usuario de Reddit.  
   - Cada **arista** = interacción usuario→usuario (comentario) o usuario→subreddit (publicación).  
   - Al finalizar, contamos **31 116 nodos** y **40 704 aristas**.

3. **Etiquetado y coloreado**  
   - Asignamos a cada usuario el atributo `subreddit` de su publicación principal.  
   - En la visualización final, cada color corresponde a una de las **5 conspiraciones**:

   1. **Negacionismo climático** (`#climateskeptics`, `#climatechangeisalie`)  
   2. **Teorías antivacunas** (`#antivaxxers`, `#vaccinehoax`)  
   3. **Astrología** (`#astrology`)  
   4. **Negación de la evolución** (`#creationism`, `#youngearthcreationists`)  
   5. **Fraude del alunizaje** (`#moonlandinghoax`)

4. **Detección de comunidades**  
   - Con Louvain encontramos clústeres temáticos perfectamente alineados con esas 5 categorías.  
   - El grafo muestra grupos concentrados en cada conspiración y también zonas de solapamiento.

5. **Métricas de la red**  
   - **Degree** y **Clustering**: cada comunidad forma un núcleo denso.  
   - **Betweenness** y **Closeness**: identificamos los “puentes” y “influencers” que unen o propagan ideas entre conspiraciones.

---

## Análisis de Comunidades (“Social Virus”)

La visualización revela **seis clústeres** principales en nuestro grafo de usuarios, cada uno identificado por color y temática:

| Clúster        | Color    | Temática                          |
|----------------|----------|-----------------------------------|
| **Aliens**     | Rosa     | Teorías extraterrestres           |
| **Simulación** | Verde    | Universo simulado                 |
| **Chemtrails** | Naranja  | Estelas químicas en la atmósfera  |
| **FlatEarth**  | Cian     | Terraplanismo                     |
| **Antivacunas**| Rojo     | Conspiraciones sobre vacunas      |
| **Epstein**    | Gris     | Teorías políticas (caso Epstein)  |
| **New World Order** | Amarillo | Gobierno mundial secreto     |
---

### Características clave por clúster

- **Aliens**  
  - **Más numeroso**: agrupa al mayor número de usuarios.  
  - **Alta densidad interna**: usuarios muy interconectados.  
  - **Puente** hacia *Antivacunas* y *Simulación*.

- **Simulación**  
  - **Segundo en tamaño**.  
  - **Solapamiento fuerte** con *Aliens* y *Chemtrails*.  
  - Usuarios escépticos de la “realidad oficial”.

- **Chemtrails**  
  - **Tamaño medio**.  
  - Conecta *Aliens* con *FlatEarth*.  
  - Enlace con narrativas de “New World Order” y *Epstein*.

- **FlatEarth**  
  - Comunidad **relativamente aislada**.  
  - Conexiones moderadas hacia *Chemtrails*.  
  - Intercambio limitado con otras teorías.

- **Antivacunas**  
  - **Más periférico** y pequeño en número.  
  - Conexiones de salida principalmente hacia *Aliens*.  
  - Puente en la transición de mitos cósmicos a narrativas médicas que ponen en peligro la salud.

- **Epstein**  
  - **Menor tamaño**; comunidad muy focalizada.  
  - Solapamiento con *Chemtrails* y *Simulación*.

- **New World Order**  
  - Usuarios que creen en un gobierno global oculto.  
  - Se solapa con **Chemtrails** y **Epstein**.

---

**Conclusión rápida**  
- *Aliens* y *Simulación* forman el **núcleo** de la red, teorías más famosas y más debate generan (público especializado y fanáticos)  
- *Chemtrails* actúa como **intermediario** entre grupos de “realidades alteradas” y teorías terrestres.  
- *FlatEarth*, *Antivacunas* y *Epstein* representan comunidades más **especializadas**, mostrando cómo las creencias “inofensivas” pueden ramificarse hacia conspiraciones con impacto real en la salud.
