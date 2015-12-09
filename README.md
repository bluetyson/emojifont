emojifont
---------

    library(emojifont)
    ## list available emoji fonts
    list.emojifonts()

    ## [1] "OpenSansEmoji.ttf"

    ## load selected emoji font
    load.emojifont('OpenSansEmoji.ttf')

base plot
---------

    require(remoji)
    set.seed(123)
    x <- rnorm(10)
    set.seed(321)
    y <- rnorm(10)
    plot(x, y, cex=0)
    text(x, y, labels=emoji('cow'), cex=1.5, col='steelblue', family='OpenSansEmoji')

![](inst/figures/figure-markdown_strict/base_emoji-1.png)

ggplot2
-------

    d <- data.frame(x=x, y=y,
         label = sample(c(emoji('cow'), emoji('camel')), 10, replace=TRUE),
         type = sample(LETTERS[1:3], 10, replace=TRUE))
    require(ggplot2)
    ggplot(d, aes(x, y, color=type, label=label)) + geom_text(family="OpenSansEmoji", size=5)

![](inst/figures/figure-markdown_strict/ggplot_emoji-1.png)

ggtree
------

    require(ggtree)
    require(colorspace)

    tree_text=paste0(
        "(","(","(",
            "(",
                "(",
                   emoji("cow"), ",",
                   "(",
                      emoji("whale"),",",
                      emoji("dolphin"),
                   ")",
                "),",
                "(",
                   emoji('pig2'),",",
                   emoji('boar'),
                ")",
            "),",
           emoji("camel"),
        "),", emoji("fish"), "),", emoji("seedling"), ");")

    ggtree(read.tree(text=tree_text)) + xlim(NA, 7) +
       geom_tiplab(family="OpenSansEmoji", size=10,
                    color=rainbow_hcl(8))

![](inst/figures/figure-markdown_strict/ggtree_emoji-1.png)
