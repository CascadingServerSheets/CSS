# Cascading Server Sheets

Why should CSS only be for styling?

## What is CSS?

CSS is a Server Sheet language that allows you to declaratively define your server routes and behaviors. Modelled after the Cascading _Style_ Sheets syntax (_so we don't need our own parsers and formatters!_), and inspired by the absolute genius of [Corset's](https://corset.dev) Cascading _Binding_ Sheets (_Why put CSS in JS, when you can put JS in CSS?_), CSS provides a simple and intuitive way to define your server's behavior.

## Housekeeping

CSS follows Documentation Driven Development, where the documentation for the the behaviors and APIs are written first, with the tests and implementations to follow. Documentation of behavior will indicate if the documented behavior is yet to be implemented.

Just open a PR to get the discussion going!

### How to contribute?

Just `git clone https://github.com/CascadingServerSheets/CSS`, make a branch, make your changes, commit, and open that PR!

> This project uses the [Gitmoji](https://gitmoji.dev) convention for commit messages. Please use it when making commits! Or at least making the PR title.

## How it works!

CSS is simple and intuitive! Just define your routes and behaviors in a CSS file, and let the server do the rest!

```css
@server {
  port: 8080;
}

:root {
  status: 200;
  render: 'Hello, World!';
}
```

That's a simple server that listens on port 8080, and returns a 200 status code with the body "Hello, World!".

Want to handle different methods? Just use an ID selector (`#`)!

```css
:root#post {
  status: 201;
  render: 'Created!';
}
```

What about a different route? Just use the Element Selector!

```css
blog {
  status: 200;
  render: 'Welcome to my blog!';
}
```

Deeper routes? Just use child selectors (` `)!

```css
blog my-first-post {
  status: 201;
  render: 'My First Post!';
}
```

Dynamic routes? Just use the Attribute Selector! And access the value with the `attr()` function!

```css
blog [post-id] {
  status: 200;
  render: 'Post ' + attr(post-id);
}
```

How hecking cool is that?
