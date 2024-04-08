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

## Step 2: Create a New Hugo Site
1. Open your terminal or command prompt.
2. Run the following command to create a new Hugo site:
    hugo new site <your_site_name>


## Step 3: Choose a Theme
1. Explore themes from the [Hugo themes directory](https://themes.gohugo.io/).
2. Follow the documentation of your chosen theme to install it into your Hugo site.

## Step 4: Add Content
1. Navigate to the `content` directory of your Hugo site.
2. Create Markdown or HTML files to add your content (e.g., pages, blog posts).

## Step 5: Configure Site Settings
1. Modify the `config.toml` or `config.yaml` file in your Hugo site's root directory.
2. Configure settings such as site title, description, and other options specific to your site and chosen theme.

## Step 6: Build Your Site
1. Run the following command to generate the static files for your site:


## Step 7: Set Up a GitHub Repository
1. Create a new repository on GitHub.
2. Initialize it with a README.md file.
3. Ensure the repository name matches your GitHub username (e.g., `<username>.github.io`) to enable GitHub Pages.

## Step 8: Push Your Site to GitHub
1. Add your GitHub repository as a remote origin:
    git remote add origin <repository_url>
2. Add all files, commit, and push to GitHub:
    git add .
    git commit -m "Initial commit"
    git push -u origin master


## Step 9: Enable GitHub Pages
1. Go to your repository's settings on GitHub.
2. Navigate to the "Pages" section.
3. Set the source branch to `master` or `main`, depending on your repository's default branch.

## Conclusion
Your Hugo website is now hosted on GitHub Pages! You can further customize your site, add more content, and update it easily by rebuilding your site with Hugo and pushing changes to GitHub.


