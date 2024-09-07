# @-rules

There are a few special rules in CSS that follow the pattern of `at-rules`.

These are mostly used for the purposes of defining behaviors of the CSS server/runtime itself, as opposed to defining specific behaviors and handlers.

## `@server`

The `@server` rule is used to define the server configuration. As such the `@server` rule must be the first rule in the CSS file. It also contains a few unique properties.

```css
@server {
  port: 8080;
  root-path: '/api';
}
```

| Property    | Description                 | Default |
| ----------- | --------------------------- | ------- |
| `port`      | The port to listen on.      | `8080`  |
| `root-path` | The root path to listen on. | `/`     |
