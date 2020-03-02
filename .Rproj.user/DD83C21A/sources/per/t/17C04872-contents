library(cowplot)
library(ggplot2)
library(rnaturalearth)
library(sf)

world.wgs <- ne_countries(scale = "medium", returnclass = "sf")

world.moll <- st_transform(world.wgs, 54009) # world mollweide epsg code
world.rob  <- st_transform(world.wgs, 54030) # world robinson epsg code

p1 <- ggplot(world.moll) +
  geom_sf(size = 0.1) +
  theme_bw()

p2 <- ggplot(world.rob) +
  geom_sf(size = 0.1) +
  theme_bw()

full_p <- plot_grid(p1, p2,
                    ncol = 1,
                    labels = c("World Mollweide (EPSG: 54009)", "World Robinson (EPSG: 54030)"),
                    hjust = 0,
                    vjust = 2,
                    scale = c(0.9,0.9),
                    label_fontfamily = "mono",
                    label_size = 12)

ggsave(full_p, height = 16, width = 14, unit = "cm",device = "tiff", filename = "proj_edited.tiff")
ggsave(full_p, height = 16, width = 14, unit = "cm",device = "png", filename = "proj_edited.png")
