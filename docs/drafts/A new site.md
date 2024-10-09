---
draft: true
date: 2024-10-09
categories:
  - Programming
  - Software
  - Meta
---

# A(nother) new site

Well, the time has come. I have for months, possibly even over a year, been putting off the creation of creating a blog.
In this time, I have tried many different attempts, but in the end none of them ever stuck.
I've tried using some cool projects like Writefreely, some projects friends have made, and even writing my own blog engine.

But finally, I have settled on using [mkdocs](https://www.mkdocs.org/), a static site generator that uses markdown files to generate a static site.
In this first real blog post, I will be talking about why I chose mkdocs, and talking about my experience with setting it up.

<!-- more -->

## So, why mkdocs?

I chose mkdocs for a few reasons, but it can be summarised to "I already knew what it did".

While I was looking for a new blog engine, I was just jumping in head first into these programs I'd never heard of before.
I had no idea what they did, what their capabilities and limitations were, what sort of deployment they needed, etc etc.
This was very discouraging, as a lot of them ended up being *too* minimalistic, or *too* complex for what I wanted.

### Enter mkdocs

I have [used mkdocs for documentation](https://docs.nio-bot.dev) before, and I have loved almost every second of using it.
The things that I love about mkdocs are:

- It is beautiful by default
- Plugins are super easy to add and use
- There are a lot of batteries included, meaning I can focus on writing content, instead of setting everything up
- It is very easy to deploy, as it renders to a static site
- It is very easy to write in, as it uses markdown, with plugins adding in extensions

And, all of this means it is not only well suited to docs, but it is also great for a blog!

As stated on the [mkdocs-material](https://squidfunk.github.io/mkdocs-material/setup/setting-up-a-blog/) docs page, it is very easy to set up a blog,
and they weren't lying. It was very easy to set up, and I was able to get it up and running and start publishing in under an hour!

## The setup process

The setup process could easily be summarised into a few steps:

1. Set up a directory
2. Run `git init`
3. Run `python3 -m venv venv && source venv/bin/activate`
4. Install the dependencies - see [`requirements.txt`](https://codeberg.org/nexy7574/blog/src/branch/dev/requirements.txt)
5. Run `mkdocs new .`
6. Scan over the configuration on the mkdocs-material site, and adjust my [`mkdocs.yml`](https://codeberg.org/nexy7574/blog/src/branch/dev/mkdocs.yml) accordingly
7. Run `mkdocs serve` and start writing a blog
8. Push to git
9. Run `mkdocs gh-deploy` to deploy to Codeberg Pages
10. Done!
