
## Bug reproduction

1. Create web component scaffolding with demoing
    ```sh
    $ npm init @open-wc
    # web component scaffolding > demoing
    ```
2. Add a public statics assets folder and use it in a story
    ```sh
    $ mkdir public
    # I coppied kitten.jpg in public/kitten.jpg
    ```

    On `index.stories.mdx` I added:
    ```md
    ## Kitten image
    <img src="public/kitten.jpg"/>
    ```
3. Start storybook
    ```sh
    $ npm run storybook
    > start-storybook --node-resolve --watch --open
    ```
    It works!  🎉

4. Build storybook
    ```sh
    $ npm run storybook:build
    > build-storybook -s public
    ```
    It doesn't work  `/public` folder is not copied. The `-s` flag shouldn't even be needed because `/public` is the default static folder. The kitten image throws a 404 error when serving `/storybook-static`

5. Not elegant solution for now
    In `pakage.json`
    ```json
    "poststorybook:build": "cp -R public storybook-static/public"
    ```
    I'm sure something similar can be done ad-hoc for rollup config too. However this shouldn't be needed.

# \<demo-static-files-bug>

This webcomponent follows the [open-wc](https://github.com/open-wc/open-wc) recommendation.

## Installation
```bash
npm i demo-static-files-bug
```

## Usage
```html
<script type="module">
  import 'demo-static-files-bug/demo-static-files-bug.js';
</script>

<demo-static-files-bug></demo-static-files-bug>
```

## Demoing with Storybook
To run a local instance of Storybook for your component, run
```bash
npm run storybook
```

To build a production version of Storybook, run
```bash
npm run storybook:build
```


## Local Demo with `es-dev-server`
```bash
npm start
```
To run a local development server that serves the basic demo located in `demo/index.html`

```bash
npm start:compatibility
```
To run a local development server in compatibility mode for older browsers that serves the basic demo located in `demo/index.html`

