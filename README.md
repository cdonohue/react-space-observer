# `<SpaceObserver>`

> A ResizeObserver react component with polyfill support

### Getting Started

Add `react-space-observer` to your project using `yarn` or `npm`

```bash
yarn add react-space-observer
```

```bash
npm install react-space-observer
```

Use the `SpaceObserver` to wrap your component and report size/geometry changes

```js
import SpaceObserver from "react-space-observer"

...
<SpaceObserver>
  {({ width, height, x, y, top, right, bottom, left }) => (
    // render your observed component here
  )}
</SpaceObserver>
...
```

### Example

Let's use a `SpaceObserver` to change a component style at a certain width:

```js
<SpaceObserver>
  {({ width }) => (
    <div
      style={{
        borderRadius: ".2rem",
        padding: "2rem",
        color: "white",
        backgroundColor: width >= 568 ? "dodgerblue" : "firebrick",
      }}
    >
      Hello, World
    </div>
  )}
</SpaceObserver>
```

As the component's geometry changes, the `width` is reported back and we are given a chance to conditionally render. Above we changed the background color from red to blue.

### How does it work?

This is a decoration around `ResizeObserver`. A ponyfill is used if `ResizeObserver` is not present. Also, only one `ResizeObserver` instance is stored in memory. This way, multiple observed elements can exist on a page without any additional overhead.
