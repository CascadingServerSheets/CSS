# Selectors

Selectors are used to _select_ requests to apply routing properties to.

## `:root`

The `:root` selector is used to define behavior for requests that directly match the root path.

```css
:root {
  status: 200;
  render: 'Hello, World!';
}
```

This will return a 200 status code with the body "Hello, World!" when a request is made on the root path (`/` by default).

## Route Segment Selectors

Route Segment Selectors are used to define behavior for requests that match a specific route segment. These are similar to `type selectors` in Cascading Style Sheets.

```css
api {
  status: 200;
  render: 'Welcome';
}
```

This will return a 200 status code with the body "Welcome" when a request is made on the `/api` path.

> The above will select any request that contains a path segment of `api`. To select requests that have a specific path segment at a specific position, use the `child combinator`.

## Method Selectors (`#`)

Method Selectors are used to define behavior for requests that match a specific method. These are similar to `id selectors` in Cascading Style Sheets.

```css
#get {
  status: 200;
  render: 'GET Request';
}
```

This will return a `200` status code with the body "GET Request" when a `GET` request is made. As defined above, this would be _ANY_ `GET` request.

## Dynamic Route Selectors (`[]`)

Dynamic Route Selectors are used to define behavior for requests that match a specific dynamic route. These are similar to `attribute selectors` in Cascading Style Sheets.

```css
[post-id] {
  status: 200;
  render: 'Post ' + attr(post-id);
}
```

This will return a `200` status code with the body "Post " followed by the value of the `post-id` attribute in the request path.

You can see here, that the `attr()` function is used to access the value of the dynamic route segment. You can read more about that in the `Functions` section.

## Nesting Selectors (`&`)

Much like Cascading Style Sheets, CSS allows for nesting selectors.

```css
posts {
  status: 200;
  render: 'Welcome';

  #post {
    status: 503;
    render: 'Not Implemented';
  }
}
```

This defines a static `GET` route (`GET /posts`) and broader (`POST /posts/**/*`). You'll notice the `/**/*` is is implied. This would be similar to defining a selector of `posts #post`. This would select all `POST` requests to any route deeper than `/posts` but not `POST` requests to `/posts` itself.

If you want it to select `POST` requests on `/posts` only, you'd want to explicitly structure the nesting with `&`

```css
posts {
  status: 200;
  render: 'Welcome';

  &#post {
    status: 503;
    render: 'Not Implemented';
  }
}
```

This now selects `POST` requests to `/posts` only, and not all `POST` requests to deeper routes.
