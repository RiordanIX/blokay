# Blokay
## Blogging SSG using shell templates using pp

An easy blogging ssg that allows embedding shell scripts into your blog.

## Usage
Type `./blokay` without any arguments to bring up a usage display.

## Embedding shell scripts

Example embedding shell scripts into html docs:
```
Here's a list of my html files:
<ul>
#!
for x in `ls -1 *.html`
do
#!
<li>$x</li>
#!
done
#!
</ul>
```

### Markdown
My recommended markdown to html parser is [`md4c`][md4c]. An example to easily
use it using `pp` is as follows:
```
<h1>HTML here</h1>
...
#!
echo "
# My markdown

This is some markdown that is embedded in a file that will be parsed by `pp`.
You could also make a separate file and give it to `md2html`, that way it'd be
easier to get syntax highlighting in your favorite editor, you'd just need to
make sure you manage your files in a nice way.
" | md2html -
#!
Continue writing whatever else
```

## `pp`
[`pp`][pp] is a preprocessor that allows embedding shell scripts in any code. Blokay
is using it for html files, but it has many more use cases than that. It's
included in this repo because it's small, simple, and required for this blokay
to work. Any shell commands must be inside of `#!` blocks.

| :memo: | Be careful with using `"` inside a file, `pp` uses them during operation |
|--------|--------------------------------------------------------------------------|


### `pp` installation
`make bin/Makefile && make install bin/Makefile`

[pp]: https://mkws.sh/pp.html
[md4c]: https://github.com/mity/md4c
