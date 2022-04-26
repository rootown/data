# `data.rootown.io`

This repository controls the contents of `data.rootown.io`, our "backend".

## Intent

This repository was set up to manage our datasets as simply and transparently as possible. Anyone should be able to understand how it works and how it protects maintainers and end-users from working with incorrect data. Anyone should be able to be taught how to update this.

## Design

The `master` branch of this repository is set up to be served at `data.rootown.io`. By default GitHub Pages uses [Jekyll](https://jekyllrb.com), a static website generation tool, to generate HTML to deploy, but we don't want that, so [we can include a `.nojekyll` file to prevent that](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#static-site-generators). We also use a `CNAME` file [to signal to GitHub Pages](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-a-subdomain) that we have DNS records pointing our subdomain to their servers.

To actually manage the versions of the datasets, we make use of feature of Git called ["submodules"](https://git-scm.com/book/en/v2/Git-Tools-Submodules). They allow us to reference a specific commit from another repository as a folder within our own. We have submodules for each of the different datasets we host, pointing to commits on their `master` branches that have been validated and are ready to be shared. If validation for an update to a dataset failed, a commit will not be made to its `master` branch, and so it cannot be updated here.

## Maintenance

**TODO**
