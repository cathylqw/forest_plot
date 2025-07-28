## Step 1: Load Packages
```
# Install if needed
install.packages("meta")

# Load in library
library(meta)
```

## Step 2: Insert Dataset in CSV Format
#### Make sure data already recorded in the form of n, SD and mean for both treatment and contro groups
```
# Load your data 
df <- read.csv("your_dataset")

# Check headings of dataset 
head(df)
```

## Step 3: Pre-set Forest Plot Criteria 
#### e = experimental group; c = control group
```
# Make sure dataset column headings are accurate
res <- metacont(
  n.e = df$n.e,
  mean.e = df$mean.e,
  sd.e = df$sd.e,
  n.c = df$n.c,
  mean.c = df$mean.c,
  sd.c = df$sd.c,
  studlab = df$Study,
  sm = "SMD",              # Standardised Mean Difference
  method.smd = "Hedges",   # Use Hedges’ g as effect size 
  random = TRUE,           # use Random effect model 
  common = FALSE,          # don't use Fixed effect model
  label.left = "Favors Control",    # Change accordingly
  label.right = "Favors Treatment"  # Change accordingly 
)
```

## Step 4: Adjustment of Font and Plot Width Sizes
```
# Changing the font size and plot width 
library(grid)
metacont(forest(res,
                plotwidth = unit(12, "cm"),         # Insert your own value
                fontsize = 8                       # Optional: readable size
         )
)
```

## Step 5: Results in Numbers 
```
# Print meta-analysis results
summary(res)
```

## Step 6: Results in Plot 
```
# Generate forest plot 
forest(res)
```
