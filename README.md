# The AI Summit London - Hackathon

## Team MLGs 
- Abimbola Oluwagbuyi
- Oscar Sjöstedt
- Ran Cheng
- Thomas Walsh

## Questions 1 & 2
These two questions were fairly straightforward. We had a dataset with the number of tonnes of CO2 released by different agricultural products (meats, eggs, rice, etc.) in different regions of the world, and we needed to calculate the fraction of the EU GHG caused by agriculture. All all we had to do was to find a dataset with the total GHG emissions in the EU, which we found [here](https://www.eea.europa.eu/data-and-maps/daviz/total-ghg-emissions-1#tab-chart_1), courtesy of the European Environment Agency.

All we had left to do was to divide the agricultural emissions of each product by the total emissions to get that fraction, solving problem 2.

To solve problem 1 all we had left to do was to sum those percentages together, giving us around 7% of emissions caused by agriculture in 2016.

For all the code for these two exercices, refer to `emissions_agriculture.ipynb`.

## Question 3
This was the tough question of the hackathon: with all the data we had, we needed to find an optimal diet such that all daily nutritional goals are reached, all while emitting as little GHG as possible.

This is possible, thanks to the three data sets we had:
1. `Agriculture_Dataset_text.csv`, containing how much of each aliment is produced, and how much GHG it emits.
2. `ABBREV_2.csv`, containing the nutritional values of different aliments.
3. `daily_nutrients.xlsx`, with the nutrients needed per day.

To join all of this together, we have two mapping files:
1. `mapping.csv`, to map files (1) and (2), thus associating production and GHG emission to nutritional value.
2. `abbrev_nutrient_map.csv`, to map files (2) and (3), thus allowing us to know how much of each food must be eaten to reach our nutritional goal.

All of this together allows us to link pollution to nutrition.

As a team of four, our approach to this was to split and work on different solutions, to explore possibilities.

Some ideas that came to mind are:
- Make a neural network,
- Use linear programming,
- Use multi-objective optimization through Pyomo. The objective function is comprised of min GHG emission and max nutrition.
- Find a simple algorithm to benchmark the others:
    - We came up with a basic algorithm, that aims to maximise one nutrient at a time, until all nutrient goals are reached.
    - To do this, we first calculate:
        1. The emissions per quantity of food produced for each aliment,
        2. The nutrients per gram of food for each aliment,
        3. The emissions per nutrient for each aliment.
    - This gives us access to the best (least polluting) source of each nutriment.
    - We can then loop through every nutriment, and start creating a "menu":
        - For that nutriment, add as much of the "optimal food" as needed to fulfill the need for that nutriment.
        - Look for the next nutriment that is the most wanted.
        - Fill the menu again with the best aliment for that new nutriment.
        - Rinse and repeat!
    - This gives us 29 different menus, that we can then sort by CO2 emissions, to give us a "best" menu.
    - All the code can be found in `optimal_diet.ipynb`.
    - This approach could be greatly improved, by:
        - finding a better heuristic for the target, rather than "nutriment we need the most"
        - taking into account the other nutritional values of the food, asides from where it performs best. Maybe a type of food is not the best anywhere but gives the best overall nutrition.
        - simply using a more complex system, that allows for more optimal results! This was intended to be a basic algorithm to benchmark the others, and doesn't in any way provide a complete solution.
