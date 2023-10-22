# jekyll-2023-test
Yet another test to create a blog with jekyll.rb

## Environment setup

In general, follow the instructions from [this page](https://jekyllrb.com/docs/installation/). These instructions are detailed for openSUSE Linux.

### 1. Install the basic software packages required

```bash
sudo zypper install -t pattern devel_ruby devel_C_C++
sudo zypper install ruby-devel
```

### 2. Install and configure `rbenv` for your shell

`rbenv` allows you to manage different Ruby environments for different projects (more info [here](https://github.com/rbenv/rbenv)).

```bash
sudo zypper install rbenv
echo 'eval "$(~/.rbenv/bin/rbenv init - bash)"' >> ~/.bashrc
```

Restart your shell to make these changes applied.

Check the list of available versions in your device:

```bash
rbenv versions
```

Select a default version for your system:

```bash
rbenv global system
```

### 3. Install the required gems

```bash
gem install jekyll bundler
```

## Site creation

### 1. Create a new jekyll site

This will create a new directory named `my-site`:

```bash
jekyll new my-site
cd my-site
```

If you want to use a folder that has been created earlier (because you already created the git repo or you wanted to set up a specific version for ruby in that folder, as described in step 2), do this instead:

```bash
jekyll new . --force # --force will override jekyll-related files and the .gitignore file
```

You might need to add `webrick` to your bundle if you're using ruby version 3.0.0 or higher:

```bash
bundle add webrick
```

### 2. Configure your ruby version in the system

Select a version for your project:

```bash
rbenv local 3.2.1
```

A file named `.ruby-version` is created to save this information.

### 3. Build the site and make it available through a local server

```bash
bundle exec jekyll serve
```

You can browse your new website from http://localhost:4000. If you want to enable live reload of file changes, so that you can see your edit changes reflected on the fly, just add `--livereload` to the previous command.

## Site deployment setup

Follow the instructions [this page](https://jekyllrb.com/docs/continuous-integration/github-actions/) with one detail: before committing the file with the workflow, remove the line with the `ruby-version` property, since it will not be needed thanks to the `rbenv` configuration that was performed before.