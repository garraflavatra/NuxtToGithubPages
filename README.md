# Build a Nuxt.js site and deploy it to Github Pages
This action will build your Nuxt.js project using `yarn build` and deploy it to GitHub Pages in the `gh-pages` branch of your repository. This is a fork of [ashkantaravati/NuxtToGithubPages](https://github.com/ashkantaravati/NuxtToGithubPages), which builds the site using `npm run build` instead of Yarn.

## Usage
1. Create a Nuxt.js site
2. Add this to your Nuxt.js configuration file (and rename "YourRepoName" to your repo name)
   ```javascript
   module.exports = {
     // ...
     publicPath: '/YourRepoName/'
     // ...
   }
   ```
3. Create a GitHub Actions workflow file and add this to it (and replace "YourGithubName" and "YourRepoName" with the names)
   ```yml
   name: Publish Nuxt app to GH Pages
   on: [push]
   jobs:
     build_vue:
       runs-on: ubuntu-latest
       name: Build Nuxt app
       steps:
       - uses: actions/checkout@v2
       - id: Build-Vue
         uses: garraflavatra/nuxt-gh-pages-yarn@v1.1.1
         with:
           username: 'YourGithubName'
           reponame: 'YourRepoName'
           token: ${{ secrets.GITHUB_TOKEN }} # Leave this line unchanged
   ```
4. Go to your repo settings, click _Pages_ in the sidebar and select `gh-pages` as branch and `/` as site directory.

## Options
| Name | Description | Default | Required |
|--|--|--|:--:|
| username | Your username | - | ✅ |
| reponame | Your repository name | - | ✅ |
| token  | Don't change | - | ✅ |
| gitemail | Git commit email | `CI@example.com` | ❌ |
| gitname | Git commit name | `CI` | ❌ |
| gitmsg  | Git commit message | `deploy` | ❌ |
| cname  | Custom domain | - | ❌ |
