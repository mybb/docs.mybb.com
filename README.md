[![MyBB](https://raw.github.com/mybb/mybb/feature/images/logo.png "MyBB")](http://mybb.com "MyBB")
# MyBB Documentation

The MyBB 1.8 documentation.

## Contributions

In this repository we are rewriting our documentation in Markdown for the release of MyBB 1.8. We're using Jekyll to build the documentation website and GitHub pages to host it. **We're still at a very early stage**.

### How to Contribute

Contributing is easy:

1. Fork the repository
2. Add pages, improve existing pages, fix typos
3. Push the changes to the forked repository
4. Send us a pull request

Disregard the `css/` and `_layouts/` directories and the `_config.yml` file. These things are specific to Jekyll, the engine our documentation runs on top of. Don't worry about it, simply add articles to their appropriate categories or create new ones if you have to and write your stuff in Markdown. Always refer to the [Markdown Syntax Documentation](http://daringfireball.net/projects/markdown/syntax). At the top of each Markdown file you have to add a block of code which Jekyll calls YAML Front Matter and edit it accordingly. For example:

    ---
    layout: page
    title: What to do if you get hacked
    ---

Simply edit the title to your page's. Then you can write your page in Markdown below. Don't use HTML unless there is no Markdown syntax for what you want to markup. And if you use HTML don't add any classes to tags or anything, just pure HTML. Use proper English grammar of course.

In the future we will document and explain the whole process of contributing to the MyBB documentation and the MyBB software itself more thoroughly so anyone can help. In the meantime we have to assume you understand and have experience with git. That said, don't worry if you're scared of screwing things up. We will review your pull request so if anything's wrong we won't merge it.

### What to Contribute

Browse [the current MyBB documentation](http://docs.mybb.com/) and pick **any article**. Copy paste it into a new file. Rewrite it in Markdown very neatly and put it under the right category.

Try not to pick articles which have images of the MyBB software. These images will have to be updated to 1.8 images, and 1.8 is not ready yet.
