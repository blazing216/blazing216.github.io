---
layout: post
title:  Run Jekyll locally
date:   2024-06-03 22:02
description: 
tags: 
---

I wanted to run Jekyll locally to test my website, but failed to 
run `bundle install`. Following the warning message, I updated
the bundler by 
```bash
sudo gem install bundler -v 2.4.22
```
I could not install the lastest version of bundler because
my Ruby version is not new enough (>= 3.0.0 was required, but
my version was 2.4.22). 

I tried `bundle install` again, which failed again. Following the
recommendation, I updated `gem`
```bash
sudo gem update --system 3.2.3
```

Along the way I learned that `Jekyll` is a `Ruby Gem`.

Following the instructions on 
`https://jekyllrb.com/docs/installation/macos/`,
I installed the ruby again using `chruby`. The steps were
```
brew install chruby ruby-install xz
```
Add the following lines to `~/.bash_profile`,
```
source /opt/homebrew/opt/chruby/share/chruby/chruby.sh
source /opt/homebrew/opt/chruby/share/chruby/auto.sh
export LDFLAGS="-L/opt/homebrew/opt/curl/lib"
export CPPFLAGS="-I/opt/homebrew/opt/curl/include"
export PKG_CONFIG_PATH="/opt/homebrew/opt/curl/lib/pkgconfig"
```
Install the ruby
```
ruby-install ruby 3.1.3
```
Add the following lines to `~/.bash_profile`,
```
chruby ruby-3.1.3
```
Install jekyll, bundler
```
gem install jekyll
gem install bundler
```
Run
```
bundle install
```
Start the server
```
bundle exec jekyll serve
```

A tiny problem was met that `Jekyll Diagrams: Command Not Found: mmdc`
The problem can be solved by
```
brew install npm
npm install -g @mermaid-js/mermaid-cli
npm install -g npm@10.8.1
```

If open `http://127.0.0.1:4000/` in a web broswer, then we
can view the website locally.

After making any changes to the files, without re-run 
`bundle exec jekyll serve` again, just refresh the page to 
see the changes. It may take a few seconds to recompile the
website.