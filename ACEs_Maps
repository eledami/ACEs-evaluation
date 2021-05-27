# Maps

# Packages 

install.packages(c("rgdal","rgeos","tmap"))
library(rgdal)
library(rgeos)
library(tmap)

# data

nb_data <- read.csv("BST_data.csv")
View(nb_data)

nb_shapefiles <-readOGR(".", "BST_13_NHOODS")

nb_shapefiles_2 <-spTransform(nb_shapefiles, CRS("+init=EPSG:27700"))

qtm(nb_shapefiles_2)

# merge data to shapefiles

nb_map <- merge(nb_shapefiles_2, nb_data, by.x="BST_Team", by.y="BST_name")

# create maps

tm_shape(nb_map) +
  tm_fill("p_organisations", palette="Oranges", title="% organisations") +
  tm_scale_bar(position = c("right", "top")) +
  tm_borders(alpha=0.5, col="white") +
  tm_compass(position = c("right", "top")) +
  tm_legend(legend.position = c("left", "top")) +
  tm_credits("Data: ACEs survey & BST neighbourhoods shapefiles, 
             PRI, Research Intelligence and Data Science, 2021, 
             Manchester City Council, 
             Crown copyright and database rights 2021,
             Ordnance Survey 1000019568", align = "right", size=0.7, 
             position=c("right", "bottom")) +
  tm_text("BST_Team", size = 0.64, col = "black", shadow = TRUE)

tm_shape(nb_map) +
  tm_fill("p_people_trained", palette="Blues",
          title="% people trained") +
  tm_scale_bar(position = c("right", "top")) +
  tm_borders(alpha=0.5, col="white") +
  tm_compass(position = c("right", "top")) +
  tm_legend(legend.position = c("left", "top")) +
  tm_credits("Data: ACEs survey & BST neighbourhoods shapefiles, 
             PRI, Research Intelligence and Data Science, 2021, 
             Manchester City Council, 
             Crown copyright and database rights 2021,
             Ordnance Survey 1000019568", align = "right", size=0.7, 
             position=c("right", "bottom")) +
  tm_text("BST_Team", size = 0.64, col = "black", shadow = TRUE)

# add the p_organisations in relation to mean 'connections' 

organisations_points <- read.csv("Organisations_connections_5.csv")

organisations_points_mappable <- SpatialPointsDataFrame(organisations_points[,1:2], 
                                                        organisations_points, 
                                                        proj4string = CRS("+init=EPSG:27700"))
tm_shape(nb_map) +
  tm_scale_bar(position = c("right", "top")) +
  tm_borders(alpha=1, col="bisque4") +
  tm_compass(position = c("right", "top")) +
  tm_legend(legend.position = c("left", "top")) +
  tm_shape(organisations_points_mappable) +
  tm_dots(col="connection_level", size=0.7, palette="BuPu",
          style="quantile") +
  tm_credits("Data: ACEs survey & BST neighbourhoods shapefiles, 
             PRI, Research Intelligence and Data Science, 2021, 
             Manchester City Council, 
             Crown copyright and database rights 2021,
             Ordnance Survey 1000019568", align = "right", size=0.7, 
             position=c("right", "bottom"))


# add the p_organisations in relation to mean 'connections' 

organisations_points_3 <- read.csv("Organisations_connections_3.csv")

organisations_points_mappable_3 <- SpatialPointsDataFrame(organisations_points[,1:2], 
                                                        organisations_points, 
                                                        proj4string = CRS("+init=EPSG:27700"))
tm_shape(nb_map) +
  tm_scale_bar(position = c("right", "top")) +
  tm_borders(alpha=1, col="bisque4") +
  tm_compass(position = c("right", "top")) +
  tm_legend(legend.position = c("left", "top")) +
  tm_shape(organisations_points_mappable_3) +
  tm_dots(col="connection", size=0.7, palette="BuPu",
          style="quantile") +
  tm_credits("Data: ACEs survey & BST neighbourhoods shapefiles, 
             PRI, Research Intelligence and Data Science, 2021, 
             Manchester City Council, 
             Crown copyright and database rights 2021,
             Ordnance Survey 1000019568", align = "right", size=0.7, 
             position=c("right", "bottom"))






