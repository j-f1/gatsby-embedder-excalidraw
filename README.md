# gatsby-embedder-excalidraw

This custom transformer for [`gatsby-remark-embedder`](https://github.com/MichaelDeBoey/gatsby-remark-embedder) allows you to embed Excalidraw diagrams in Markdown content simply by pasting an Excalidraw link in the source.

The code for this library is lifted from [this file](https://github.com/excalidraw/excalidraw-blog/blob/master/src/gatsby-embedder-excalidraw/index.js) in the [`excalidraw-blog`](https://github.com/excalidraw/excalidraw-blog) Gatsby site. All credit for this transformer goes to those authors. I was inspired to do this when I saw [Alex Luong's tweet](https://twitter.com/alex__luong/status/1257909443112497153) about making this functionality into a `gatsby-remark-excalidraw` plugin.

- [Installation](#installation)
- [Usage](#usage)
- [Example](#example)
  - [Install dependencies](#install-dependencies)
  - [Configure plugins](#configure-plugins)
  - [Create a drawing](#create-a-drawing)
  - [Embed your drawing](#embed-your-drawing)
- [License](#license)

## Installation

```bash
npm install gatsby-embedder-excalidraw
```

## Usage

```js
// gatsby-config.js
module.exports = {
  plugins: [
    {
      resolve: 'gatsby-transformer-remark',
      options: {
        plugins: [
          {
            resolve: 'gatsby-remark-embedder',
            options: {
              customTransformers: [require('gatsby-embedder-excalidraw')]
            }
          }
        ]
      }
    }
  ]
};
```

## Example

This guide will show you how to get up and running with `gatsby-embedder-excalidraw` in the fewest steps possible. It uses `gatsby-plugin-mdx` to take advantage of its awesome default behaviour of automatically creating pages based on MDX files in `src/pages`.

### Install dependencies

First, install `gatsby` and its dependencies:

```bash
npm install gatsby react react-dom
```

Next, install `gatsby-plugin-mdx` and its dependencies:

```bash
npm install gatsby-plugin-mdx @mdx-js/mdx @mdx-js/react
```

### Configure plugins

Add `gatsby-plugin-mdx` to your Gatsby config:

```js
// gatsby-config.js
module.exports = {
  plugins: [
    {
      resolve: 'gatsby-plugin-mdx'
    }
  ]
};
```

Install the `gatsby-remark-embedder` plugin and this Excalidraw transformer `gatsby-embedder-excalidraw`:

```bash
npm install gatsby-remark-embedder gatsby-embedder-excalidraw
```

Add `gatsby-remark-embedder` as a Gatsby remark plugin for `gatsby-plugin-mdx`. In your `gatsby-remark-embedder` options, add `gatsby-embedder-excalidraw` as a custom transformer:

```diff
// gatsby-config.js
module.exports = {
  plugins: [
    {
-     resolve: 'gatsby-plugin-mdx'
+     resolve: 'gatsby-plugin-mdx',
+     options: {
+       gatsbyRemarkPlugins: [
+         {
+           resolve: 'gatsby-remark-embedder',
+           options: {
+             customTransformers: [require('gatsby-embedder-excalidraw')]
+           }
+         }
+       ]
+     }
    }
  ]
};
```

### Create a drawing

Head over to [Excalidraw](https://excalidraw.com) and draw something! Once you're satisfied, you can find a shareable link to your drawing in the export dialog, accesible from the icon in the top left corner of the page.

![link](link.gif)

### Embed your drawing

Create an MDX page at `src/pages/index.mdx` and add a link to an Excalidraw diagram:

```markdown
# Fox grab flowchart

Fox's followups after a grab depend on your opponent's DI:

https://excalidraw.com/#json=5695519967936512,sLhjTgn1_wB1iVLLquX6Fg
```

Voila! 🎉 https://excalidraw-embed.trevorblades.com

## License

[MIT](./LICENSE)
