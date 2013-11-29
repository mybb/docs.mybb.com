[![MyBB](https://raw.github.com/mybb/mybb/feature/images/logo.png "MyBB")](http://mybb.com "MyBB")
# MyBB Documentation

The MyBB 1.8 documentation.

## Contributions

In this repository we are rewriting our documentation in Markdown for the release of MyBB 1.8. We're using Jekyll to build the documentation website and GitHub pages to host it. **We're still at a very early stage**.

### How to Contribute

Contributing is easy:

1. Fork the repository
2. Add pages, improve existing pages, fix typos - whatever
3. Push the changes to the forked repository
4. Send us a pull request

In the future we will document and explain the whole process of contributing to the MyBB Documentation and the MyBB software itself more thoroughly so anyone can help. In the meantime we have to assume you understand and have experience with git. That said, don't worry if you're scared of screwing things up. We will review your pull request so if anything's wrong we won't merge it.

Disregard the `assets/css/` and `_layouts/` directories and the `_config.yml` file. These things are specific to Jekyll, the engine our documentation runs on top of. Don't worry about it, simply add articles to their appropriate categories or create new ones if you have to and write your stuff in Markdown. At the top of each Markdown file you have to add a block of code which Jekyll calls YAML Front Matter and edit it accordingly. For example:

```
---
layout: page
title:  "FAQ"
---
```

Simply edit the title to your page's. Then you can write your page in Markdown below.

### Style Guide

In order to maintain OCD-friendly documentation we follow a strict set of rules. In no particular order:

1. Use the [standard Markdown syntax](http://daringfireball.net/projects/markdown/syntax). Only use HTML if there's no Markdown equivalent (e.g. tables).
2. Use proper English grammar.
3. Do not use quotation marks to emphasize words. Instead use single asterisks (e.g. `*foo*`) or double asterisks to denote important words (e.g. `**bar**`).
4. Do not use more than one newline anywhere. Always use one newline to separate paragraphs, headings, etc.
5. Only use inline code and code blocks to markup actual code, file contents or file names.
6. Carefully indent the values of the [YAML Front Matter](http://jekyllrb.com/docs/frontmatter/) so that they align with each other.
7. Do not create a Contents section. TOCs are dynamically generated with JavaScript.
8. Capitalize the words in heading titles according to the [MLA](http://www.mla.org/) format, e.g. `Uploading the Language Files`.
9. When linking to internal pages use relative links, e.g. `[Using FTP](http://docs.mybb.com/install/ftp)` should be `[Using FTP](install/ftp)`.

When in doubt look through the existing pages and their markup.

### What to Contribute

Browse [the current MyBB documentation](http://docs.mybb.com/) and pick **any article**. Copy paste it into a new file. Rewrite it in Markdown very neatly and put it under the right category.
