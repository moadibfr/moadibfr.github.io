Title: TechBlog is Up
Date: 2017-06-08 10:07
Category: TechBlog

Ok hi there, it's 10:07AM I'm gonna start a tach blog on gh pages to see how fast I can get it up.

For practical reason I'm starting to write this before going because I'll note all I have to do to get it working...

Ok let's start by installing pelican:
http://docs.getpelican.com/en/3.7.1/quickstart.html
```
mkcd -p  ~/Sources/perso/ghpages-blog
moadib@IX * ~/Sources/perso/ghpages-blog/sudo pip install --upgrade pelican markdown
pelican-quickstart
Welcome to pelican-quickstart v3.7.1.

This script will help you create a new Pelican-based website.

Please answer the following questions so this script can generate the files
needed by Pelican.


> Where do you want to create your new web site? [.]
> What will be the title of this web site? Hey My TechBlog is Up !!
> Who will be the author of this web site? MoAdiB
> What will be the default language of this web site? [en]
> Do you want to specify a URL prefix? e.g., http://example.com   (Y/n) n
> Do you want to enable article pagination? (Y/n) y
> How many articles per page do you want? [10]
> What is your time zone? [Europe/Paris]
> Do you want to generate a Fabfile/Makefile to automate generation and publishing? (Y/n) y
> Do you want an auto-reload & simpleHTTP script to assist with theme and site development? (Y/n) y
> Do you want to upload your website using FTP? (y/N) n
> Do you want to upload your website using SSH? (y/N) n
> Do you want to upload your website using Dropbox? (y/N) n
> Do you want to upload your website using S3? (y/N) n
> Do you want to upload your website using Rackspace Cloud Files? (y/N) n
> Do you want to upload your website using GitHub Pages? (y/N) y
> Is this your personal page (username.github.io)? (y/N) n
Done. Your new project is available at /home/moadib/Sources/perso/ghpages-blog
```

Ok seems I have everything set up, lets save this under /Sources/perso/ghpages-blog/content/TechBlog-Is-Up.md

and generate the blog:
```
pelican content
Done: Processed 1 article, 0 drafts, 0 pages and 0 hidden pages in 0.53 seconds.
```

Then it seems I could preview my website:
```
cd ~/projects/yoursite/output
python -m pelican.server
```

But let skip this and deploy to GitHub, I've set up my repository moadibfr.github.io
```
make github
pelican /home/moadib/Sources/perso/ghpages-blog/content -o /home/moadib/Sources/perso/ghpages-blog/output -s /home/moadib/Sources/perso/ghpages-blog/publishconf.py
WARNING: Feeds generated without SITEURL set properly may not be valid
Done: Processed 1 article, 0 drafts, 0 pages and 0 hidden pages in 0.40 seconds.
ghp-import -m "Generate Pelican site" -b gh-pages /home/moadib/Sources/perso/ghpages-blog/output
/bin/sh: 1: ghp-import: not found
Makefile:121: recipe for target 'github' failed
make: *** [github] Error 127
```

Ooops: http://docs.getpelican.com/en/3.7.1/tips.html
```
sudo pip install ghp-import

git init
Initialized empty Git repository in /home/moadib/Sources/perso/ghpages-blog/.git/
moadib@IX   ~/Sources/perso/ghpages-blog/git remote add origin git@github.com:moadibfr/moadibfr.github.io.git

make github
pelican /home/moadib/Sources/perso/ghpages-blog/content -o /home/moadib/Sources/perso/ghpages-blog/output -s /home/moadib/Sources/perso/ghpages-blog/publishconf.py
WARNING: Feeds generated without SITEURL set properly may not be valid
Done: Processed 1 article, 0 drafts, 0 pages and 0 hidden pages in 0.40 seconds.
ghp-import -m "Generate Pelican site" -b gh-pages /home/moadib/Sources/perso/ghpages-blog/output
git push origin gh-pages
Counting objects: 44, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (29/29), done.
Writing objects: 100% (44/44), 32.45 KiB | 0 bytes/s, done.
Total 44 (delta 12), reused 44 (delta 12)
remote: Resolving deltas: 100% (12/12), done.
To git@github.com:moadibfr/moadibfr.github.io.git
 * [new branch]      gh-pages -> gh-pages
git push origin gh-pages:master
```

Ok I'll slightly edit the makefile to publish with "make github"
```
vi Makefile
github: publish
        ghp-import -m "Generate Pelican site" -b $(GITHUB_PAGES_BRANCH) $(OUTPUTDIR)
        git push origin $(GITHUB_PAGES_BRANCH)
become:
github: publish
        ghp-import -m "Generate Pelican site" -b $(GITHUB_PAGES_BRANCH) $(OUTPUTDIR)
        git push origin $(GITHUB_PAGES_BRANCH)
        git push origin $(GITHUB_PAGES_BRANCH):master
```

Ho just so you know. My first step was to get sublime having a markdown preview and I'm now a sublime power user so I took some time to update it and then:
```
control+shift+p
install package
> install "pp" and "pp-markdown"
``̀

And https://help.github.com/articles/creating-and-highlighting-code-blocks/ helped ;)
