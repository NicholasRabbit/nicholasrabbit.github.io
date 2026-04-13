### Notes of Step by Step Tutorial

#### Liquid

1. `{{}}` represents an object in Jekyll.

#### Front Matter 

1. Note that the "Front Matter" is written in the original file, such as `root/index.htm.`, but not the generated file in `_site`.  When `jekyll serve` is executed, the original file will have been generated a new file in `_site` to replace the old one.
2. You must populate "Front Matter" to your file if you want to use "Liquid Tags" in Jekyll.

#### Layouts

1) How to use "layout" ? 

First of all, we should create a template which can be used any page in our site. As an illustration, create a `default.html` as a template. Then it can be imported in from the "front matters". 

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {{ content }}
  </body>
</html>
```

Import the `default.html`  in the following `index.html`. 

```html
---
layout: default
title: Home
---
<h1>{{ "Hello World!" | downcase }}</h1
```

2)  We can create templates in `_layouts`  such as `author.html`, `post.html` and `default.html` and import them in different collections. If we don't want to import one "layout" page every time when creating a new page, for example, we want to use `author.html` for all the author's page in the directory `_authors`, we can achieve this goal by using front matter defaults in `_config.yml`.

```yaml
collections:
  authors:
    output: true

defaults:
  - scope:
      path: ""
      type: "authors"  # "authors" is the directory "_authors" without the underscore. 
    values:
      layout: "author"
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
  - scope:
      path: ""
    values:
      layout: "default"
```



### Assets

1. Don't key words with spelling error!!

2. There is an forward slash before `/assets/`

```html
<!--It is stylesheet NOT stytlesheet-->
<link rel="stylesheet" href="/assets/css/styles.css">
```

