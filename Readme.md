# Creating a Website with Hugo and Hosting on GitHub Pages

## Introduction
In this guide, we'll walk through the process of creating a website using Hugo, a static site generator, and hosting it through GitHub Pages.

### Prerequisites
Before we begin, ensure you have the following:
- Basic knowledge of the command line.
- A GitHub account.

## Step 1: Install Hugo
1. Download Hugo from the [official releases page](https://github.com/gohugoio/hugo/releases).
2. Follow the installation instructions for your operating system. 
3. Verify that you have installed latest version of Hugo
```bash
    hugo version
```

### Step 2: Create a New Hugo Site

1. Open your terminal or command prompt.
2. Run the following command to create a new Hugo site:
```bash
    hugo new site <your_site_name>
```
3. Move into the folder created
```bash
  cd <your_site_name>
```

A similar directory structure will be created:

```
my-site/
├── archetypes/
│   └── default.md
├── assets/
├── content/
├── data/
├── layouts/
├── public/
├── resources/
├── static/
├── themes/
└── config.toml         <-- site configuration
```

<!-- 
1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
-->

## Step 7: Initialize the Github repository
1. Create a Github repository.
2. Add your GitHub repository as a remote origin:
```bash
    git init
    git add .
    git commit -m "first commit"
    git branch -M main
    git remote add origin git@github.com:saliaku/happy_website.git
    git push -u origin main
```


## Step 3: Choose a Theme
1. Explore themes from the [Hugo themes directory](https://themes.gohugo.io/).
2. Follow the documentation of your chosen theme to install it into your Hugo site.
3.Here we are using this command to install the ananke theme to the themes folder

```bash
    git clone https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
```
4. Add this line to the config.toml file, to define the theme that is going to be used for your website. You can use any theme that you prefer. 
```bash
echo "theme = 'ananke'" >> config.toml
```
5. Now you are ready to run your hugo website in localhost. Press Ctrl + C to stop Hugo’s development server.
```bash
    hugo server
```

## Step 4: Add Content
1. Navigate to the `content` directory of your Hugo site.
2. Create Markdown or HTML files to add your content (e.g., pages, blog posts).

## Step 5: Configure Site Settings
1. Modify the `config.toml` or `config.yaml` file in your Hugo site's root directory.
2. Configure settings such as site title, description, and other options specific to your site and chosen theme.

## Step 6: Build Your Site
1. Run the following command to generate the static files for your site:
```bash
    hugo
```
    or
```bash
    hugo -d /path/to/your/directory
```


## Step 7: Push Your Site to GitHub
1. Create a Github repository.
2. Add your GitHub repository as a remote origin:
```bash
    git remote add origin <repository_url>
```
3. Add all files, commit, and push to GitHub:
```bash
    git add .
    git commit -m "Initial commit"
    git push -u origin main
```
## Step 8: Enable GitHub Pages
1. Go to your repository's settings on GitHub.
2. Navigate to the "Pages" section. In the center of your screen you will see this:
![My Image0](https://gohugo.io/hosting-and-deployment/hosting-on-github/gh-pages-1.png)
3. Change the Source to GitHub Actions. The change is immediate; you do not have to press a Save button.
![My Image1](https://gohugo.io/hosting-and-deployment/hosting-on-github/gh-pages-2.png)
4. Create an empty file in your local repository.
```bash
.github/workflows/hugo.yaml
```
5. Copy and paste the YAML below into the file you created. Change the branch name and Hugo version as needed.
```bash
# Sample workflow for building and deploying a Hugo site to GitHub Pages
name: Deploy Hugo site to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches:
      - main

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

# Default to bash
defaults:
  run:
    shell: bash

jobs:
  # Build job
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.124.0
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb          
      - name: Install Dart Sass
        run: sudo snap install dart-sass
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive
          fetch-depth: 0
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v4
      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
      - name: Build with Hugo
        env:
          # For maximum backward compatibility with Hugo modules
          HUGO_ENVIRONMENT: production
          HUGO_ENV: production
        run: |
          hugo \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"          
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

6. Commit the change to your local repository with a commit message of something like “Add workflow”, and push to GitHub.
7. From GitHub’s main menu, choose Actions. You will see something like this:
![My Image2](https://gohugo.io/hosting-and-deployment/hosting-on-github/gh-pages-3.png)
8. When GitHub has finished building and deploying your site, the color of the status indicator will change to green.
![My Image3](https://gohugo.io/hosting-and-deployment/hosting-on-github/gh-pages-3.png)
9.Click on the commit message as shown above. You will see this:
![My Image4](https://gohugo.io/hosting-and-deployment/hosting-on-github/gh-pages-5.png)

Under the deploy step, you will see a link to your live site.

In the future, whenever you push a change from your local repository, GitHub will rebuild your site and deploy the changes.

## Conclusion
Your Hugo website is now hosted on GitHub Pages! You can further customize your site, add more content, and update it easily by rebuilding your site with Hugo and pushing changes to GitHub.


