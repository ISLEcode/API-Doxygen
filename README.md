## API Doxygen

**API Doxygen** is a customised version of [Documentor][insdocu] — it is intended to be used in with [API Designer][designer] and
[API Swagger][swagger]. Akin to Postman's [Documenter][postdoc] but for [API-Designer][designer] (i.e. [Insomnia]), it is based on
[Svelte] — the «&nbsp;cybernetically enhanced&nbsp;» application framework, to automagically generate your API documentation
:smile:.

<details>
<summary><b>Objectives</b></summary>
---

All credits for this software goes to its original authors. Customisations here intend to:

  - Transform into a GitHub template
  - Automate the build through a Makefile and GitHub Actions
  - Reduce the (numerous) dependencies
  - And probably migrate to SveleKit

**Important**: We focus on macOS and Linux — stick with [Documentor][insdocu] if you are on Windows.

</details>

<details>
<summary><b><u>Requirements</u></b></summary>

* Node.js (8.x or higher is recommended)
* An exported Insomnia workspace JSON (v4)

</details>
<details>
<summary><b><u>Getting started</u></b></summary>

Install configuration file

```sh
npx insomnia-documenter --config /path/to/insomnia/config.json
```

</details>
<details>
<summary><b><u>Options</u></b></summary>

```
Options:
  -c, --config <location>  Location of the exported Insomnia JSON config.
  -l, --logo <location>    Project logo location (48x48px PNG).
  -o, --output <location>  Where to save the file (defaults to current working directory).
  -h, --help               output usage information
```

</details>
<details>
<summary><b><u>Using a GitHub release</u></b></summary>

Alternatively, you can start using Insomnia Documenter by downloading a release archive from [GitHub](https://github.com/jozsefsallai/insomnia-documenter/releases) and adding your `insomnia.json` export file to the root directory of your site.

</details>
<details>
<summary><b><u>Updating the API</u></b></summary>

Updating the API is super simple! Since Insomnia Documenter is a plug-and-play web app, you can just replace your `insomnia.json` with your new exported JSON file. Just make sure it's called `insomnia.json`.

The same actually applies to the logo as well (`logo.png`).

</details>
<details>
<summary><b><u>Custom API path</u></b></summary>

Maybe you want to document multiple APIs on the same domain? Perhaps you want to host your documentation page on GitHub pages? In this (any many other cases), you will need to specify what the root path is. To do this, you have to open `index.html` and replace the following line:

```html
<div id="app"></div>
```

with something like this:

```html
<div id="app" data-root="/path/to/docs"></div>
```

In this case, the app will pick up the `insomnia.json` file from the `/path/to/docs` directory. This gives you more flexibility over how you want to maintain your documentation page (for example, you can store the export file somewhere other than the root directory of the webpage). You should NOT put a trailing slash in the `data-root` property.

Please note that setting this attribute will not affect the favicon and the logo of the page. They will still be loaded from the same directory where `index.html` is.

</details>

## Running the Page Locally

Opening the `index.html` file will fail to load in 99.9% of cases because that's just how fetch works. To preview the page locally, you might want to use a tool such as [zeit/serve](https://github.com/zeit/serve):

```sh
npx serve
```

The page will be available at http://localhost:5000.

## Insomnia Plugin

[devhammed](https://github.com/devhammed) has made an awesome Insomnia Plugin that allows you to generate a documentation page directly from Insomnia's interface. **[Get The Plugin](https://insomnia.rest/plugins/insomnia-plugin-documenter)** ([npm](https://www.npmjs.com/package/insomnia-plugin-documenter) - [github](https://github.com/devhammed/insomnia-plugin-documenter))

## Changelog

Please see the [Changelog document](https://github.com/jozsefsallai/insomnia-documenter/blob/master/CHANGELOG.md).

## Contribution

The CLI tool is a commander applet, while the frontend itself is a Svelte app. This project is still in beta, which means it has bugs and can be improved here and there. Contribution is most welcome :)

**Clone the repository:**

```sh
git clone git@github.com:jozsefsallai/insomnia-documenter.git
cd insomnia-documenter
```

**Install the dependencies:**

```sh
npm install
```

**Copy the demo Insomnia export file:**

```sh
cp demo/insomnia.json public/insomnia.json
```

**Run a development build with hot reload:**

```sh
npm run dev
```

**Create a production build:**

```sh
npm run build
```

**Linting:**

```sh
npm run lint
```

**Testing:**
```sh
npm run test
```

## License

MIT.

*Note: this project is not affiliated with Kong and/or Insomnia.*

## Insomnia Documenter for enterprise

Available as part of the Tidelift Subscription

The maintainers of Insomnia Documenter and thousands of other packages are working with Tidelift to deliver commercial support and maintenance for the open source dependencies you use to build your applications. Save time, reduce risk, and improve code health, while paying the maintainers of the exact dependencies you use. [Learn more.](https://tidelift.com/subscription/pkg/npm-insomnia-documenter?utm_source=npm-insomnia-documenter&utm_medium=referral&utm_campaign=enterprise&utm_term=repo)

[insdocu]:      https://github.com/jozsefsallai/insomnia-documenter
[designer]:     https://github.com/ISLEcode/API-Designer
[doxygen]:      https://github.com/ISLEcode/API-Doxygen
[swagger]:      https://github.com/ISLEcode/API-Swagger
[postdoc]:      https://www.getpostman.com/api-documentation-generator
[insomnia]:     https://insomnia.rest
[svelte]:       https://svelte.dev
