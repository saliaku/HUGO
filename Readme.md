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

## Step 3: Choose a Theme
1. Explore themes from the [Hugo themes directory](https://themes.gohugo.io/).
2. Follow the documentation of your chosen theme to install it into your Hugo site.
3.Here we are using this command to install the ananke theme to the themes folder

```bash
    git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
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

3. Set the source branch to `master` or `main`, depending on your repository's default branch.

## Conclusion
Your Hugo website is now hosted on GitHub Pages! You can further customize your site, add more content, and update it easily by rebuilding your site with Hugo and pushing changes to GitHub.


