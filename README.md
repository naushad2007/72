## nytimes: R package accessing NYTimes' API
- R functions for accessing New York Times' article search API
- Created during CRMDA's Big Dynamic Data working group

## Install and load

```{r}
install.packages("devtools")
devtools::install_github("mkearney/nytimes")
library(nytimes)
```

## Authorizing API access
- Use code below to create environment variable to store your api key,
  which you can acquire here: [https://developer.nytimes.com/signup](https://developer.nytimes.com/signup)

```{r}
## replace x's with nytimes article search API key which
##    you can acquire by visiting the following URL:
##    https://developer.nytimes.com/signup
apikey <- paste0("NYTIMES_KEY=", "xxxxxxxxxxxxxxxxxxxxxxxxxxxx")

## make path to .Renviron
file <- file.path(path.expand("~"), ".Renviron")

## save environment variable
cat(apikey, file = file, append = TRUE, fill = TRUE)
```

## Demonstration

```{r}
## get http response objects for search about sanctions
r <- get_nyt("sanctions", n = 2000)

## collapse results into tidy data frame
nytdf <- parse_nyt(r)

## preview object structure
str(nytdf, 1)

## preview data
head(nytdf, 10)
```
