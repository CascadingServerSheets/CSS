# Combinators

Much like Cascading Style Sheets, CSS features a selection of combinators to allow for more complex route selection.

## Descendant Combinator (` `)

Naturally, simply placing a space between selectors will select any route that has the right hand side as a descendant of the left hand side.

```css
blog post {
  status: 200;
  render: 'Welcome to my blog post!';
}
```

This will select any request that has a path of `/blog/**/post`. So, `/blog/post/`, `/blog/first/post`, `/blog/first/second/post`, etc.

It's important to recognize that ` ` does not define string path segments, but just multiple segments that must exist in the that order, but with any number of segments in between.

## Child Combinator (`>`)

The Child Combinator allows you to strictly define the path segments that must exist in the request path.

```css
blog > post {
  status: 200;
  render: 'Welcome to my blog post!';
}
```

This will select any request that has a path of `/blog/post`. So, `/blog/post/` will match, but `/blog/first/post` will not.

## Selector List (`,`)

The Selector List allows you to define rules to apply to multiple independent selectors.

```css
blog,
post {
  status: 200;
  render: 'Welcome to my blog or post!';
}
```

This will apply to routes `/blog` and `/post`. The list is treated as independent selectors, so the rules will apply to each selector in the list as if they were defined separately.
