# paper-airplanes

Creative project in Three.js with 3D paper airplanes

## Making this project from scratch

1. Create a GitHub repository
2. Clone the repository
3. Create the project with Node and Vite
4. Create a placeholder web page
5. Test Vite dev setup
6. Setup GitHub Pages
7. Add JavaScript
8. Add the Three.js dependency
9. Add build steps for GitHub Pages

### Create a GitHub repository

Go to github.com/new to create a repository for the project.

Give the repository a name in kebab case. It's worth a bit of thought, because the name of the project will be part of the URL for the web page. Don't get frozen; the name of the repository can be changed.

I like to start the project with a readme, .gitignore and the MIT license.

Writing a modest description and some notes in the readme will help developers in the future understand the project. You may be your own "future" developer.

The Node .gitignore is a reasonable choice for a web project. The template is a bit heavy-handed, but it covers build and dependency folders well. There is no reason to push a ton of extra baggage to cloud.

I use the MIT license. It was recommended in a previous workplace. The company required using GitHub, suggested public open-source and recommended the MIT license. I just went with it.

### Clone the repository

Open GitHub Desktop and clone the repository. That is, make a copy on your computer.

GitHub Desktop makes simple repository management intuitive.

### Create the project with Node and Vite

Open the terminal and navite to the project folder. Initialize the project by running

``` Terminal
npm init -y
```

Install Vite by running

``` Terminal
npm install vite
```

Update package.json. Change the license to MIT. Replace the scripts: test with dev and build.

``` JSON
{
  ...
  "scripts": {
    "dev": "vite",
    "build": "vite build"
  },
  ...
  "license": "MIT",
  ...
}
```

### Create a placeholder web page

Create a new ```index.html``` file. Tip: in VS Code type an exclamation point (!) and then tab-complete it.

``` HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

The content of the file is less important than checking that Vite is ready to go. We are in the "hello world" stage of the project.

### Test Vite dev setup

From the teminal, start the development server: ```npm run dev```. Once the server is started, enter 'o' to open the browser. An new browser tab should open with a blank page.

In ```index.html```, add some text (e.g., Hi.) to the body and save. The text should appear on the web page.

### Setup GitHub Pages

From the repository page on github.com, open the Settings > Pages tab. Select GitHub Actions for the build and deployment source. Choose "Static HTML", click Configure. The YAML file for the GitHub Actions deployment is shown. Click the green Commit changes button; and commit to the main branch.

Open the Actions tab. There should be a workflow run for our commit "Create static.yml" Click on the link for the workflow run "Create static.yml". There should be one card "deploy" for the job in our YAML script.

Click the link on the "deploy" card to open the newly published web page.

NB: since this was done in on the GitHub site, you will need to pull from GitHub to your local version to synchronize your work.

### Add JavaScript

Add a ```script.js``` to the project.

``` JavaScript
document.body.innerText = 'Scripting.'
```

Update ```index.html```.

``` HTML
...
    Hi.
    <script type="module" src="script.js"></script>
</body>
</html>
```

### Add the Three.js dependency

From the terminal install three.js

``` Terminal
npm install three
```

Check that Three.js in available. Replace the code in ```script.js``` with the following.

``` JavaScript
import * as THREE from 'three'

document.body.innerText = `THREE.REVISION: ${THREE.REVISION}`
```

### Add build steps for GitHub Pages

The last deployment won't have quite worked. The initial page text will not have been changed to show the THREE.REVISION

Update ```static.yml``` to include Install and Build steps. Also change the path to ```dist```.

``` YAML
...
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Install
        run: npm ci
      - name: Build
        run: npm run build
      - name: Setup Pages
        uses: actions/configure-pages@v5
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: dist
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

The Install step uses ```npm ci``` "clean install".

> This command is similar to npm install, except it's meant to be used in automated environments such as test platforms, continuous integration, and deployment -- or any situation where you want to make sure you're doing a clean install of your dependencies.

npm Docs - <https://docs.npmjs.com/cli/v10/commands/npm-ci>
