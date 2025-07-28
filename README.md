# Generating a Forest plot with SMD as effect size

## Step 1: Load Packages
```
# Install if needed
install.packages("meta")

# Load in library
library(meta)
```

## Step 2: Insert Dataset in CSV Format
##### Make sure data already recorded in the form of n, SD and mean for both treatment and control groups. Example shown below:
<img width="613" height="186" alt="Screenshot 2025-07-28 at 1 52 59 PM" src="https://github.com/user-attachments/assets/5597c402-8458-4303-a0f3-b89d9f878c3d" />

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
##### Example detailed results shown below:
<img width="606" height="477" alt="Screenshot 2025-07-28 at 1 53 53 PM" src="https://github.com/user-attachments/assets/7f71ab9a-597c-4ebe-9f53-e8ec3258b0fd" />


## Step 6: Results in Plot 
```
# Generate forest plot 
forest(res)
```
##### Example forest plot shown below:
<img width="1001" height="297" alt="MWM_AD" src="https://github.com/user-attachments/assets/e1d69bea-c913-4448-82ec-4a6fb7468819" />
