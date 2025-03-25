
# FlixBus European 2024 Trips Insights

This project explores and analyzes the **FlixBus European 2024 trips dataset**. The dataset contains information on bus trips between cities across Europe, including their origin and destination cities, countries, and various related attributes. The goal of the analysis is to uncover interesting insights into the structure and behavior of the bus network, focusing on key metrics such as **degree centrality**, **betweenness centrality**, **bidirectional routes**, **strongly connected components**, and the **shortest paths** between cities.

## Table of Contents
1. Data Overview
2. Graph Construction
3. Key Metrics and Visualizations
   - Degree Centrality
   - Betweenness Centrality
   - Bidirectional Routes
   - Shortest Paths
4. Country Connections Analysis
5. Graphs and Outputs

## Data Overview
The analysis begins with loading and merging the two datasets: `cities_data.csv` and `trips_data.csv`. The cities data provides information about the cities (name, country, etc.), while the trips data contains records of bus routes between cities.

The **European countries** were filtered to focus the analysis on trips where both the origin and destination cities belong to European countries. This was done by merging the datasets and filtering by the country column.

| from      | to        | from_country | to_country | trip            |
|-----------|-----------|--------------|------------|-----------------|
| Podgorica | Durrës    | Montenegro   | Albania    | Podgorica-Durrës |
| Budva     | Durrës    | Montenegro   | Albania    | Budva-Durrës     |
| Durrës    | Budva     | Albania      | Montenegro | Durrës-Budva     |
| Durrës    | Dubrovnik | Albania      | Croatia    | Durrës-Dubrovnik |
| Kotor     | Durrës    | Montenegro   | Albania    | Kotor-Durrës     |
| ...       | ...       | ...          | ...        | ...              |

## Graph Construction
The data was used to construct a **directed graph** using the **NetworkX** library. In this graph:
- Nodes represent cities
- Directed edges represent bus routes between cities
- Edge attributes represent individual trips (from city A to city B)

## Key Metrics and Visualizations

### Degree Centrality
We computed the **degree centrality** for each city in the network. Degree centrality measures how well-connected a city is by counting the number of direct connections (inbound and outbound) to/from other cities. Cities with the highest degree centrality are considered the most influential in terms of connectivity.

- **Top 50 Cities by Degree Centrality**:  
  The top 50 cities with the highest degree centrality were selected and visualized in a **bar chart**. The following chart displays the **degree centrality scores** for the top cities:

  ![Top 50 Cities by Degree Centrality](results/Top%2050%20Cities%20by%20Degree%20Centrality.png)

### Betweenness Centrality
Next, we calculated the **betweenness centrality** for each city. Betweenness centrality measures how often a city lies on the shortest path between two other cities, indicating the city's role as an intermediary in the network.

- **Top 50 Cities by Betweenness Centrality**:  
  The cities with the highest betweenness centrality were visualized in a **bar chart**. The following chart represents the **betweenness scores** for the most central cities:

  ![Top 50 Cities by Betweenness Centrality](results/Top%2050%20Cities%20by%20Betweenness%20Centrality.png)

### Bidirectional Routes
In this part of the analysis, we identified **bidirectional routes** — trips where a route exists from city A to city B and also from city B to city A. These routes were identified and listed as pairs of cities.

- **Bidirectional Routes**:
  The output was a list of bidirectional routes found in the dataset. For example:

  ```
  Bidirectional routes found: 9256
  Copenhagen ↔ Hamburg
  Brussels ↔ Timișoara
  Antwerp ↔ Utrecht
  Berlin ↔ Moss
  Marburg ↔ Munich
  ...
  ```

### Shortest Paths from Berlin
For **shortest path calculations**, we used **Dijkstra's algorithm** to calculate the shortest paths from **Berlin** to all other cities. The shortest path indicates the most efficient route between two cities, with the least number of edges.

- **Shortest Paths from Berlin**:
  The output showed the shortest paths to each city from Berlin, such as:

  ```
  Shortest paths from Berlin:
  To Podgorica: Berlin → Sofia → Podgorica
  To Durrës: Berlin → Kotor → Durrës
  To Budva: Berlin → Sofia → Budva
  To Dubrovnik: Berlin → Vienna → Dubrovnik
  To Kotor: Berlin → Kotor
  ...
  ```

## Country Connections Analysis
We analyzed the **connections between countries**, counting how many bus routes existed between each pair of countries. The **top 3 most connected origin countries** were selected and visualized.

- **Top 3 Most Connected Origin Countries**:
  A **bar chart** visualized the number of routes from the top 3 origin countries to their destination countries. The following chart presents the **number of routes** for each origin country and its destinations:

  ![Top 3 Most Connected Origin Countries](results/Top%203%20Most%20Connected%20Origin%20Countries.png)

## Graphs and Outputs
In addition to the analyses mentioned above, several graphs were plotted to help visualize the structure of the network:
1. **Top 20 Most Connected Cities**: A **network graph** showing the top 20 cities by degree centrality.
   ![Top 20 Most Connected Cities](results/Top%2020%20Most%20Connected%20Cities%20in%20the%20Bus%20Network.png)

2. **Shortest and Alternative Paths from Paris**: A **network graph** visualizing the shortest and alternative paths from Paris, with **shortest path edges** highlighted in **red** and **alternative paths** shown in **gray**.
   ![Shortest and Alternative Paths from Paris](results/Paris's%20Top%2014%20Destinations-%20Shortest%20Paths%20(Red)%20&%20Other%20Paths%20(Gray).png)
   
3. **In-Degree vs Out-Degree**: A **stacked bar chart** comparing the in-degree and out-degree of cities, showing the number of incoming and outgoing connections for each city.
   ![In-Degree vs Out-Degree](results/Top%2050%20Cities-%20In-Degree%20vs%20Out-Degree%20(Stacked).png)

## Conclusion
The project provides valuable insights into the structure of the **FlixBus European 2024 network**:
- **Key cities** such as Berlin and Peris play a central role in the network.
- **Bidirectional routes** and **strongly connected components** show how cities are interlinked.
- Understanding the **shortest paths** between cities can help optimize bus routes.
