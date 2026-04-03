# Local Preview Guide

Steps to build and preview the site on your machine before pushing to GitHub Pages.

## Prerequisites

- [Homebrew](https://brew.sh) installed
- Ruby 3.x via Homebrew (`brew install ruby`)

## 1. Add Homebrew Ruby to your PATH

```bash
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
```

To make this permanent, add the line above to your `~/.zshrc`:

```bash
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

## 2. Install dependencies

From the repository root:

```bash
bundle install
```

## 3. Start the local server

```bash
bundle exec jekyll serve
```

The site will be available at **http://localhost:4000**.

Jekyll watches for file changes and rebuilds automatically. Refresh your browser to see updates.

## 4. Build without serving (optional)

To generate the `_site/` output without starting a server:

```bash
bundle exec jekyll build
```

## Troubleshooting

**`cannot load such file -- csv` or similar stdlib errors**
Ensure you are using Homebrew Ruby (≥ 3.2), not the system Ruby 2.6:
```bash
ruby --version   # should show 3.x or 4.x
which ruby       # should show /opt/homebrew/opt/ruby/bin/ruby
```

**Remote theme takes a long time on first run**
The Jekyll Serif theme is downloaded on the first build and cached. Subsequent builds are fast.

**Port 4000 already in use**
Run on a different port:
```bash
bundle exec jekyll serve --port 4001
```
