# Docbox

[![Circle CI](https://circleci.com/gh/mapbox/docbox.svg?style=svg)](https://circleci.com/gh/mapbox/docbox)

**Docbox is an open source version of Mapbox's REST API documentation system.** It takes structured Markdown files and generates a friendly two-column layout with navigation, permalinks, and examples. The documentation source files that Docbox uses are friendly for documentation authors and free of presentational code: it's Markdown.

[![](https://farm2.staticflickr.com/1619/25089476199_5fc31f69df_o.png)](https://circle-artifacts.com/gh/mapbox/docbox/4/artifacts/0/tmp/circle-artifacts.8gUjTxc/index.html#delete-a-wobble)

_[Demo documentation](https://circle-artifacts.com/gh/mapbox/docbox/4/artifacts/0/tmp/circle-artifacts.8gUjTxc/index.html)_

**Docbox is a JavaScript application written with React.** The core magic is thanks to the [remark](http://remark.js.org/) Markdown parser, which enables the layout: after parsing a file into an [Abstract Syntax Tree](https://en.wikipedia.org/wiki/Abstract_syntax_tree), we can move examples to the right, prose to the left, and build the navigation system.

**It has a supercharged test suite**. Our tests check for everything from broken links to invalid examples and structure problems: this way, the application is only concerned with output and you can proactively enforce consistency and correctness. We even extract JavaScript examples from documentation and test them with [eslint](http://eslint.org/)

**When you're ready to ship**, Docbox's `build` task minifies JavaScript and uses React's server rendering code to make documentation indexable for search engines and viewable without JavaScript.

_Docbox is a [Mapbox](http://mapbox.com/) community open source project. We built an awesome system for our REST API documentation and wanted to share it with you. Not a Mapbox product, so there's no guaranteed support and may have some rough edges._

## Writing Documentation

Documentation is written as Markdown files in the `content` directory, and is organized by the `src/content.js` file - that file requires each documentation page and puts them in order. This demo has a little bit of content - [content/example.md](content/example.md) and [content/introduction.md](content/introduction.md), so that there's an example to follow.

## Development

We care about the ease of writing documentation. Docbox comes with batteries included: after you `npm install` the project, you can run `npm start` and its development server, [budo](https://github.com/mattdesl/budo), will serve the website locally and update automatically.

To run the site locally:

1. Clone this repository
	2. `git clone https://github.com/mapbox/docbox.git`
2. `npm install`
3. `npm start`
4. Open http://localhost:9966/

## Tests

Tests cover both the source code of Docbox as well as the content in the `content/` directory.

To run tests:

1. Clone this repository
	2. `git clone https://github.com/mapbox/docbox.git`
2. `npm install`
3. `npm test`


## Deployment

The `npm run build` command builds a `bundle.js` file that contains all the JavaScript code and content needed to show the site, and creates an `index.html` file that already contains the site content. Note that this _replaces_ the existing `index.html` file, so it's best to run this only when deploying the site and to undo changes to `index.html` if you want to keep working on content.

1. Clone this repository
	2. `git clone https://github.com/mapbox/docbox.git`
2. `npm install`
3. `npm run build`

---

Props to [Tripit's Slate project](https://github.com/tripit/slate), which served
as the inspiration for Docbox's layout.
