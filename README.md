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

## Conspiraciones estudiadas y guía para entender el grafo

La visualización “Social Virus” revela seis comunidades principales en nuestro grafo de usuarios:

| Clúster        | Color    | Temática                         | Características clave                                                                                               |
|----------------|----------|----------------------------------|---------------------------------------------------------------------------------------------------------------------|
| **Aliens**     | Rosa     | Teorías extraterrestres          | - **Más numeroso**: congrega al mayor número de usuarios.  
                                                - **Alta densidad interna**: usuarios muy interconectados.  
                                                - **Puente** natural hacia “Antivacunas” y “Simulación”.                           |
| **Simulación** | Verde    | Teoría del universo simulado     | - **Segundo en tamaño**.  
                                                - **Fuerte solapamiento** con “Aliens” y “Chemtrails”: comparten usuarios que desconfían de la realidad oficial. |
| **Chemtrails** | Naranja  | Avión-pesticida en el cielo      | - Comunidad mediana.  
                                                - **Puentes** claros hacia “Aliens” y “FlatEarth”.  
                                                - Usuarios que también discuten “New World Order” y “Epstein”.            |
| **Flatearth**  | Cian     | Terraplanismo                    | - Agrupación más aislada, con conexiones moderadas hacia “Chemtrails”.  
                                                - Usuarios estrictos: intercambio limitado con otras teorías.                    |
| **Antivacunas**| Rojo     | Conspiraciones sobre vacunas     | - **Más periférico** y pequeño en número.  
                                                - Conexiones de salida hacia “Aliens” (usuarios puente) más que entrada.        |
| **Epstein**    | Gris     | Teorías sobre Jeffrey Epstein    | - **Menor tamaño**; comunidad muy focalizada.  
                                                - Intersecta sobre todo con “Chemtrails” y “Simulación”.                    |

### Insights clave

1. **Aliens y Simulación** dominan la red  
   - Su gran tamaño y densidad los convierten en los nodos centrales del discurso conspirativo.  
   - Actúan de **hubs** desde donde emergen puentes a otras narrativas.

2. **Chemtrails como conector**  
   - Sirve de intermediario entre grupos de “realidades alteradas” (Aliens, Simulación) y teorías más “terrestres” (FlatEarth).  
   - Suele compartir usuarios con Epstein y New World Order, ampliando su alcance.

3. **FlatEarth y Antivacunas, más aislados**  
   - Terraplanismo mantiene una comunidad propia con poca mezcla.  
   - Antivacunas, aunque pequeña, está conectada a “Aliens” por un núcleo de usuarios que migran de la especulación cósmica a la desconfianza médica.

4. **Epstein, comunidad de nicho**  
   - Aunque es el clúster minoritario, su presencia indica que temas de conspiración política (caso Epstein) también forman parte del ecosistema, solapándose principalmente con “Chemtrails” y “Simulación”.

---

**Conclusión**:  
Cada clúster representa una narrativa conspirativa distinta, con tamaños y grados de interconexión propios.  
- **Aliens** y **Simulación** son los motores de la red,  
- **Chemtrails** actúa como puente,  
- **FlatEarth**, **Antivacunas** y **Epstein** son comunidades más especializadas.  

Este mapa nos ayuda a entender no solo qué teorías son más populares, sino también **cómo** y **por dónde** circula la información que las conecta.  



