---
title: "Contribution Guide to JunctionXHanoi Blog"
description: "Contribution Guide to JunctionXHanoi Blog"
keywords: ['blog', 'software', 'software-engineering', 'technology', 'code']
---

First of all, thank you for sharing your ideas, knowledge, opinions 🎉🎉 You are awesome and we love you 😍😍

️🧡💛💚💙💜🖤

The following is a set of guidelines for contributing to our blog.
We tried to be as comprehensive as possible, but if you feel that there is more to this, please feel free to propose changes to this in a pull request.

### Table of Content

> [Contribute as an author](#author)
>
> [Contribute as a translator](#translator)
>
> [Bonus: Fancy author profile](#bonus)
>
> [Doubts and questions](#question)

### <a name="author" id="author"></a> I. Contribute as an author

Step-by-step guide for your new post to be on [JunctionXHanoiBlog](https://junctionxhanoiblog.github.io)

##### Setting up local env

Start by forking [this repository](https://github.com/junctionxhanoiblog/junctionxhanoiblog) and then clone it recursively to your local workspace

```bash
git clone https://github.com/YOUR-USERNAME/junctionxhanoiblog --recursive
cd junctionxhanoiblog
```

Check if you have [hugo](https://gohugo.io) installed by running `hugo version`.
If you haven't already installed [hugo](https://gohugo.io), please follow the instruction on [their site](https://gohugo.io/getting-started/installing/).

##### Start a new post

Generate a new post from our theme template by running

```bash
hugo new posts/YOUR-POST-NAME/index.md # we will explain why index.md in the next section
```

Fill in all the necessary fields:

- title: try to keep it short and captivating.
- date: must be in [ISO-8601 format](https://en.wikipedia.org/wiki/ISO_8601), [this timestamp generator](https://timestampgenerator.com/) might come handy for such.
- authors: A collection (array) of post authors' full/pen names. For fancy authors' profiles, head down to [bonus section](#bonus)
- cover: image that will be shown in preview and at the top of your post
- tags: topics of your post
- keywords: same as tags but can be more specific
- description: a short summary of your post to be shown in preview
- showFullContent: please keep this as false to share blog's estate with other authors

Write your blog post in markdown with an enhanced flavor from [hugo](https://gohugo.io/).
If you are intending to do more than just standard mardown (md), checkout [hugo docs](https://gohugo.io/content-management/) to learn more.

##### Static assets

We intend to use leaf bundle organisation for all posts on [JunctionXHanoi Blog](https://junctionxhanoiblog.github.io), which is the reason why you were asked to create a folder with your post name and an `index.md` for post content.
Your final product with some static assets would look something like this

```
content/
├── about
│   ├── index.md
├── posts
│   ├── my-post
│   │   ├── content1.md
│   │   ├── content2.md
│   │   ├── image1.jpg
│   │   ├── image2.png
│   │   └── index.md
│   └── my-other-post
│       └── index.md
│
└── another-section
    ├── ..
    └── not-a-leaf-bundle
        ├── ..
        └── another-leaf-bundle
            └── index.md
```

- **my-post**
  - This leaf bundle has the index.md, two other content Markdown files and two image files.
- **image1**
  - This image is a page resource of my-post and only available in my-post/index.md resources.  
- **image2**
  - This image is a page resource of my-post and only available in my-post/index.md resources.

Then your assets can be included in the post using the full path with `content` folder as root
(i.e. `/posts/test-posts/cover.jpg` is the needed path to include the cover image).

##### Letting us know 🎉🎉

After you are done with your post, please open a [Pull Request](https://github.com/junctionxhanoiblog/junctionxhanoiblog/compare) labelled `post` on our repository and your post will be up in no time. 🥳🥳

### <a name="translator" id="translator"></a> II. Contribute as a translator

Step-by-step to make your contribution by translating someone else's post on [JunctionXHanoi Blog](https://junctionxhanoiblog.github.io)

##### Seeking permission from original author

Open [an issue](https://github.com/junctionxhanoiblog/junctionxhanoiblog/issues/new) labelled `translation` with a link in description to the original post on [our repo](https://github.com/junctionxhanoiblog/junctionxhanoiblog).
We will connect with the original author and help you obtain their permission 👌👌.

##### Setting up local env

Start by forking this repository and then clone it recursively to your local workspace

```bash
git clone https://github.com/YOUR-USERNAME/junctionxhanoiblog --recursive
cd junctionxhanoiblog/
```

Check if you have [hugo](https://gohugo.io) installed by running `hugo version`.
If you haven't already installed [hugo](https://gohugo.io), please follow the instruction on [their site](https://gohugo.io/getting-started/installing/).

##### Create the post in target language

Identify the post's ID by locating what the containing folder name is (i.e. if the path to markdown file is `/content/posts/example/index.md` then the post's ID is `example`).
Create the post in target language with the following command after identifying target language's key from [our config file](https://github.com/junctionxhanoiblog/junctionxhanoiblog/blob/master/config.yaml) (i.e. `vi` for Viet)

```bash
# For English as target language, there's no need for language key
# as English is the default language
hugo new posts/<POST-ID>/index.<LANGUAGE-KEY>.md
```

Fill in all the necessary fields:

- title: translation from original post
- date: must be in [ISO-8601 format](https://en.wikipedia.org/wiki/ISO_8601), [this timestamp generator](https://timestampgenerator.com/) might come handy for such.
- authors: A collection (array) of post authors' full/pen names. For fancy authors' profiles, head down to [bonus section](#bonus)
- cover: same as original post's
- tags: same as or translated from original post's
- keywords: same as or translated from original post's
- description: translation from original post
- showFullContent: please keep this as false to share blog's estate with other authors

Start the post with link to original post and attribution to the original author.
For example, your translated post can be started with "This post was translated from [our example post](/posts/example) by Do Hoang".

Write your blog post in markdown with an enhanced flavor from [hugo](https://gohugo.io/).
If you are intending to do more than just standard mardown (md), checkout [hugo docs](https://gohugo.io/content-management/) to learn more.

##### Letting us know 🎉🎉

After you are done with your post, please open a [Pull Request](https://github.com/junctionxhanoiblog/junctionxhanoiblog/compare) labelled `post` and `translation` on our repository and your post will be up in no time. 🥳🥳

### <a name="bonus" id="bonus"></a> III. Bonus: Fancy author profile

This section is for anyone who's looking for a fancier `Author` profile page rather than just a page with your list of posts when readers click on your post's author name.

Create an author data for yourself, we recommend using your Github handle as an identifier for consistency and to avoid collision among our contributors

```bash
touch data/authors/YOUR-USERNAME.yaml
```

There are 3 fields that you can provide in your author data file:

- name: self-explanatory 😁😆
- img: your profile picture (also use your Github handle for naming), can be put inside `/static` folder and referred from root of JunctionXHanoi site (i.e. location `/static/dohoang.jpg`, referred as `/dohoang.jpg` in author data file)
- url: link to your online profile
- bio: short intro of yourself, please keep it under 100 characters

Use the corresponding identifier for the values in `authors` field of your post. (i.e., my author data file is `dohoang.yaml` then my post's `authors` field should include `dohoang`)

### <a name="question" id="question"></a> IV. Doubts and questions

Please shoot us [a new issue](https://github.com/junctionxhanoiblog/junctionxhanoiblog/issues/new) labelled `question` on [our repo](https://github.com/junctionxhanoiblog/junctionxhanoiblog).