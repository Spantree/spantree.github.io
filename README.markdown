# Spantree's Blog

## Setup

Octopress requires Ruby 1.9.3. To install this with RVM, do

```
\curl -L https://get.rvm.io | bash -s stable --ruby
rvm install 1.9.3
rvm use 1.9.3
```

Note: The rvm install takes a fairly long time.

Run the following commands after cloning

```
gem install bundler
bundle install
```

## Blogging

In order to create a new blog post, run `rake new_post['title']`

This will create a markdown file in the `source/posts` directory, which you can then edit to create the actual post. 

It's highly recommended that one of the first things you do is add `published: false` to the top of the article. This will prevent it from being published before it is ready.

To view your changes, run `rake preview`, which will start a server at `localhost:4000` for you to view the blog.

## Publishing

When you are ready to publish the article, change the file to say `published: true`. After that, run the following:

`
rake generate
rake deploy
`

This will generate your blog, copy the generated files into `_deploy/`, add them to git, commit and push them up to the master branch. 

## What is Octopress?

Octopress is [Jekyll](https://github.com/mojombo/jekyll) blogging at its finest.

1. **Octopress sports a clean responsive theme** written in semantic HTML5, focused on readability and friendliness toward mobile devices.
2. **Code blogging is easy and beautiful.** Embed code (with [Solarized](http://ethanschoonover.com/solarized) styling) in your posts from gists, jsFiddle or from your filesystem.
3. **Third party integration is simple** with built-in support for Pinboard, Delicious, GitHub Repositories, Disqus Comments and Google Analytics.
4. **It's easy to use.** A collection of rake tasks simplifies development and makes deploying a cinch.
5. **Ships with great plug-ins** some original and others from the Jekyll community &mdash; tested and improved.


## Documentation

Check out [Octopress.org](http://octopress.org/docs) for guides and documentation.
