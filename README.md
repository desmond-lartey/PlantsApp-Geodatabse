<!DOCTYPE html>
<html>

<body>

<div style="display: flex; justify-content: space-between;">
    <img src="https://agro-nl.nl/wp-content/uploads/2019/04/trees-bareroot-e1557303577410.jpg" alt="Image 1" style="width: 24%; margin-right: 1%;">
    <img src="https://agro-nl.nl/wp-content/uploads/2019/04/shrubs-p9-min-e1557303401583.jpg" alt="Image 2" style="width: 24%; margin-right: 1%;">
    <img src="https://agro-nl.nl/wp-content/uploads/2019/04/shrubs-full-ground-min-e1557303444131.jpg" alt="Image 3" style="width: 24%; margin-right: 1%;">
    <img src="https://agro-nl.nl/wp-content/uploads/2019/04/trees-open-ground-e1557303524105.jpg" alt="Image 4" style="width: 24%;">
</div>

<h1>Documentation</h1>

<h2>Overview:</h2>
    <p>The provided SQL queries aim to analyze various aspects of climate, adaptation strategies, budgeting, and dominant species across different countries. The database contains multiple tables, each capturing specific details about climate trends, vulnerabilities, budgeting for adaptation, and more. The following documentation provides an in-depth understanding of the relationships between these tables and the rationale behind joining certain tables to answer specific questions.</p>

<h2>1. Tables and Relationship:</h2>
        <li><strong>budget:</strong> Contains data about countries, their climate vulnerabilities, urban greening initiatives, and estimated budgets for adaptation.</li>
        <li><strong>adaptation:</strong> Holds information about countries, their climate vulnerabilities, adaptation strategies, and recommended ornamental plant species.</li>
        <li><strong>climate:</strong> Captures the current climate state and trend for different countries.</li>
        <li><strong>climateclassification:</strong> Classifies countries based on winter hardiness zones, temperature, and suitable plant species.</li>
        <li><strong>climateprojections:</strong> Provides projections for climate changes in countries over various time frames.</li>
        <li><strong>climatezone:</strong> Specifies the climate zone for each country.</li>
        <li><strong>vulnerabilities:</strong> Lists future vulnerabilities and recommended plant species for each country.</li>
        <li><strong>dominantspecies2:</strong> Contains polygon data indicating dominant species available in countries from a specific research.</li>
        <li><strong>world:</strong> Contains polygon data for countries.</li>

<h2>Analysis:</h2>

<h3>1. Budget Analysis:</h3>
    <p><strong>Objective:</strong> Determine countries with the highest and lowest estimated budgets for adaptation and identify the main climate vulnerabilities for countries with the top 5 highest budgets.</p>
     <p><strong>Objective:</strong> The budget table is self-sufficient for this analysis.</p>

<h4>a. Highest and Lowest Estimated Budgets:</h4>
    <li><strong></strong>The budget table is queried to determine countries with the highest and lowest estimated budgets for adaptation. </li>
    <li><strong></strong>The ORDER BY clause sorts the results based on the Estimated_Budget column in descending and ascending order, respectively. </li>

<h4>b. Main Climate Vulnerabilities for Top 5 Budgets:</h4>
    <li>Budget<strong></strong>The budget table is again used to list the main climate vulnerabilities for countries with the top 5 highest estimated budgets.</li>

<h3>2. Adaptation Strategies:</h3>
    <p><strong>Objective:</strong> Identify the most commonly recommended plant species across countries and the adaptation strategies for countries with specific vulnerabilities.</p>
    <p><strong>Relationships:</strong> The adaptation table is used for this analysis. Multiple columns within the table are aggregated to determine the most common plant species.</p>

<h4>a. Most Commonly Recommended Plant Species:</h4>
    <p><strong>Adaptation:</strong>The adaptation table is queried to determine the most commonly recommended plant species across countries.</p>
    <p><strong>Relationships:</strong>The GROUP BY clause groups the results by the OrnamentalPlantSpecies column, and the ORDER BY clause sorts the results based on the count of countries recommending each species.</p>

<h4>b. Adaptation Strategies for Specific Vulnerabilities:</h4>
    <p><strong>AAdaptation:</strong>The adaptation table is queried to list countries with specific vulnerabilities (e.g., "Water scarcity") and their associated adaptation strategies.</p>

<h3>3. Climate Trends:</h3>
    <p><strong>Objective:</strong> Count countries experiencing warming vs. cooling trends and identify countries with the most severe climate states.</p>
    <p><strong>Relationships:</strong> The climate table is used to determine climate trends and states for different countries.</p>

<h4>a. Warming vs. Cooling Trends:</h4>
<ul>
    <li>
        <strong>Climate:</strong> The climate table is queried to count the number of countries experiencing warming and cooling trends.
    </li>
    <li>
        <strong>Clause:</strong> The WHERE clause filters the results based on the presence of the words "Warming" and "Cooling" in the Climate Trend column.
    </li>
</ul>

<h4>b. Countries with Severe Climate States:</h4>
<ul>
    <li>
        The climate table is used to list countries with severe climate states, specifically those with the word "rainfall" in the Current Climate State column.
    </li>
</ul>

<h3>5. Climate Projections</h3>
<ul>
    <li>
        <strong>Objective:</strong> Identify countries projected to experience the most drastic changes in the next 30 years and analyze trends in 5-year, 10-year, and 30-year projections.
    </li>
    <li>
        <strong>Relationships:</strong> The climateprojections table provides projections for future climate changes in countries.
    </li>
    <li>
        <strong>Countries with Drastic Changes in Next 30 Years:</strong> The climateprojections table is queried to identify countries projected to experience drastic changes in the next 30 years.
    </li>
    <li>
        <strong>Trends in Projections:</strong> The climateprojections table is used to analyze trends in the 5-year, 10-year, and 30-year projections.
    </li>
</ul>


<h3>6. Dominant Species Analysis</h3>
    <p><b>Objective:</b> Determine the dominant species in each country and the area they occupy.</p>
    <p><b>Relationships:</b> A spatial join is performed between the world and dominantspecies2 tables to determine the dominant species in each country.</p>

<h3>7. Vulnerabilities</h3>
    <p><b>Objective:</b> Identify countries projected to have significant future vulnerabilities and the recommended plant species for countries with high-risk vulnerabilities.</p>
    <li><strong></strong><b>Relationships:</b> The vulnerabilities table provides insights into future vulnerabilities and recommended plant species for different countries.</li>
    <li><strong></strong><b>Vulnerabilities:</b> The vulnerabilities table is queried to identify countries projected to have significant future vulnerabilities.</li>
    <li><strong></strong><b>Vulnerabilities:</b> The vulnerabilities table is used to determine the recommended plant species for countries with high-risk future vulnerabilities.</li>

<h2>Rationale for Joins:</h2>
    <p>The spatial join between the world and dominantspecies2 tables is crucial to determine the dominant species in each country and the area they occupy. This join helps in understanding the distribution of species across countries.</p>
    <p>Other queries primarily use individual tables without joins, as the tables are structured to provide comprehensive data for specific analyses.</p>

<h2>Relationships:</h2>
<li><strong>Key:</strong> The primary key for linking most tables is the Country column. This column is present in almost all tables, making it the primary attribute for joining tables.</li>
        <li><strong>Relation:</strong> The spatial relationship between the world and dominantspecies2 tables is based on the geometry of countries and the distribution of dominant species.</li>


<p>In essence, the SQL scripts are designed to extract specific insights from the database by querying individual tables or joining multiple tables based on the Country attribute or spatial relationships. The queries are tailored to answer specific information requests related to climate trends, adaptation strategies, budgeting, and dominant species distribution across countries.</p>

<h2>Conclusion:</h2>
    <p>The database provides a holistic view of climate trends, vulnerabilities, adaptation strategies, and budgeting across countries. By analyzing this data, stakeholders can make informed decisions about climate adaptation, budget allocation, and strategies to combat future vulnerabilities. The relationships between tables, especially the spatial relationship, offer a deeper understanding of the distribution of species and the impact of climate on various countries. <a href="https://interactive-web-mapping.streamlit.app/">VISIT THE GEODATABASE APP HERE</a></p>

<p>If you want to know more about the functional and ornamental qualities for over 3000 plant species, <a href="https://select-plant-guide.streamlit.app/">VISIT PLANTAPP HERE</a>.</p>
</body>

</html>
