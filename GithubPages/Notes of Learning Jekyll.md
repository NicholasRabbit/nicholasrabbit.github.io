### Notes of Step by Step Tutorial

#### Liquid

1. `{{}}` represents an object in Jekyll.

#### Front Matter 

1. Note that the "Front Matter" is written in the original file, such as `root/index.htm.`, but not the generated file in `_site`.  When `jekyll serve` is executed, the original file will have been generated a new file in `_site` to replace the old one.
2. You must populate "Front Matter" to your file if you want to use "Liquid Tags" in Jekyll.

#### 4. Layouts

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

After configuring the default layout for pages by categories, we can remove the layout from front matters of all pages. 

#### 7. Assets

1. Don't key words with spelling error!!

2. There is an forward slash before `/assets/`

```html
<!--It is stylesheet NOT stytlesheet-->
<link rel="stylesheet" href="/assets/css/styles.css">
```

3. Import multiple CSS files in `assets/css/styles.scss`from `_sass/` 

   ```scss
   ---
   ---
   @import "main";
   @import "layout";
   ```

   `main.scss` and `layout.scss` are in `_sass/`

   

#### 9. Collections

(1) N.B. In order to list all the posts of an author, the author's name in the front matter of a post should be as same as the `short_name` in the front matter of the page of this author's information.  For example, 

`_posts/2025-04-06-A post`

```html
---
author: nick
---
```

`_authors/nicholas.md` (The page of an author's information)

```html
---
short_name: nick
---
```

How to connect them? 

Read the document of this chapter. 

### Others 

#### Permalinks

"permalink" allows us to customise the URL for a page; the URL can be different from the page's name.

(1) As an illustration, if you want the URL of `/my_pages/about-me.html` to be `/about/`, you should set the it to the value of `permalink` in the front matter of the page. 

```markdown
---
permalink: /about/
---
```

(2) Another example is that I can set front matter in my `_pages/about.md`  and add URL in `_data/navigation.yml` , so that the "About" can be accessed. 

`_pages/about.md`

```markdown
---
layout: single
permalink: /about/
title: About 
---
```

`_data/navigation.yml`

```yaml
# main links
main:
  - title: "About"
    url: /about/
```

