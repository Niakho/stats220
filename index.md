# Information about the Meme
The formating of the meme is an adaption of exiting meme format of picture and text followed by picture and text.
The images used are the combination of using well known Pikachu images.
The inspiration of this meme is from how students tend to procrastinate until the very last moment.  


# Library
```r
library(magick)
```

# meme images
```r
sleep_pika <- image_read("https://pbs.twimg.com/media/D8qKs4IXkAAz9rK.jpg") %>%
  image_scale(900)


surprised_pika <- image_read("https://i.kym-cdn.com/entries/icons/mobile/000/027/475/Screen_Shot_2018-10-25_at_11.02.15_AM.jpg") %>%
  image_scale(900)
```

# text box
```r
time_spent <- image_blank(width = 500, 
                       height = 506, 
                       color = "#e6e6e6") %>%
  image_annotate(text = "Casually\nProcrastinating",
                 color = "#000000",
                 size = 60,
                 font = "Impact",
                 gravity = "center")


due_tmr <- image_blank(width = 500, 
            height = 500, 
            color = "#e6e6e6") %>%
  image_annotate(text = "Assignment\nIs Due Tomorrow",
                 color = "#000000",
                 size = 60,
                 font = "Impact",
                 gravity = "center")
```

# making each row
```r
sleep <- c(sleep_pika, time_spent)
top_row <- image_append(sleep)

surprise <- c(surprised_pika, due_tmr)
bottom_row <- image_append(surprise)
```

# meme format
```r
meme <- c(top_row, bottom_row) %>%
  image_append(stack = TRUE) %>%
  image_scale(800)

meme
```
# exporting meme
```r
image_write(meme, "my_meme.png")
```


