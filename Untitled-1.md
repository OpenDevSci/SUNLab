






-----
<!-- --- 
title: "Palmer Penguins"
author: "Cobblepot Analytics"
format: 
  dashboard:
    #logo: images/penguins.png
    nav-buttons: [linkedin, twitter, github]
    scrolling: true
---


## Row {height=70%}

```{r}
```

## Row {height=30%}

```{r}
```

```{r}
```


---

# Bills 

```{r}
```

# Flippers {orientation="columns" scrolling="true"}

## Column

```{r}
```

```{r}
```

## Column 

```{r}
```

---

## Row

```{r}
```

## Row {.tabset}

```{r}
#| title: Chart 2
```

```{r}
#| title: Chart 3
```

---

## Row {height=70%}

```{r}
```

## Row {height=30%}

### Column {.tabset}

```{r}
#| title: Chart 2
```

```{r}
#| title: Chart 3
```

### Column

```{r}
```

::: {.card title="My Title"}
Card text 
:::

## Row {.tabset}

### Plots

```{r}
```

```{r}
```

### Data

```{r}
```

## Column {width=40%}

```{r}
```

```{r}
```

## Column {width=40%}

```{r}
```

::: {.card}
This text will be displayed within a card
:::

```{r}
```

::: {.card title="My Title"}
This text will be displayed within a card
:::



```
------------
------------
------------


    
    


-----

<!-- 
: 2024 Mar Mobil Tech (All data only) 
(fitbit_assent, mt_asnt_sig)

```{r}
library(tidyverse)
library(lubridate)

# Read the CSV file
data <- read_csv("/Users/shawes/Desktop/2024MarMobTech.csv")

# Inspect the first few rows of the dataset to ensure it's read correctly
print(head(data))

# Check unique values in 'site_name' and 'redcap_event_name' to ensure filtering conditions are correct
print(unique(data$site_name))
print(unique(data$redcap_event_name))

# Apply filter and select specified columns
filtered_data <- data %>%
    filter(site_name == "FIU", redcap_event_name == "5_year_follow_up_y_arm_1") %>%
    select(id_redcap, redcap_event_name, site_name, asnt_timestamp, fitbit_assent) # , mt_asnt_sig)


# Check if filtered_data is empty
if (nrow(filtered_data) == 0) {
    print("No rows match the filtering criteria.")
} else {
    # Recode variables as specified
    filtered_data <- filtered_data %>%
        mutate(
            asnt_timestamp = as.Date(asnt_timestamp),
            week = floor_date(asnt_timestamp, unit = "week"),
            # fitbit_assent = if_else(fitbit_assent == 2, 1, 0),
            # mt_asnt_sig = if_else(mt_asnt_sig == 1, 1, 0)
        )

    # Save the modified dataframe
    write_csv(filtered_data, "Modified2024MarMobTech_Recoded.csv")
}


```



-----

```{r}
library(dplyr)
library(readr)
library(lubridate)

# Read the CSV file
data <- read_csv("/Users/shawes/Desktop/2024MarBiospec.csv")

# Inspect the first few rows of the dataset to ensure it's read correctly
print(head(data))

# Check unique values in 'site_name' and 'redcap_event_name' to ensure filtering conditions are correct
print(unique(data$site_name))
print(unique(data$redcap_event_name))

# Apply filter and select specified columns
filtered_data <- data %>%
    filter(site_name == "FIU", redcap_event_name == "5_year_follow_up_y_arm_1") %>%
    select(id_redcap, redcap_event_name, site_name, asnt_timestamp, hair_status_y, dna_blood_y, teeth_donated_1_p)


# Check if filtered_data is empty
if (nrow(filtered_data) == 0) {
    print("No rows match the filtering criteria.")
} else {
    # Recode variables as specified
    filtered_data <- filtered_data %>%
        mutate(
            asnt_timestamp = as.Date(asnt_timestamp),
            week = floor_date(asnt_timestamp, unit = "week"),
            hair_status_y = if_else(hair_status_y == 2, 1, 0),
            dna_blood_y = if_else(dna_blood_y == 1, 1, 0),
            teeth_donated_1_p = if_else(teeth_donated_1_p == "yes", 1, 0)
        )

    # Save the modified dataframe
    write_csv(filtered_data, "Modified2024MarBiospec_Recoded.csv")
}


```

------- -->