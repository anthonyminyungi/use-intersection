# use-intersection

[![npm](https://img.shields.io/npm/v/use-intersection.svg?style=flat-square)](https://www.npmjs.com/package/use-intersection)
[![CircleCI](https://img.shields.io/circleci/project/github/cats-oss/use-intersection/master.svg?style=flat-square)](https://circleci.com/gh/cats-oss/use-intersection)

> [React Hooks](https://reactjs.org/docs/hooks-intro.html) for [IntersectionObserver](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API).

:dog: See [Storybook](https://cats-oss.github.io/use-intersection/).

## Installation

```bash
$ yarn add use-intersection
```

## Usage

### Basic

This is the simplest example.

```typescript
import * as React from 'react';
import { useIntersection } from 'use-intersection';

const Component: React.FC = () => {
  const target = React.useRef<HTMLDivElement>(null);
  const intersecting = useIntersection(target);

  return <div ref={target}>{intersecting ? 'visible' : 'invisible'}</div>;
};
```

### Custom Root Element

This is an example of using scrollable elements other than Viewport.

```typescript
import * as React from 'react';
import { useIntersection } from 'use-intersection';

const Component: React.FC = () => {
  const root = React.useRef<HTMLDivElement>(null);
  const target = React.useRef<HTMLDivElement>(null);
  const intersecting = useIntersection(target, {
    root,
    rootMargin: '100px',
  });

  return (
    <div style={{ overflow: 'hidden auto', height: 300 }}>
      {/* ... */}
      <div ref={target}>{intersecting ? 'visible' : 'invisible'}</div>
      {/* ... */}
    </div>
  );
};
```

## Browser support

Supports modern web browser.

If your browser does not support `IntersectionObserver`, we recommend using Polyfill.

### npm package

```bash
$ yarn add intersection-observer
```

> https://www.npmjs.com/package/intersection-observer

### CDN

```html
<script src="https://polyfill.io/v3/polyfill.min.js?features=IntersectionObserverEntry%2CIntersectionObserver"></script>
```

> https://polyfill.io/v3/

## API

The following resources will help you.

- [React Hooks](https://reactjs.org/docs/hooks-intro.html)
- [Intersection Observer](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)

---

`useIntersection` is returns a flag whether the target intersects.

```typescript
useIntersection(
  ref: React.RefObject<Element>,
  options: IntersectionOptions = {},
  callback?: IntersectionChangeHandler,
) => boolean;
```

### `options: IntersectionOptions`

```typescript
{
  root?: React.RefObject<Element>;
  rootMargin?: string;
  threshold?: number | number[];
  defaultIntersecting?: boolean;
}
```

### `callback: IntersectionChangeHandler`

```typescript
(entry: IntersectionObserverEntry) => void
```

## CHANGELOG

See [CHANGELOG.md](./CHANGELOG.md).

## Contributing

We are always welcoming your contribution :clap:

1. Fork (https://github.com/cats-oss/use-intersection) :tada:
1. Create a feature branch :coffee:
1. Run test suite with the `$ yarn test` command and confirm that it passes :zap:
1. Commit your changes :memo:
1. Rebase your local changes against the `master` branch :bulb:
1. Create new Pull Request :love_letter:

Bugs, feature requests and comments are more than welcome in the [issues](https://github.com/cats-oss/use-intersection/issues).

### Development scripts

#### `yarn storybook`

Run Storybook.

```bash
$ yarn storybook
```

#### `yarn test`

Run Unit test with Jest.

```bash
$ yarn test
```

#### `yarn lint`

Run lint with ESLint.

```bash
$ yarn lint
```

#### `yarn format`

Run formatting with ESLint (`--fix`) and Prettier.

```bash
$ yarn format
```

## License

[MIT © Cyberagent, Inc](./LICENSE)