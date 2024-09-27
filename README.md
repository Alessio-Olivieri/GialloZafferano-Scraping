# What are the most loved reciped by italians?

## Overview

This project is developed as part of the **Applied Computer Science and Artificial Intelligence** course for the **2023/2024** academic year, specifically for the **Database 2** course. The focus of the project is on **web scraping, data extraction, and network analysis**. By scraping data from the Giallo Zafferano website, the project builds a comprehensive dataset of recipes and their attributes, which is then used to explore relationships between recipes and ingredients using graph-based techniques.

The project demonstrates how **graph theory** and **network analysis** can be applied to analyze and visualize large datasets, such as recipes, by treating them as interconnected entities. This approach is highly relevant in fields like **data mining**, **database management**, and **artificial intelligence**, where understanding the underlying structure of data is essential for extracting meaningful insights.

## notebook.qmd

This Quarto document demonstrates a comprehensive pipeline for scraping recipes from the Giallo Zafferano website, processing the data, and analyzing ingredient similarities using network analysis techniques. The document is structured into multiple sections, each focusing on a specific aspect of the process, from data extraction to advanced graph analysis.

### Key Steps and Functions

1. **Scraping Recipes:**
   - The `get_recipes` function scrapes recipe names and their links from the Giallo Zafferano website.
   - The `get_data` function scrapes detailed information for each recipe, including ingredients, rating, description, tags, steps, and images.
   - The `scrape_all_pages` function iterates through all the available pages on the website to collect the entire dataset of recipes.

2. **Data Cleaning and Transformation:**
   - The `clean_string` function cleans the extracted ingredient quantities by removing unnecessary text and normalizing units.
   - The scraped data is structured into a DataFrame that contains key recipe details such as name, ingredients, rating, description, steps, and other metadata.

3. **Recipe Similarity Network:**
   - Recipes are treated as nodes, and edges between nodes represent shared ingredients. The similarity is quantified by the number of common ingredients between recipes.
   - The adjacency matrix is constructed using the `create_graph` function, and a graph is plotted where each node is a recipe and edges represent shared ingredients.
   - This section includes various visualizations using `igraph` to depict how recipes are connected based on ingredient similarity.

4. **Ingredients Similarity Network:**
   - Ingredients are treated as nodes, and edges between them represent recipes that contain both ingredients. This approach reveals how commonly certain ingredients co-occur across different recipes.
   - A similar process as the recipe similarity graph is applied here to construct the network.

5. **Advanced Analysis:**
   - **Edge Rating:** Calculates an average rating for edges (ingredient pairs) based on the ratings of the recipes that connect them. This can help identify which ingredient combinations are associated with highly-rated recipes.
   - **Special Ingredients:** An analysis to identify ingredients that appear more frequently in 5-star recipes vs. lower-rated recipes. The vertices connected by high-rated recipes are plotted separately from those connected by low-rated recipes.
   
6. **Network Statistics:**
   - **Degree Centrality:** Measures how connected each ingredient or recipe is within the network. The more connections (shared recipes or ingredients), the higher the centrality.
   - **Betweenness Centrality:** Identifies which ingredients act as bridges between other ingredients in the network, making them more critical in recipe diversity.

### Graph Visualizations
- Different types of graphs are used to represent recipe and ingredient similarity. Custom color schemes and edge weights are applied to visually emphasize key relationships.
- The graphs are plotted using various `igraph` layouts, such as Fruchterman-Reingold, with nodes representing recipes or ingredients and edges showing shared connections.

### Important Functions and Code Snippets:
- **`find_image`:** Extracts images of recipes if available.
- **`generate_colors`:** Generates random colors for nodes in the graph.
- **`cool_hist`:** A helper function that generates histograms to represent various network statistics such as degree centrality and betweenness centrality.

### Libraries Used:
- `tidyverse` for data manipulation.
- `rvest` for web scraping.
- `httr` for HTTP requests.
- `igraph` for network creation and visualization.
- `ggplot2` and `ggrepel` for visualizations and histograms.

## How to Use
1. **Scraping Data:**
   - Uncomment the scraping code block (`scrape_all_pages()`) to collect data directly from the Giallo Zafferano website. Ensure you are connected to the internet and have all the required R packages installed.
   
2. **Loading Pre-Scraped Data:**
   - If the scraping process is not required, you can load pre-scraped data (`pages`) to skip the web scraping step and proceed with analysis.

3. **Running the Analysis:**
   - Execute each code block in sequence. The document is designed to build upon previous sections, and the final output will be visualizations and network statistics based on the scraped data.

4. **Visualizing Networks:**
   - Once the graphs are created, adjust layout and visualization parameters as needed. The `plot()` function generates the graphs with options for customizing node size, edge labels, and colors.

5. **Statistical Insights:**
   - Run the network statistics blocks to gain insights into which ingredients are most common, serve as bridges between recipes, or are associated with highly-rated dishes.

## Customization
- **Filtering Ingredients:** You can customize which ingredients to exclude from the network (e.g., common items like salt or water) by modifying the `ingredients_NOSA` list.
- **Graph Parameters:** Change the color schemes, layout options, and edge width scaling factors to better suit your needs.

### Requirements:
- R version >= 4.0
- The following R packages:
  - `tidyverse`
  - `rvest`
  - `httr`
  - `igraph`
  - `ggplot2`
  - `ggrepel`

