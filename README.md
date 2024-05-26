# paper-airplanes

Creative project in Three.js with 3D paper airplanes

## Making this project from scratch

1. Create a GitHub repository
2. Clone the repository
3. Create the project with Node and Vite

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
