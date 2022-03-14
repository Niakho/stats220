library(magick)

# meme images
sleep_pika <- image_read("https://pbs.twimg.com/media/D8qKs4IXkAAz9rK.jpg") %>%
  image_scale(900)


surprised_pika <- image_read("https://i.kym-cdn.com/entries/icons/mobile/000/027/475/Screen_Shot_2018-10-25_at_11.02.15_AM.jpg") %>%
  image_scale(900)


# text box
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


# making each row
sleep <- c(sleep_pika, time_spent)
top_row <- image_append(sleep)

surprise <- c(surprised_pika, due_tmr)
bottom_row <- image_append(surprise)

# meme format
meme <- c(top_row, bottom_row) %>%
  image_append(stack = TRUE) %>%
  image_scale(800)

meme

# exporting meme
image_write(meme, "my_meme.png")

