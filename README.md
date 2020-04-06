# README

## Todo
* Fix About page
* Change color
* Add own categories and content
* Change make.ipynb to make.py
* Add .gifs and LaTeX work
* Consider some [Hugo Maitenance](https://discourse.gohugo.io/t/advice-needed-regarding-hugo-dev-environment-on-mac/10156/12)

## Learnings
* Must add `_index.md` in every folder where content (i.e. example.md) exists
* Must change `.Page` iteration according to [ADVICE](https://discourse.gohugo.io/t/subsubfolders-in-chris-albon-theme/24472)
* Can add images to markdown files with `![png](images/page.jpg)`
* Can change publish directory with `publishDir="../ericpena.github.io"`
* Stay Oganized!

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