# README

## Todo
* Fix About page
* Change color
* Add own categories and content
* Change make.ipynb to make.py
* Add .gifs and LaTeX work
* Consider some [Hugo Maitenance](https://discourse.gohugo.io/t/advice-needed-regarding-hugo-dev-environment-on-mac/10156/12)

Theme code update: index.html
```html
<ul>
    {{ $section := site.GetPage "machine_learning/basics" }}
    {{ with $section }}
        {{ range .Pages }}
        <li><a href="{{.Permalink}}">{{.Title}}</a></li>
        {{ end }}
    {{ end }}
</ul>
```

## License
[MIT](https://choosealicense.com/licenses/mit/)