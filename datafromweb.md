datafromweb
================
Pradeeti Mainali
2024-10-10

loading necessary libraries:

# Extracting tables:

``` r
url = "http://samhda.s3-us-gov-west-1.amazonaws.com/s3fs-public/field-uploads/2k15StateFiles/NSDUHsaeShortTermCHG2015.htm"

drug_use_html = read_html(url)
```

get the pieces I actually need.

``` r
marj_use_df = 
drug_use_html |>
  html_table() |>
# spits out the table you are looking for
  first() |> #takes the first element out of a table
  slice(-1)

# still not really tidy
```

### Learning assesment:

``` r
nyc_cost_df = 
  read_html("https://www.bestplaces.net/cost_of_living/city/new_york/new_york") |>
  html_table(header=TRUE) |>
  #header = true will let it know that the first row is the header.
  first()
```

# CSS Selectors

``` r
swm_html = read_html("https://www.imdb.com/list/ls070150896/")
```

``` r
swm_html |>
  #define CSS here. use html_elementS
  html_elements(".ipc-title-link-wrapper .ipc-title__text") |>
  html_text()
```

    ## [1] "1. Star Wars: Episode I - The Phantom Menace"     
    ## [2] "2. Star Wars: Episode II - Attack of the Clones"  
    ## [3] "3. Star Wars: Episode III - Revenge of the Sith"  
    ## [4] "4. Star Wars: Episode IV - A New Hope"            
    ## [5] "5. Star Wars: Episode V - The Empire Strikes Back"
    ## [6] "6. Star Wars: Episode VI - Return of the Jedi"    
    ## [7] "7. Star Wars: Episode VII - The Force Awakens"    
    ## [8] "8. Star Wars: Episode VIII - The Last Jedi"       
    ## [9] "9. Star Wars: Episode IX - The Rise of Skywalker"

``` r
swm_html |>
  html_elements(".dli-title-metadata-item:nth-child(2)") |>
  html_text()
```

    ## [1] "2h 16m" "2h 22m" "2h 20m" "2h 1m"  "2h 4m"  "2h 11m" "2h 18m" "2h 32m"
    ## [9] "2h 21m"

``` r
swm_html |>
  html_elements(".metacritic-score-box") |>
  html_text()
```

    ## [1] "51" "54" "68" "90" "82" "58" "80" "84" "53"

LEts import some books

``` r
books_html = read_html("https://books.toscrape.com/") |>
  html_elements(".product_pod a") |>
  html_text()
```
