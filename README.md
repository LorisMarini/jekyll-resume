# Resume
*Resume template powered by Jekyll + GitHub Pages. Cloned and adapted from [jglovier](https://github.com/jglovier/resume-template)*.

![img](social_preview.png)

## Quick Start

Make sure you have an appropriate [version of ruby](#ruby-environment) installed. To run locally:

1. clone repo
1. `bundle install` (uses [bundler](https://bundler.io/) to install the project dependencies specified in the Gemfile(s))
2. `bundle exec jekyll serve`
3. Open your browser to `localhost:4000`

Most of the basic customisation will take place in the `/_config.yml` file. Most of the content configuration will take place in the `/_layouts/resume.html` file.

## Contributions

I made some changes to the structure of the content in `_data` and `_layouts/resume.html`.

- Favicon: line 17 of `_layouts/head.html`. Remember to remove `/` when specifying the file name as [@LazaroIbanez](https://medium.com/@LazaroIbanez/how-to-add-a-favicon-to-github-pages-403935604460) pointed out.

- Template keys: I added `environment`, `responsibilities` and `achievements` to the layout. Surely more verbose than what [@jglovier](https://github.com/jglovier/resume-template) did, but worth it imo. Since `_layouts/resume.html` controls which of these fields are included in the build remember to change the key names there as well.

- Hyperlinks: Added a `target="_blank"` in `_includes/icon-links.html` to keep the reader focused on the main page.

- Social Preview: It's a png image at 1.6 ratio called `social_preview.png` saved in the settings of this repository. This is what pops up when sharing the link on Slack/Telegram etc.

- SEO: plugin to make it easier to find the page online [see docs](https://help.github.com/en/articles/search-engine-optimization-for-github-pages)

- Google Analytics: Added the plugin `jekyll-analytics` and configured Google Analytics to have fun tracking traffic.

## Ruby environment

If you are on macOS chances are you will run into issues when trying to make changes to the system ruby at `/usr/bin/ruby`. As suggested in this [stack-exchange thread](https://stackoverflow.com/questions/51126403/you-dont-have-write-permissions-for-the-library-ruby-gems-2-3-0-directory-ma), I recommend installing another version of ruby and control it with a ruby version manager.
Popular options are *RVM*, *rbenv* and *chruby*, I chose the latter because I like transparency, predictability and control. I also installed ruby with [ruby-install](https://www.ruby-lang.org/en/documentation/installation/#ruby-install) which works well with chruby. For a more in depth discussion and guidelines see this blog post by [Steve Marshall](https://stevemarshall.com/journal/why-i-use-chruby/). To get that going:

```
brew update
brew install chruby
```

then add this line to your **~/.bashrc** or **~/.zshrc** file as detailed in the [configuration section](https://github.com/postmodern/chruby#configuration) of the readme:

```
 source /usr/local/opt/chruby/share/chruby/chruby.sh
```

If you are using zsh I recommend adding the line above to `~/.oh-my-zsh/custom/chruby.zsh` (create it if it does not exist). This works thanks to zsh [customisations](https://github.com/ohmyzsh/ohmyzsh/wiki/Customization), which are automatically sourced by the oh-my-zsh.sh [script](https://github.com/ohmyzsh/ohmyzsh/blob/master/oh-my-zsh.sh#L95). Then install the ruby installer **ruby-install**, which you'll use to install any version of ruby you need:

```
brew install ruby-install
```
The first time it runs, `ruby-install` updates the latest versions of the packages you can install. You should see something like this:

```
>>> Downloading latest ruby versions ...
>>> Downloading latest jruby versions ...
>>> Downloading latest rbx versions ...
>>> Downloading latest truffleruby versions ...
>>> Downloading latest mruby versions ...
Stable ruby versions:
  ruby:
    2.4.9
    2.5.7
    2.6.5
    2.7.0
  jruby:
    9.2.11.0
  rbx:
    4.15
  truffleruby:
    20.0.0
  mruby:
    2.1.0
```

Now you can install a version of ruby [compatible with Jekyll](https://jekyllrb.com/docs/installation/), I am just going with the latest (takes a good 10 minutes):

```
ruby-install ruby-2.7.0
```

Now this `chruby system && which ruby` results in `/usr/bin/ruby`, while `chruby ruby-2.7.0 && which ruby` returns `~/.rubies/ruby-2.7.0/bin/ruby`. To make this the default in any new shell update or create the file `~/.oh-my-zsh/custom/ruby.zsh` with the line `chruby ruby-2.7.0`.

## Publishing to GitHub Pages

[GitHub Pages](https://pages.github.com/) will host this for free with your GitHub account. Just make sure you're using a `gh-pages` branch, and the site will automatically be available at `yourusername.github.io/resume-template` (you can rename the repo to resume for your own use if you want it to be available at `yourusername.github.io/resume`). You can also add a CNAME if you want it to be available at a custom domain...

**Your own domain name**

To setup your GH Pages site with a custom domain, [follow the instructions](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages/) on the GitHub Help site for that topic.
