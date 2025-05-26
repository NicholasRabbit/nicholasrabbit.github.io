### Notes of Step by Step Tutorial

#### Liquid

1. `{{}}` represents an object in Jekyll.

#### Front Matter 

1. Note that the "Front Matter" is written in the original file, such as `root/index.htm.`, but not the generated file in `_site`.  When `jekyll serve` is executed, the original file will have been generated a new file in `_site` to replace the old one.
2. You must populate "Front Matter" to your file if you want to use "Liquid Tags" in Jekyll.

#### Layouts

1. If the `About.html` is not included in the homepage, you should enter `http:...9090/about.html` to visit it.

### Assets

1. Don't key words with spelling error!!

2. There is an forward slash before `/assets/`

```html
<!--It is stylesheet NOT stytlesheet-->
<link rel="stylesheet" href="/assets/css/styles.css">
```

