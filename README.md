# black_bear_aware

This is the repository for the Black Bear Aware MESM 2023 Group Project. More information about the project can be found on the [Bren School Group Project Page](https://bren.ucsb.edu/projects/black-bear-aware-predicting-human-black-bear-conflict-likelihood-changing-climate). 

See here for an updated Dryad link shortly. 


Contents
=========

 * [Why?](#why)
 * [Limitations](#Limitations)
 * [Contributors](#contributors)
 * [Repository Directory](#repository-directory)
 * [File Directory](#file-directory)
 

### Why?
The purpose of this code was to develop a reproducible model that can be used to predict human-black bear conflict across California. Users can explore the code we used to wrangle our input data for use in our model, and the code we used to develop and run our model. Additionally, our model .rds files are saved in this repository, which users can access directly. Model visualization is possible using our data_vis.Rmd.


### Limitations
Spatial records of human-black bear conflicts across California were supplied to the Black Bear Aware team by the California Department of Fish and Wildlife. Due to privacy concerns, this data cannot be shared publicly. Users of this repository will require spatial conflict data if they wish to recreate our model. Our model can be visualized without spatial conflict data but requires properly configured environmental data. Please reach out to the contributors below with questions. 

 
### Contributors
**Claire Meuter: Data Manager**

University of California, Santa Barbara

clairemeuter@bren.ucsb.edu

**Mia Guarnieri: Project Manager**

University of California, Santa Barbara

mguarnieri@bren.ucsb.edu

**Samantha Rozal: Finance Manager and Outreach Coordinator**

University of California, Santa Barbara

srozal@bren.ucsb.edu 

**Chase Tarr: Communications Manager**

University of California, Santa Barbara

chasetarr@ucsb.edu

### Repository Directory  
Our repository is organised into four folders: analysis, data_vis_files, data_wrangling, and models. 

+ analysis
This folder contains the code we used to further analyze our model outputs. 

+ data_vis_files
Contains the code used to make data visualizations for this project, including hotspot maps, a table of model coefficients, figures displaying transformed coefficients and their confidence intervals, and a marginal effects plot for one specified coefficient.

+ data_wrangling
This folder contains the code we used to standardize our spatial data for use in our model. 

+ models 
This folder contains code we used to generate our models, as well as our .rds models that are available for use. 

### File Directory 
**Folder: analysis**

+ collinearity_tests.Rmd: Code used to test for collinearity between variables.

+ demographic_exploration.Rmd: Instructions and code used for a comparative statistical analysis of the demographics between regions of high conflict, no reporting and high conflict, reporting. The demographics tested include racial/ethnic identity, social vulnerability index, and english proficiency.

+ high_conflict_area_calculations.Rmd: instructions and code for calculating the area of high conflict (modeled conflict risk ≥ 0.7) within modeled conflict rasters.

+ public_private_high_conflict_areas.Rmd: Code to explore the relationship between ownership of land and locations of high likelihood of human-black bear conflict in across California. 

+ zonal_stats_county.Rmd: Code used to find the average conflict risk by county, metropolitan statistical area, and cdfw region. 

**Folder: data_vis_files**

+ data_vis.Rmd: contains the code used to make data visualizations for this project, including hotspot maps, a table of model coefficients, figures displaying transformed coefficients and their confidence intervals, and a marginal effects plot for one specified coefficient.

**Folder: Data_wrangling**

+ distance_rasters : Code used to wrangle and create distance layers for 5 variables: Distance to streams, distance to roads, distance to urban areas, distance to recreational areas, and distance to forest cover. 

+ Drought_Projections: Code used to wrangle precipitation and evapotranspiration values and input them into the Palmer Drought Severity Index function to get pdsi values by year and location. 

+ Drought_agg : Code used to create rasters containing annual mean Palmer Drought Severity Index (PDSI) values from 2016 to 2021, calculated from weekly data taken from US Drought Monitor. 

+ Fire_projection_wrangling : Code used to wrangle and create distance layers for distance to fire for fire projections spanning from 2024 to 2029. 

+ Fire_wrangling: Code used to wrangle and create distance layers for distance to fire for fire records spanning from 2011 to 2020. Raster layers created from this .rmd include: Distance to moderate to severe burn scars from 2015,2016, 2017, 2018, 2019, 2020 and distance to moderate to severe burn scars from 2011 to 2012, 2012 to 2013, 2013 to 2014, 2014 to 2015, 2015 to 2016, 2016 to 2017, 2017 to 2018, and 2018 to 2019
 

+ Forest_cover_wrangling: Code used to wrangle foret cover layers. 

+ Human_pop_wrangling: Code used to wrangle human population density layers into formatting acceptable for use in our model. Raster layers created from this .rmd include: human population density 2016, 2017, 2018, 2019, 2020, and 2021

+ Nlcd_wrangling: Contains instructions and code for wrangling land cover data (specifically from the USGS NLCD database) to feed into the RSPF model. This involves reclassifying, reprojecting, and cropping the data to the extent of California.

+ Other_data_wrangling: Code to wrangle elevation data, road data, create aspect and terrain, and drought raster layers. 

**Folder: Models**

+ Candidate_models: This folder contains files for our candidate base and climate models, which were evaluated using AIC and a series of robustness checks before our final model was selected. Models containing “climate” in the name include our climate variables (drought and fire). All other models do not include drought and fire covariates. basemodel_allyears.rds contains all evaluated environmental variables (but no climate variables). climate_model_allyears.rds contains all evaluated environmental and climate variables. Variables included in each model are listed below.
    + basemodel_allyears.rds: elevation + aspect + terrain ruggedness + population density + land cover + road density + distance to roads + distance to streams + distance to urban areas + distance to recreational areas + distance to forests + forest density
      
    + climate_model_allyears.rds: elevation + aspect + terrain ruggedness + population density + land cover + road density + distance to roads + distance to streams + distance to urban areas + distance to recreational areas + distance to forests + forest density + distance to fires 1 year ago + distance to fires 2-3 years ago + distance to fires 4-5 years ago + drought
    + mod1.rds: elevation + land cover + distance to forests + population density + distance to recreational areas + road density + distance to urban areas
    + mod2.rds: elevation + forest density + land cover + distance to forests + population density + distance to recreational areas + road density + distance to urban areas
    + mod3.rds: elevation + land cover + distance to forests + population density + distance to recreational areas + distance to streams + terrain ruggedness + distance to urban areas
    + mod3climate.rds: elevation + land cover + distance to forests + population density + distance to recreational areas + distance to streams + terrain ruggedness + distance to urban areas + distance to fires 1 year ago + distance to fires 2-3 years ago + distance to fires 4-5 years ago + drought
    + mod4.rds: elevation + forest density + land cover + distance to forests + population density + distance to recreational areas + distance to streams + distance to urban areas
    + mod5.rds: elevation + land cover + distance to forests + population density + distance to streams + terrain ruggedness + distance to urban areas

+ Model_code: This folder contains the code for our base models (models without climate variables) and code for our climate models. Data was processed by year, data frames were generated for each year by conflict points and randomly generated non-conflict points, and then recombined into one final data frame. The final model was then run utilizing this final data frame that combined all years. We ran a final climate model that had the best AIC and where we squared population density and road density. Most of our analysis data was created from these rasters. 

+ sq_mod3climate.rds: This is an r data object which contains our final, best-fit model. Code for creating this model can be found in the model_code folder, within the climate_model.rmd. The formula for this model is: elevation + land cover + distance to forests + population density + population density2 +  distance to recreational areas + distance to streams + terrain ruggedness + distance to urban areas + distance to fires 1 year ago + distance to fires 2-3 years ago + distance to fires 4-5 years ago + drought

