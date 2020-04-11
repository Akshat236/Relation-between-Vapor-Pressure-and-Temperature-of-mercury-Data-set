# Relation-between-Vapor-Pressure-and-Temperature-of-mercury-Data-set
This is a descriptive report accompanied with various types of graphs to develop mathematical model for the relation between the Vapor Pressure and Temperature of mercury

# Introduction to "Pressure data set"

This report will be guiding on how the "Pressure" data set can be used in R studio to graph and ananlyze the relation between the Vapor Pressure and Temperature.

Hypothesis: They are directly proportional 

Temperature(independent variable): How hot or cold a body is.

Vapor pressure(dependent variable): pressure exerted by the gas in equilibrium with a solid or liquid at a given temperature unit.

units:

.Vapor pressure: mm Hg or Torr

.Temperature: °C

Below we can find the a data frame with 19 observations on 2 variables.

```{r}
pressure.data = pressure
View (pressure.data)
dim(pressure.data)
```


Our variables are vapor pressure and temperature, and both of them are numeric. 
```{r}
str(pressure.data)
```

# Plotting histograms
Histograms can be used to study the frequency of the variables(Vapor Pressure and Temperature)

First we will graph the histogram for the vapor pressure, it is evident that the Vapour pressure of mercury is mostly between 0 and 50mm Hg. 

```{r}
hist(pressure.data$pressure, 20, col="Blue")
```

Next we will graph the histogram for the temperature, it is evident that the temperature of mercury is mostly between 0 and 20°C.

```{r}
hist(pressure.data$temperature, 20, col="red")
```

# Plotting a Box plot

We can now plot a Box plot, which will show the variation amongst our variables. We can deduce from the graph that the Temperature has a greater range of values than the Vapor Pressure. 

As we can see from the boxplot, the average temperature value is 150.

```{r}
boxplot(pressure.data$temperature, main="Box Plot", xlab="Temperature", ylab="Value", col = "red", pch=19)
```

As we can see from the boxplot, the average vapor pressure value is 25.

```{r}
boxplot(pressure.data$pressure, main="Box Plot", xlab="Vapour pressure", ylab="Value", col = "red", pch=19)
```

# Plotting a Scatter plot

The scatter plot below suggests that the relation between vapor pressure and temperature is exponential, as the function is approaching 0; Hence, my hypothesis is proven false. 

The slope of this graph is 1.51242
```{r}
plot(x=pressure.data$temperature, y=pressure.data$pressure, main = "Pressure data Scatter plot", xlab="Temperature(°C)", ylab="Vapor pressure(mm Hg)", pch=19, col="green")
lin.mod = lm(pressure.data$pressure~pressure.data$temperature)
pr.lm = predict(lin.mod)#Add line of best fit
lines(lowess(pressure.data$temperature, pressure.data$pressure), col = "blue")#Graphing a smooth curve
lines(pr.lm~pressure.data$temperature, col="blue", lwd=0.7)
abline(mod <- lm(pressure.data$pressure~pressure.data$temperature))
coef(mod)#calculate slope
```
