# eleventy-plugin-syntaxhighlight

A pack of [Eleventy](https://github.com/11ty/eleventy) plugins for syntax highlighting using the Liquid templating engine. No runtime JavaScript here, these highlight transformations are all done at build-time.

## Installation

Available on [npm](https://www.npmjs.com/package/@11ty/eleventy-plugin-syntaxhighlight).

```
npm install @11ty/eleventy-plugin-syntaxhighlight --save
```

Open up your Eleventy config file (probably `.eleventy.js`) and use `addPlugin`:

```
const syntaxHighlight = require("@11ty/eleventy-plugin-syntaxhighlight");
module.exports = function(eleventyConfig) {
  eleventyConfig.addPlugin(syntaxHighlight);
};
```

If you use the Prism version, you are responsible for including [your favorite theme CSS](https://github.com/PrismJS/prism-themes)!

[Read more about Eleventy plugins.](https://github.com/11ty/eleventy/blob/master/docs/plugins.md)

## Usage

### Supplies: Two Liquid Tags

* `{% highlight %}`: syntax highlights a block of code using PrismJS.
* `{% highlight-plain %}`: adds `<pre><code>` around a block of code and offers the line-highlighting feature set as `highlight`.

### Prism Syntax Highlighter

```
{% highlight js %}
function myFunction() {
  return true;
}
{% endhighlight %}
```

```
// Line highlighting classes (single highlight)
// Adds `highlight-line-active` class to lines 1,3,5 (for line highlighting)
{% highlight js 1,3-5 %}
function myFunction() {
  // …
  return true;
}
{% endhighlight %}
```

```
// Line highlighting classes (add and remove)
// Adds `highlight-line-add` class to lines 1,3
// Adds `highlight-line-remove` class to lines 5,6,7,8
{% highlight js 1,3 5-8 %}
function myFunction() {
  // …
  return true;
}
{% endhighlight %}
```

### Plain Code Block

No syntax highlighting here but you do get the line highlighting features shown in the Prism examples above.

```
{% highlight-plain js %}
```

```
{% highlight-plain js 1,3-5 %}
```

```
{% highlight-plain js 1,3 5-8 %}
```
