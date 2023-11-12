# Hugo Cheat Sheet

![hugo](media/hugo-logo.png)

Thank you for supporting the Hugo Blox Builder open source initiative to empower creators and educators!

# Useful links

- [Hugo Blox Documentation](https://docs.hugoblox.com/)
- [Hugo Blox on GitHub](https://github.com/HugoBlox/)
- [Chat with the Discord community](https://discord.gg/z8wNYzb)
- [Ask longer questions on the Forums](https://github.com/HugoBlox/hugo-blox-builder/discussions)
- [Troubleshooting Guide](https://docs.hugoblox.com/)
- [Twitter community](https://twitter.com/GetResearchDev)
- [Email newsletter](http://eepurl.com/hosBCH)

# Hugo site structure

There are **3 main folders for Hugo sites**:

- `content/` for your Markdown-formatted content files (homepage, etc.)
- `assets/media/` for your media files (images, videos)
- `config/_default/` for your site configuration files
  - `config.yaml` to configure Hugo (site title, URL, Hugo options, enable page features)
  - `params.yaml` to configure Hugo Blox Builder options (SEO, site features)
  - `menus.yaml` to configure your menu links (if the menu is enabled in `params.yaml`)
  - `languages.yaml` to configure your site's language or to set language-specific options in a multilingual site

# Markdown style

**While typing:**

- Type `**` on either side of your text to **bold.**
- Type `_` on either side of your text to *italicize*.
- Type ` on either side of your code for inline code. (That's the backtick symbol to the left of your 1 key.)
- Type `~~` on either side of your text to ~~strikethrough~~.
- Type `{{< math >}}$x=1/y${{< /math >}}` for inline math (and enable math in `params.yaml`)
- Type `{{< math >}}$$x=1/y$${{< /math >}}` for block math (and enable math in `params.yaml`)

**At the beginning of any new line or existing block of content, try these:**

- Type `-` followed by `space` to create a bulleted list.
- Type `- [ ]` or `- [x]` to create a to-do checkbox.
- Type `1.` followed by `space` to create a numbered list.
- Type `##` followed by `space` to create an H2 sub-heading.
- Type `###` followed by `space` to create an H3 sub-heading.
- Type `>` followed by `space` to create a quote block.

[View all formatting options](https://docs.hugoblox.com)

# YAML Front Matter

[Learn YAML syntax](https://learnxinyminutes.com/docs/yaml/) for setting page options within Markdown files.

[View page options](https://docs.hugoblox.com)

# Theme Customization

The following options are available for [creating or customizing color themes](https://docs.hugoblox.com):

```toml
# The name of your theme
name = "My Theme"

# Light theme
[light]
	# Your brand color (used for buttons etc.)
	primary = "blue"
	
	# Link color
	link = "blue"
	link_hover = "navy"
	
	# Menu colors
	menu_primary = "#fff" # Menu background
	menu_text = "#000" # Menu text color
	menu_text_active = "#000" # Menu active link color
	menu_title = "#000" # Menu title color
	
	# Default odd and even widget page section background colors
	home_section_odd = "rgb(255, 255, 255)"
	home_section_even = "rgb(255, 255, 255)"

# Dark theme
# Supports all color options above.
# Note that Bootstrap only currently supports one `primary` color across both light and dark modes.
[dark]
  # Link colors
  link = "skyblue"
  link_hover = "white"
```

# Hugo CLI Commands

- `hugo`
  Build your site (if not deploying to Netlify)
- `hugo server`
  View your site locally, previewing your site in your browser as you edit your site. After editing the homepage or site config, you may need to stop Hugo (`Control + C`) and restart it.
- `hugo mod graph`
  Show your site's module (theme) version in Hugo's format (the first 7 characters after the last hyphen give the actual "commit" version on GitHub)
- `echo "https://github.com/HugoBlox/hugo-blox-builder/commits/"$(hugo mod graph | grep "blox-bootstrap@" | grep -oE ".{12}$" | grep -oE "^.{7}")`
  Get a link to your Hugo Blox Builder "commit" version on GitHub
- `hugo version`
  Show your Hugo version
- `hugo mod vendor`
  Download Hugo Blox Builder Hugo Modules into your site folder for easier offline editing.

# Create your own Widgets

Use the [Blox Creator](https://github.com/HugoBlox/create-blox)

# Edit the Layout of Any Page

Layouts are parametised in page front matter and site configuration to provide a friendly **no-code** environment.

However, all layouts can also be fully customized using [Hugo's override principle](https://docs.hugoblox.com).

# RStudio for Statisticians

Many members of the community enjoy writing technical blog posts with snippets of the R statistical programming language using the RStudio editor.

The RStudio team released Blogdown, a wrapper around Hugo for the RStudio IDE. However, users report that **Blogdown doesn't fully support modern Hugo versions**, with the RStudio team confirming these reports on GitHub.

Hence, the community recommend converting RMarkdown files directly to Markdown **without Blogdown** by using `render("input.Rmd", md_document())` or adding `output: md_document` to the file's front matter. Then Hugo can be used directly and in a more streamlined setup.
- [RStudio & Blogdown documentation](https://docs.rstudio.com/)
- [RStudio & Blogdown support](https://docs.rstudio.com/support/)

**Something we didn't cover?**

Check out the full [Hugo Blox documention](https://docs.hugoblox.com), [Hugo documentation](https://gohugo.io/documentation/), and [Netlify documentation](https://docs.netlify.com/).

Message _CodeWithGeo_ on Discord with your feedback✌️
