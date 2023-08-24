<!DOCTYPE html>
<html>

<body>
    <img src="https://www.rfwireless-world.com/images/Geodatabase-life-cycle.jpg" alt="Cover Image">

    <h1>Comprehensive Documentation</h1>

    <h2>Overview:</h2>
    <p>The provided SQL queries aim to analyze various aspects of climate, adaptation strategies, budgeting, and dominant species across different countries. The database contains multiple tables, each capturing specific details about climate trends, vulnerabilities, budgeting for adaptation, and more. The following documentation provides an in-depth understanding of the relationships between these tables and the rationale behind joining certain tables to answer specific questions.</p>

    <h2>Tables and Relationships:</h2>
    <ol>
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
    <p><strong>Relationships:</strong> The budget table is self-sufficient for this analysis.</p>

    <h4>a. Highest and Lowest Estimated Budgets:</h4>
    <p>The budget table is queried to determine countries with the highest and lowest estimated budgets for adaptation.</p>
    <p>The ORDER BY clause sorts the results based on the Estimated_Budget column in descending and ascending order, respectively.</p>

    <h4>b. Main Climate Vulnerabilities for Top 5 Budgets:</h4>
    <p>The budget table is again used to list the main climate vulnerabilities for countries with the top 5 highest estimated budgets.</p>

<h3>2. Adaptation Strategies:</h3>
    <p><strong>Objective:</strong> Identify the most commonly recommended plant species across countries and the adaptation strategies for countries with specific vulnerabilities.</p>
    <p><strong>Relationships:</strong> The adaptation table is used for this analysis. Multiple columns within the table are aggregated to determine the most common plant species.</p>

    <h4>a. Most Commonly Recommended Plant Species:</h4>
    <p>The adaptation table is queried to determine the most commonly recommended plant species across countries.</p>
    <p>The GROUP BY clause groups the results by the OrnamentalPlantSpecies column, and the ORDER BY clause sorts the results based on the count of countries recommending each species.</p>

    <h4>b. Adaptation Strategies for Specific Vulnerabilities:</h4>
    <p>The adaptation table is queried to list countries with specific vulnerabilities (e.g., "Water scarcity") and their associated adaptation strategies.</p>

<h3>3. Climate Trends:</h3>
    <p><strong>Objective:</strong> Count countries experiencing warming vs. cooling trends and identify countries with the most severe climate states.</p>
    <p><strong>Relationships:</strong> The climate table is used to determine climate trends and states for different countries.</p>

<h4>a. Warming vs. Cooling Trends:</h4>
    <p>The climate table is queried to count the number of countries experiencing warming and cooling trends.</p>
    <p>The WHERE clause filters the results based on the presence of the words "Warming" and "Cooling" in the Climate Trend column.</p>

    <h4>b. Countries with Severe Climate States:</h4>
    <p>The climate table is used to list countries with severe climate states, specifically those with the word "rainfall" in the Current Climate State column.</p>

<h3>5. Climate Projections</h3>
    <p><b>Objective:</b> Identify countries projected to experience the most drastic changes in the next 30 years and analyze trends in 5-year, 10-year, and 30-year projections.</p>
    <p><b>Relationships:</b> The climateprojections table provides projections for future climate changes in countries.</p>
    
        <li><b>Countries with Drastic Changes in Next 30 Years:</b> The climateprojections table is queried to identify countries projected to experience drastic changes in the next 30 years.</li>
        <li><b>Trends in Projections:</b> The climateprojections table is used to analyze trends in the 5-year, 10-year, and 30-year projections.</li>

<h3>6. Dominant Species Analysis</h3>
    <p><b>Objective:</b> Determine the dominant species in each country and the area they occupy.</p>
    <p><b>Relationships:</b> A spatial join is performed between the world and dominantspecies2 tables to determine the dominant species in each country.</p>

<h3>7. Vulnerabilities</h3>
    <p><b>Objective:</b> Identify countries projected to have significant future vulnerabilities and the recommended plant species for countries with high-risk vulnerabilities.</p>
    <p><b>Relationships:</b> The vulnerabilities table provides insights into future vulnerabilities and recommended plant species for different countries.</p>
   
        <li><b>Countries with Significant Future Vulnerabilities:</b> The vulnerabilities table is queried to identify countries projected to have significant future vulnerabilities.</li>
        <li><b>Recommended Plant Species for High-Risk Vulnerabilities:</b> The vulnerabilities table is used to determine the recommended plant species for countries with high-risk future vulnerabilities.</li>

    <h2>Rationale for Joins:</h2>
    <p>The spatial join between the world and dominantspecies2 tables is crucial to determine the dominant species in each country and the area they occupy. This join helps in understanding the distribution of species across countries.</p>
    <p>Other queries primarily use individual tables without joins, as the tables are structured to provide comprehensive data for specific analyses.</p>

    <h2>Relationships:</h2>
    <p>The primary key for linking most tables is the Country column. This column is present in almost all tables, making it the primary attribute for joining tables.</p>
    <p>The spatial relationship between the world and dominantspecies2 tables is based on the geometry of countries and the distribution of dominant species.</p>

    <p>In essence, the SQL scripts are designed to extract specific insights from the database by querying individual tables or joining multiple tables based on the Country attribute or spatial relationships. The queries are tailored to answer specific information requests related to climate trends, adaptation strategies, budgeting, and dominant species distribution across countries.</p>

    <h2>Conclusion:</h2>
    <p>The database provides a holistic view of climate trends, vulnerabilities, adaptation strategies, and budgeting across countries. By analyzing this data, stakeholders can make informed decisions about climate adaptation, budget allocation, and strategies to combat future vulnerabilities. The relationships between tables, especially the spatial relationship, offer a deeper understanding of the distribution of species and the impact of climate on various countries.</p>
</body>

</html>
