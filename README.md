# Crypto.com Chain's documentation

The documentation in this repository site is meant to provide specifications and implementation details that will be useful to third party developers or contributors to the main repository.

## Getting Started

### Prerequisites

You're going to need:

- **NPM**
- **Oracle JDK** (For generating the pdf, deployment needs this)

### Getting Set Up

1. Fork this repository on Github
2. Clone your forked repository (not our original one) to your hard drive with `git clone https://github.com/YOURUSERNAME/chain-docs.git`
3. `cd chain-docs`
4. Initialize and start chain-docs.

```bash
npm install
cd docs
vuepress dev
```

You can now see the docs at [http://localhost:8080](http://localhost:8080).

## Adding new page to the doc

1. Create a markdown file under `/docs/getting-started/`
2. Open `/docs/.vuepress/config.js`
3. Add the file name to `sidebar` and the `ordering` under `vuepress-plugin-export` in plugins

``` diff
module.exports = {
  ...,

  themeConfig: {
    ...,

    sidebar: {
      '/getting-started/': [
        '',
        ...,
+        '[Add_Your_New_File_Name_Here]'
        ...
      ]
    }
  },
  ...,

  plugins: [
    ['vuepress-plugin-export',
    {
      sorter: function(a,b){
        var ordering = {
          'Home': 0,
          ...,
+         '[Add_Your_New_File_Name_Here]': [Add_The_Number_You_Want_The_Page_Be_Ordered]
          ...,
        };
        ...
      }
    }
    ]
  ]
}
```

## Generating a PDF version of the site

Go to ``chain-docs/docs``, then run:

```bash
vuepress export
```

a PDF version of the site will be generated under the ``/docs`` path.

## Deploying Chain-doc to Github Pages

1. Make sure you're working on a fork in your own account, not our original respository: `git remote show origin`
2. Commit your changes: `git commit -a -m "YOUR MESSAGE"`
3. Push the changes to GitHub: `git push`
4. Run `./deploy.sh`

You should see your updates on [http://yourusermame.github.io/chain-docs](http://yourusermame.github.io/chain-docs).
