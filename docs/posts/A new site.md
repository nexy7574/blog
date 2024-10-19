---
draft: false
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

## Rationale & Experience

### So, why mkdocs?

I chose mkdocs for a few reasons, but it can be summarised to "I already knew what it did".

While I was looking for a new blog engine, I was just jumping in head first into these programs I'd never heard of before.
I had no idea what they did, what their capabilities and limitations were, what sort of deployment they needed, etc etc.
This was very discouraging, as a lot of them ended up being *too* minimalistic, or *too* complex for what I wanted.

**Enter mkdocs**

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

### The setup process

The setup process was actually, in my opinion, relatively short.

I already knew how to get an mkdocs site going - install mkdocs and run the new command.
Then, I knew about mkdocs-material, so I searched up "mkdocs material blog", which lead me to
the link above. This guide did a great job at documenting just how simple it was to get a simple
markdown-based blog going, and even some extra goodies.

I then spent maybe an hour tinkering around with plugins, discovering the RSS plugin
(which you can subscribe to with the RSS button in the footer), messing with the theme, etc,
until I came to the conclusion that 
[this config](https://codeberg.org/nexy7574/blog/src/branch/dev/mkdocs.yml)
was the one that I was happy with.

And it was as simple as that! I was already able to write my first post, which is
hello world. Of course though, this is just 30 minutes of lorem ipsum. This that you're reading is my
first ACTUAL post.

---

This wasn't without a hurdle though.
Yes, that's right, a singular hurdle.

I couldn't figure out why my entire blog posts were being rendered on the home page, instead of just an
excerpt.
This was a fairly easy mistake to not only make, but also fix, so I am just documenting it here in case
someone finds this with some search engine magic and it solves their problem.

To get only part of your blog post, not the full blog post, on your home page, all you need to do
is add `<!-- more -->` to your markdown file where you want the excerpt to end.
It is also beneficial to have

```yaml
plugins:
  - blog:
      post_excerpt: required
```

in your mkdocs.yml config, so that your blog will not build without an excerpt, preventing you from
publishing a post without an excerpt.

### Publishing to codeberg pages

I chose to write this blog and host it on Codeberg, as I have recently been migrating to Codeberg mainly.

Those of you who have known me for a long time will know that I used to host my own git server,
forgejo, at <https://git.i-am.nexus>. However, due to my unreliable hard drives, and financial situation,
I decided that it is unsafe to host projects that I intend to keep long term on my own instance.
I wrote a quick script that would mass-migrate my forgejo repos to Codeberg, and
manually went through and replaced all of my remote references for other projects.

!!! danger "The git server will be pulled down at some point"
    **Update** as of 2024-10-19: The domain is now redirecting all queries to their equivalent on Codeberg.
    If you visit <https://git.i-am.nexus/nex/howmuchdoesthesims4cost.lol> for example, you will be
    redirected to <https://codeberg.org/nexy7574/howmuchdoesthesims4cost.lol>.

    ~~I do not intend to keep the forgejo server running forever, so do not visit that link in the future.
    If I remember, I will update this post.~~

This also came with another big advantage - codeberg pages.
Codeberg "recently" (to my knowledge) launched <https://codeberg.page>, which allows
<https://codeberg.org> accounts to host static sites for free. The best part is, I can use CI to
just push to a branch, and it will be automatically deployed.

This is great, as it means I do not have to worry about the generation, deployment, OR hosting aspects
of running the blog. I get to focus purely on writing the content.
The workflow with codeberg pages works like this:

1. Write the content I want to publish
2. Make sure it looks good locally before pushing. If not, whack it in `drafts/` and come back later.
3. Push to the `dev` branch
4. CI kicks in, builds the site
5. CI pushes the built site to the `pages` branch
6. codeberg automatically recognises that the site has been re-built, and serves the new documents.

So really, the only human part of this process is steps 1 and 2. The rest is done automatically,
even RSS!

## Conclusion

I hope that by starting this blog, I can more easily share my experiences with people in a format that
is easier to preserve, and allows for richer display and interaction than some other formats I have tried.

mkdocs as a blog engine, codeberg for the SCM, and codeberg pages for the hosting, it all comes together to
make a very nice experience for me, and I hope for you too, should you want to start your own blog.
