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

As a team of four, our approach to this was to split and work on different solutions, to explore possibilities.

Some ideas that came to mind are:
- Make a neural network,
- Use linear programming,
- Find a simple algorithm to benchmark the others.
