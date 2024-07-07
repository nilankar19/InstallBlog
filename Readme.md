# Ubuntu, Jekyll, and GitHub Pages Setup Guide

## 1. Setting up Jekyll

1. **Update the system**:
   ```bash
   sudo apt update
   sudo apt upgrade
   ```

2. **Install Ruby and dependencies**:
   ```bash
   sudo apt install ruby-full build-essential zlib1g-dev
   ```

3. **Set up Ruby Gems environment**:
   ```bash
   echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
   echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
   echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
   source ~/.bashrc
   ```

4. **Install Jekyll and Bundler**:
   ```bash
   gem install jekyll bundler
   ```

5. **Create a new Jekyll site**:
   ```bash
   jekyll new my-awesome-site
   cd my-awesome-site
   ```

6. **Build and serve your site locally**:
   ```bash
   bundle exec jekyll serve
   ```
   - Access your site at `http://localhost:4000`.

## 3. Deploying to GitHub Pages

1. **Install Git**:
   ```bash
   sudo apt install git
   ```

2. **Configure Git**:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

3. **Create a GitHub repository**:
   - Name it `username.github.io` (replace `username` with your GitHub username).

4. **Initialize and push your site**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/username/username.github.io.git
   git push -u origin main
   ```

5. **Configure `_config.yml`**:
   ```yaml
   url: "https://username.github.io"
   ```

6. **Push changes**:
   ```bash
   git add .
   git commit -m "Configure for GitHub Pages"
   git push
   ```

7. **Enable GitHub Pages**:
   - Go to your repository on GitHub, navigate to Settings > Pages, select the main branch, and click Save.

Your site is now live at `https://username.github.io`. Push changes to the main branch to update your site.

## configure bundle

```bash
bundle install

jekyll build

bundle exec jekyll serve --livereload

```