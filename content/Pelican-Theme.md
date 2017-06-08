Title: Pelican Theme
Date: 2017-06-08 10:40
Category: TechBlog

Hey I want a theme for my TechBlog !!


http://www.pelicanthemes.com/

I think I like this one: http://bricabraque.github.com (https://github.com/getpelican/pelican-themes/tree/master/bricabrac)

So the readme state:
```
How-to

To use this theme, just extract the archive and copy the bricabrac theme folder to the themes folder in your Pelican site path. Then add the line below to your pelicanconf.py :

THEME = 'themes/bricabrac-pelican-theme'
```

I'll do it with git instead:
```
moadib@IX   ~/Sources/perso/git clone --recursive https://github.com/getpelican/pelican-themes
moadib@IX * ~/Sources/perso/mkdir ghpages-blog/themes
moadib@IX   ~/Sources/perso/mv pelican-themes/bricabrac ghpages-blog/themes/

vi ghpages-blog/pelicanconf.py
THEME = 'themes/bricabrac'
```
