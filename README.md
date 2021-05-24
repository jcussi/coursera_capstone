# coursera_capstone
Capstone for Data Science course


# Introduction: Business problem
Our client wishes to implement a restaurant in the state of New York, in order to determine the appropriate location that can guarantee the success of the business, our client considers the following aspects important: First, that the candidate cities must have a considerable population density ; second, to guarantee the influx of the public (customers) to have options for appropriate restaurant categories and finally to determine if there is competition in the market, taking into account those options that do not generate much competition.

## Objetive:
Recommend the appropriate location to create a new restaurant in the New York state, in order to guarantee the success of the business.

## Considerations:
Cities with the highest population density in the state of New York, in order to guarantee the influx of the public.
In a radius of 500 meters, consider up to 100 restaurants within the cities of New York State.
Determine the top 10 of the most common restaurants, in order to identify the categories that do not have much competition in the market.


# Data
Source: https://simplemaps.com/data/us-zips

Data: US Zip Codes Database 

Fields:

fieldname 	    description
-----------------------------------------------------------------------------------------------------------------
zip 	        The 5-digit zip code assigned by the U.S. Postal Service. 			
lat 	        The latitude of the zip code (learn more). 			
lng 	        The longitude of the zip code (learn more). 			
city 	        The official USPS city name. 			
state_id 	    The official USPS state abbreviation. 			
state_name 	    The state's name. 			
zcta 	        TRUE if the zip code is a Zip Code Tabulation area (learn more). 			
parent_zcta     The ZCTA that contains this zip code. Only exists if zcta is FALSE. Useful for making inferences about a zip codes that is a point from the ZCTA that contains it. 			
population 	    An estimate of the zip code's population. Only exists if zcta is TRUE. 			
density 	    The estimated population per square kilometer. Only exists if zcta is TRUE. 			
county_fips 	The zip's primary county in the FIPS format. 			
county_name 	The name of the county_fips. 			
county_weights 	A JSON dictionary listing all county_fips and their weights (by population) associated with the zip code. 			
imprecise 	    TRUE if the lat/lng has been geolocated using the city (rare). 			
military 	    TRUE if the zip code is used by the US Military (lat/lng not available). 			
timezone 	    The city's time zone in the tz database format. (e.g. America/Los_Angeles)

## Another sources
https://www.scikit-yb.org/en/latest/api/cluster/elbow.html
https://www.linkedin.com/pulse/applied-data-science-capstone-project-restaurant-wagner-mba
https://towardsdatascience.com/strategic-location-for-establishing-an-asian-restaurant-c3aecf2496b1
https://magnet.xataka.com/en-diez-minutos/verdad-densidad-poblacion-no-importa-total-sino-densidad-habitada-1


# Methodology:
[ES]
Después de contar con la data "US Zip Codes Database", y después de haber tomado en cuenta el estado "New York" hasta este punto ya tenemos procesado: 
* Las primeras 200 ciudades con mayor densidad poblacional con el objetivo de determinar la location recomendada para aperturar el restaurante.
Ahora procederemos con otras actividades como: 
* Obtener información a partir de la API de Forsquare para obtener hasta 100 restaurantes existentes en un radio de 500 metros.
* Para contribuir al análisis clasificar por categoría los restaurantes para determinar la frecuencia por ciudad.
* Determinar las 10 ciudades con mayor densidad poblacional, con la finalidad de posteriormente seleccionar a la ciudades que esten dentro del top 10.
* Nos centraremos en las áreas más prometedoras y dentro de ellas crearemos grupos de ubicaciones enfocados a la recomendación del mejor lugar donde implementar un restaurante: Después de obtener hasta los 100 restaurantes en un radio de 500 metros, posteriormente presentaremos un mapa de todas esas ubicaciones.
* Determinar el top 10 de las categorías de restaurantes por cada ciudad y localidad.
* Se procedará con el cluster aplicando  agrupación de k-means de esas ubicaciones para identificar la localidad, para la explotación de la ubicación óptima donde recomendaremos la implementación de un restaurante.
* Para recomendar se debe restringir el resultado de k-means a las ciudades de mayor densidad poblacional.

[EN]
After having the data "US Zip Codes Database", and after having taken into account the state "New York" up to this point we have already processed:
* The first 200 cities with the highest population density in order to determine the recommended location to open the restaurant.
Now we will proceed with other activities such as:
* Obtain information from the Forsquare API to obtain up to 100 existing restaurants within a radius of 500 meters.
* To contribute to the analysis, classify restaurants by category to determine frequency by city.
* Determine the 10 cities with the highest population density, in order to subsequently select the cities that are within the top 10.
* We will focus on the most promising areas and within them we will create groups of locations focused on recommending the best place to implement a restaurant: After obtaining up to 100 restaurants within a radius of 500 meters, we will later present a map of all those locations .
* Determine the top 10 restaurant categories for each city and town.
* We will proceed with the cluster applying k-means grouping of those locations to identify the locality, for the exploitation of the optimal location where we will recommend the implementation of a restaurant.
* To recommend, the k-means result should be restricted to the cities with the highest population density.


# Results and Discussion

[ES]
Para todos los resultados de K-means se ha restringido con las ciudades con mayor densidad, acotando así lo más posible la probabilidades de localidades donde es conveniente recomendar para la apertura del restaurante, además de recomendar las categorías convenientes. A continuación se describe los resultados por cluster.

Cluster 1: 
En el resultado del cluster, se ha restringido con las 10 ciudades con mayor densidad población del cual se refleja a las ciudades "Flushing" y "Jamaica" con frecuencia de 96 y 90 respectivamente. 
Posteriormente se puede apreciar el resultado estadístico donde el "top" (datos mas comunes) resultan ser la ciudad "Flushing" y la localidad "Dunkin'".
Del anterior resultado también contamos con los 10 categorias de restaurantes mas comunes, de los cuales se toma en cuenta a los 3 últimos para mitigar la competencia, pero a la vez velando que este dentro del top 10; como resultado se tiene a 8th-"Asian Restaurant", 9th-"Donut Shop" y 10th-"Fried Chicken Joint".

Cluster 2: 
En el resultado del cluster, se ha restringido con las 10 ciudades con mayor densidad población del cual no existe ciudades que esten dentro de las 10 ciudad con mayor densidad, por el cual no se tiene resultados para recomendar.

Cluster 3: 
En el resultado del cluster, se ha restringido con las 10 ciudades con mayor densidad población del cual se refleja a las ciudades "New York", "Brooklyn", "Bronx", "Astoria", "Long Island City", "Jackson Heights", "Staten Island" y "Ozone Park" con frecuencias de 3296, 1292, 412, 151, 91, 71, 55, 39 respectivamente. 
Posteriormente se puede apreciar el resultado estadístico donde el "top" (datos mas comunes) resultan ser la ciudad "New York" y la localidad "Dunkin'".
Del anterior resultado también contamos con los 10 categorias de restaurantes mas comunes, de los cuales se toma en cuenta a los 3 últimos para mitigar la competencia, pero a la vez velando que este dentro del top 10; como resultado se tiene a 8th-"Bakery", 9th-"Chinese Restaurant" y 10th-"Sandwich Place".

Cluster 4: 
En el resultado del cluster, se ha restringido con las 10 ciudades con mayor densidad población del cual no existe ciudades que esten dentro de las 10 ciudad con mayor densidad, por el cual no se tiene resultados para recomendar.


[EN]
For all the K-means results, it has been restricted to the cities with the highest density, thus limiting as much as possible the probabilities of locations where it is convenient to recommend for the opening of the restaurant, in addition to recommending the appropriate categories. The results by cluster are described below.

Cluster 1:
In the result of the cluster, it has been restricted to the 10 cities with the highest population density, which is reflected to the cities "Flushing" and "Jamaica" with a frequency of 96 and 90 respectively.
Later you can see the statistical result where the "top" (most common data) turn out to be the city "Flushing" and the locality "Dunkin '".
From the previous result we also have the 10 most common restaurant categories, of which the last 3 are taken into account to mitigate the competition, but at the same time ensuring that it is within the top 10; as a result there are 8th- "Asian Restaurant", 9th- "Donut Shop" and 10th- "Fried Chicken Joint".

Cluster 2:
In the result of the cluster, it has been restricted to the 10 cities with the highest population density, of which there are no cities that are within the 10 cities with the highest density, for which there are no results to recommend.

Cluster 3:
In the result of the cluster, it has been restricted to the 10 cities with the highest population density, which is reflected to the cities "New York", "Brooklyn", "Bronx", "Astoria", "Long Island City", "Jackson Heights "," Staten Island "and" Ozone Park "with frequencies of 3296, 1292, 412, 151, 91, 71, 55, 39 respectively.
Later you can see the statistical result where the "top" (most common data) turn out to be the city "New York" and the locality "Dunkin '".
From the previous result we also have the 10 most common restaurant categories, of which the last 3 are taken into account to mitigate the competition, but at the same time ensuring that it is within the top 10; as a result we have 8th- "Bakery", 9th- "Chinese Restaurant" and 10th- "Sandwich Place".

Cluster 4:
In the result of the cluster, it has been restricted to the 10 cities with the highest population density, of which there are no cities that are within the 10 cities with the highest density, for which there are no results to recommend.
