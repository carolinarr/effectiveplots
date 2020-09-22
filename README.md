# How to Make Effective Plots.
Material for PICSciE's "How to Make Effective Plots" workshop.

# PART I - Principles

## Principles for Creating Effective Visualizations

### Quick tips for Getting Started (Exploratory Phase)

1. Tidy data!
2. List variables
3. List data types & relationships of interest
4. Produce many, quick visualizations  
  
Helpful chart chooser: <https://www.data-to-viz.com/#explore>

### Principles for Effective Visualization (Presentation Phase)

1. Articulate the main idea your graphic should convey FIRST
2. Run through checklist of best practices
  * Avoid Common Pitfalls of Misleading Graphs
      + 
  * Go for Simplicity
      + 
  * Look at Text  
      + 
  * Look at Color
      + 
3. Test your graphic on others – with no hints

*** 

# PART II - Applying Principles + Visualization Resources

## Applying Effective Visualization Principles in R

Going to be using RStudio on myadroit.princeton.edu.  
Before launching RStudio, need to load packages on head node of Adroit.

### Upload Dataset in Adroit

Create 'effectiveplots' directory.  
Upload files.  

### Install & Load Packages 

On Adroit's head node: 
```{bash, eval=FALSE}
ssh <netid>@adroit.princeton.edu      # If working in terminal, log into Adroit.
module load rh/devtoolset/8           # Load modules.
R                                     # Start R.
```

Once in R:
```{r, eval=FALSE}
install.packages("dplyr")
install.packages("gpplot2")       
install.packages("scales")
```

*NOTE:* Package installation only needs to be done once.

### Open RStudio on MyAdroit
```{r eval=FALSE}

library(dplyr)      # to manipulate data
library(ggplot2)    # to make plots
library(scales)     # to use use "commas" in label argument for scale_y_continuous()

# load in dataset
d_covid <- read.csv("effectiveplots/covid_pop_latlong_2020-07-23.csv") 

# get variable names
names(d_covid)
head(d_covid)
```

### Default Plot

ggplot - Data, Aesthetics, Geometries

"An aesthetic is a visual property of the objects in your plot. Aesthetics include things like the size, the shape, or the color of your points."

```{r, eval=FALSE}
ggplot(data = ) + 
  geom_col()
```

### Improved Plot

```{r, eval=FALSE}

# Adjustments to Data
#*********************
# for AVOID COMMON PITFALLS OF MISLEADING GRAPHS
# to arrange bars from highest to lowest
d_covid_gg <- d_covid %>% 
  arrange() %>%  
  mutate()   

# for COLOR
# if want to highlight nj
d_covid_nj <- d_covid %>% 
  filter()

# Plotting
#*********************

ggplot(data = d_covid_gg) +
  geom_col(aes(x = state, y = total_cases)) +
  
  # 1. ARTICULATING MAIN IDEA
  # Add labels
  labs(title = "",
       subtitle = "",
       caption = "") +
  
  # 2. BEST PRACTICES
  
  # AVOID COMMON PITFALLS OF MISLEADING GRAPHS
  coord_flip() +
  scale_y_continuous()  +
  
  # SIMPLICITY
  theme_classic() +
  theme(
    panel.background = element_blank(),                # remove color of background panel
    panel.grid.major.y = element_blank(),              # remove major Y grid lines
    panel.grid.major.x = element_line(),               # define major X grid lines     
    panel.grid.minor = element_blank(),                # remove minor grid lines
    axis.line = element_blank(),
    axis.ticks = element_blank(),
    
    # TEXT
    plot.caption = element_text(), 
    plot.title.position = "plot",
    plot.caption.position = "plot", 
    plot.title = element_text(), 
    plot.subtitle = element_text(),
    axis.text = element_text(),
    axis.title.x.bottom =  element_text()) 
    ) +
  ylab("") +
  xlab() +
  
  # COLOR
  geom_col(data = , mapping = aes())
```


### Save Your Plot
```{r, eval=FALSE}
ggsave("<insert-your-file-path>/covid_nj.png")
```


### Resources

ggplot2 cheatsheet  
https://rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf

ggplot2 Main Page  
(see section 'Learning ggplot2')  
https://ggplot2.tidyverse.org/  

ggplot2 Themes  
https://ggplot2.tidyverse.org/reference/theme.html  

ggplot2 Theme Elements  
https://ggplot2.tidyverse.org/reference/element.html  

Various graphs and corresponding code, made in R with ggplot2:  
https://www.r-graph-gallery.com/index.html  

*** 

## Need help? Visualization Services at Princeton

.

### PRINCETON INSTITUTE FOR COMPUTATIONAL SCIENCE AND ENGINEERING (PICSciE) 

*Area of expertise:* General visualization (exploration / design / creation / storytelling / troubleshooting) and GIS training and support  
https://researchcomputing.princeton.edu/systems-and-services/visualization 

**PICSciE/Research Computing’s Visualization Staff**

Eliot Feibush  
*Visualization Scientist*  
efeibush@princeton.edu

William (Bill) Guthe  
*Senior Graphical Information Systems Visualization Analyst*   
wguthe@princeton.edu

Carolina Roe-Raymond  
*Visualization Analyst*  
c.roe-raymond@princeton.edu

**Help Through Email**  
cses@princeton.edu

**In-Person Help**  
Help Sessions (usually 245 Lewis Science Library, now on Zoom)  
Tuesdays 10:30 – 11:30 am  
Thursdays 2:00 – 3:00 pm  
https://researchcomputing.princeton.edu/education/help-sessions

**Project Consultations**  
Have a visualization you or your group would like to build, but want help getting there?   
You can apply to work with our visualization analysts over a semester to help you build the visualizations you need.   
Contact Carolina Roe-Raymond at (c.roe-raymond@princeton.edu) to apply.

**Workshops**  
https://researchcomputing.princeton.edu/workshops

. 

### GEOGRAPHIC INFORMATION SYSTEMS AND REMOTE SENSING AT PRINCETON UNIVERSITY; MAPS AND GEOSPATIAL INFORMATION

*Area of expertise:* GIS training, support, and data  
Library: https://library.princeton.edu/collections/pumagic  
Research Computing/OIT: https://researchcomputing.princeton.edu/vis-lab/gis

**Staff**  
Tsering Wangyal Shawa  
Princeton University Library  
shawatw@princeton.edu, 609-258-6804

William (Bill) Guthe  
Research Computing and OIT  
wguthe@princeton.edu, 609-258-4609

**Training available through… **

* Princeton courses
* Workshops
  - Register at: http://library.princeton.edu/collections/pumagic/workshops
* Esri self-paced e-Learning classes 
  - http://training.esri.com, contact Wangyal or Bill

. 

### CeDAR
*Area of expertise:* Tableau training and support  
https://cedar.princeton.edu/

. 

### VIS-E LAB
*Area of expertise:* Ethnographic data visualization  
https://anthropology.princeton.edu/research-programs/vize-lab

.

### DATA AND STATISTICAL SERVICES 
*Area of expertise:* Data and statistical consulting  
https://dss.princeton.edu/

.

### STOKES LIBRARY - STOKES VIZ HUB
*Area of expertise:* Digital research and data visualization grounded in qualitative analysis  
https://library.princeton.edu/stokes/stokes-viz-hub

.

### OFFICE OF POPULATION RESEARCH
*Area of expertise:* Offers workshop on graph design (among other topics)  
https://opr.princeton.edu/workshops/

 
