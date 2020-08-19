# About
Repository for IPF How-To Guides webpage.

Page is displayed at: https://mpicbg-scicomp.github.io/ipf_howtoguides/


# Contribute
* Copy the [Template page](guides/Template_Page.md) and fill with own instructions.
* Images: Place them under *guides/pics* . 
	* Try using standard markdown image import `![](path/to/pic.png)`. 
	* If the image is too large, specify its size via html import: `<img src="path/to/pic.png" width="100">`
	* Can also create a html table to place multiple images next to each other (without header), see [Ilastik guide](guides/Ilastik_PixelClassification) for an example.
* Update the main page ([index.md](index.md)) with a link + thumbnail for the new how-to guide.

## Setup on a local computer
* The page is automatically being built on the github server. But for development it is more convenient to work locally.
* Clone the repository.

#### Markdown
* The easiest way is to write new text with your favorite markdown editor. The preview will then be *github flavored markdown* (and not the built page) and some of the page features will not be previewable (buttons, table of content, ...). 
* But for adding a new how-to page this should totally suffice.

#### Build page with jekyll
* Setup instructions: https://docs.github.com/en/github/working-with-github-pages/testing-your-github-pages-site-locally-with-jekyll and https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll
* Instructions are roughly (to be improved) ([see here](https://jekyllrb.com/docs/installation/macos/)):
	* Install `ruby` ([if not yet installed](https://stackify.com/install-ruby-on-your-mac-everything-you-need-to-get-going/), should be installed by default on a MacOS)
	* Install `bundler` and `jekyll`
* To serve the page:
	* go to root folder of your repository and type: `bundle exec jekyll serve`
	* open browser and go to: `localhost:4000/`


## Keep in mind
* `Don't share account information (passwords!) publicly. `
* **TODO** Check with IT department about sharing internal links.
* More sensitive information can be placed in the internal wiki (and linked here).

## Page theme
* General info on github pages [here](https://guides.github.com/features/pages/) and [here](https://docs.github.com/en/github/working-with-github-pages).
* This page uses `justthedocs` jekyll theme: https://pmarsceill.github.io/just-the-docs/

#### Theme features which are currently not used but could be useful:
* Buttons: https://pmarsceill.github.io/just-the-docs/docs/ui-components/buttons/ 
* Custom Page Title for the left sidebar: https://pmarsceill.github.io/just-the-docs/docs/navigation-structure/ 
> ```
> ---
> title: Custom title
> ---
> ```
* The Navigation structure on the left side bar can be customized in case we get too many pages: https://pmarsceill.github.io/just-the-docs/docs/navigation-structure/

