# jekyll-2023-test
Yet another test to create a blog with jekyll.rb

## Environment setup

In general, follow the instructions from [this page](https://jekyllrb.com/docs/installation/).

### openSUSE

#### 1. Install the basic software packages required

```bash
sudo zypper install -t pattern devel_ruby devel_C_C++
sudo zypper install ruby-devel
```

#### 2. Install and configure `rbenv` for your shell

`rbenv` allows you to manage different Ruby environments for different projects (more info [here](https://github.com/rbenv/rbenv)).

```bash
sudo zypper install rbenv
echo 'eval "$(~/.rbenv/bin/rbenv init - bash)"' >> ~/.bashrc
```

Restart your shell to make these changes applied.

#### 3. Configure your ruby version in the project

Check the list of available versions in your device:

```bash
rbenv versions
```

Select a version for your project:

```bash
rbenv local 3.2.1
```

A file named `.ruby-version` is created to save this information.