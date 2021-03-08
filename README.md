# Oxide Computer Company website

[![make shellcheck](https://github.com/oxidecomputer/website/workflows/make%20shellcheck/badge.svg)](https://github.com/oxidecomputer/website/actions?query=workflow%3A%22make+shellcheck%22+branch%3Amaster)
[![make test](https://github.com/oxidecomputer/website/workflows/make%20test/badge.svg)](https://github.com/oxidecomputer/website/actions?query=workflow%3A%22make+test%22+branch%3Amaster)
[![make broken-link-checker](https://github.com/oxidecomputer/website/workflows/make%20broken-link-checker/badge.svg)](https://github.com/oxidecomputer/website/actions?query=workflow%3A%22make+broken-link-checker%22+branch%3Amaster)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [Prerequisites](#prerequisites)
- [Stack](#stack)
- [Running locally](#running-locally)
- [Adding new content](#adding-new-content)
  - [Blog posts](#blog-posts)
  - [Team members](#team-members)
- [Previewing the production build](#previewing-the-production-build)
- [Styling with TailwindCSS](#styling-with-tailwindcss)
  - [Global CSS utilities.](#global-css-utilities)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## Prerequisites

- [Node and NPM](https://nodejs.org/)

## Stack

- [Eleventy](https://11ty.dev) for templates and site generation
- [Tailwindcss](https://tailwindcss.com) for a utility first CSS workflow


## Running locally

```bash
# install the project dependencies
npm install

# run the build and server locally
npm run watch
```

## Adding new content 

### Blog posts

Add a new markdown file to [`src/site/blog`](src/site/blog). Make sure it has the
following metadata at the top of the file. To make things easy on yourself, duplicate an existing post.

```
---
title: 'Post title'
subtitle: 'Post subtitle (if any)'
date: 2020-02-03T23:00:00
tags: ['post', 'announcements']
authors: ["first-last", "first-last", "first-last"]
description: |
    A description that is used in snippets.
---
```

~~The authors field can hold more than one author and is the name of the `json`
file for the specific author in [`_data/team`](src/site/_data/team).~~

Make sure to add a `description` to your post for the main pages as well as social 
media cards.

### Team members

Add a json file to [`_data/team`](data/team) in the following format:

```json
{
  "weight": 1,
  "name": "Jessie Frazelle",
  "title": "CPO",
  "twitter": "jessfraz",
  "github": "jessfraz",
  "linkedin": "https://www.linkedin.com/in/jessie-frazelle/",
  "blog": "https://jess.dev"
}
```

Then add an entry to the ordered list in [`_data/team/members.json`](src/site/_data/team/members.json).

## Previewing the production build

When building for production, an extra build step will strip out all CSS classes not used in the site. This step is not performed during the automatic rebuilds which take place during dev.

```bash
# run the production build
npm run build
```

## Styling with TailwindCSS

This site uses TailwindCSS to offer utility CSS classes and provide a rapid means to styling the site. This means that most styling can be done without writing any additional CSS. Instead, utility classes can be added directly to the HTML. This may not be to everyone's tastes, but it can provide some very rapid development and also offer surprising levels of familiarity for those used to working in this way (since the conventions and classes are not _per site_.)

While running/developing locally, the `npm run start` command will recompile the site as files are saved and this includes the CSS pipeline from Tailwind.

### Global CSS utilities.

A small number of bespoke CSS rules are provided for efficiency of repeated or global classes. These reside in `src/site/_includes/css/tailwind.css`

