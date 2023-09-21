---
order: 10
icon: repo-push
---
The OpenMRS Guide is hosted at [https://github.com/openmrs/openmrs-book-guide](https://github.com/openmrs/openmrs-book-guide). 
Anyone is welcome to help us improve the guide by contributing pull requests to this repository. We use [Retype](https://retype.com/) 
for this guide. It's basically simple [Markdown formatting](https://retype.com/guides/formatting/).

## GitHub account

If you don't have one, get a [GitHub account](https://github.com/join). It's free!

## Simplest approach

Use the `Edit this page` link at the bottom of any page to make edits. GitHub will guide you through submitting any changes as a pull request.

## Advanced edits

If you plan to perform more extensive edits of the guide, you can clone the repository, make multiple edits and submit 
those changes through a pull request. This requires some basic knowledge of working with [git](https://www.w3schools.com/git/).

### Using gitpod.io

gitpod.io offers free environments. By forking the guide's repository to your own GitHub account, signing up for a free gitpod.io account, 
and granting access to your GitHub account, you can create a gitpod.io workspace for free using your fork of the guide's repository and 
the VS Code editor. Once the environment is running, you can start Retype within virtual VS Code's terminal window using the commands:

```bash
npm install retypeapp --global 
retype start
```

This should start Retype and run the guide on port 5000 at a URL you can load in your browser for testing.

### Using Docker

If you have [Git](https://git-scm.com/) and [Docker](https://docker.com/) installed, you can clone the guide locally and make & test
changes locally.

```bash
git clone https://github.com/openmrs/openmrs-book-guide
cd openmrs-book-guide
docker run --rm -it -p 5000:5000 -v "$PWD:/app" -w /app retypeapp/retype retype start
```

The guide should be running at the URL displayed by Retype until you press `Ctrl-C` to quit. While Retype is running, any changes made
to the files should show up nearly instantly in your browser.

## Questions?

If you have questions, join the community in [OpenMRS Talk](https://talk.openmrs.org/) or [Slack](http://om.rs/slack).

!!!
**NOTE**: The guide was written for OpenMRS 1.9 in 2012 and needs to be updated. We would appreciate any help in updating the 
guide to cover OpenMRS 2.x and OpenMRS 3.x.
!!!