+++
title = "xfel-init-project.el"
author = ["Fernando Jascovich"]
date = 2019-12-28
lastmod = 2019-12-28T15:40:49-03:00
tags = ["emacs", "project", "management"]
draft = false
weight = 2003
layout = "single"
+++

After trying some project management tools for emacs, I found several great and thorough packages which I used on a daily basis for software development:

-   [Projectile](<https://github.com/bbatsov/projectile>)
-   [Ivy](<https://github.com/abo-abo/swiper>)

But then, after a while of using those great tools, I noticed that there are little functionality that I really use from those packages. And, as an excuse for exercising elisp, I decided to write some... let's say "helpers" for working every day.

This is the result: [xfel-init-project.el](<https://github.com/fernando-jascovich/dotfiles/blob/master/emacs/xfel-init-project.el>).

As you can see, there are a few things that I use daily for working besides, of course, all the things that emacs has out-of-the-box. Ok, not all the things... who really knows all the things that emacs has inside?

So, by relying on [rg](<https://github.com/BurntSushi/ripgrep>) for getting file lists and searching inside those files, I wrote a super simple file finder and the inclusion of rg results inside \`grep-find\` (this function in particular because it produces a compile buffer with the ability of enabling [wgrep](<http://github.com/mhayashi1120/Emacs-wgrep>) and having an excellent global search-and-replace thing).

Other thing to mention is that I use ido, mainly because it comes with emacs, so I don't have to install any additional package for completion.

I hope this helps someone looking for simple or personal alternatives for everyday tasks.

P.S.: My configuration files are in the same repository -> [init.el](<https://github.com/fernando-jascovich/dotfiles/blob/master/emacs/init.el>)
