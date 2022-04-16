---
title: TypeScript and Modules for Safety
subtitle: >
    Or, how to avoid dealing with `NaN` problems more than once.
qualifiers:
    audience: >
        TypeScript developers (or at least: folks interested in TypeScript).
    epistemic: >
        This works nicely. It has tradeoffs, which I cover, but it’s correct.
date: 2022-04-13T19:10:00-0600
tags:
    - TypeScript
    - software development
---

Today, I came across some code that looked like this:

```ts
function truncateNumber(n: number): number {
  if (isNaN(n)) {
    return n;
  }

  // some truncation logic ...
}
```

My immediate response, to be honest, was a degree of horror.[^number-is-nan] This is used in some formatting code, which means that if the API hands over a `NaN` for some reason (or if some other conversion in the app produces one), we hand it right back… as a `NaN`.[^li-nan] I was thinking a bit on ways to avoid this problem with TypeScript, and came up with a *decent* approach, though one which has its own tradeoffs.

There are two key elements to the solution: the use of modules and the use of complete lies in the type system… which are isolated within modules. (We could do this without the lies, but that would involve considerably more performance overhead.)

First, we’ll introduce a utility type for defining a type-only item

<dl>
<dt><code>opaque.ts</code></dt>
<dd>

```ts
declare const Brand: unique symbol;
declare class Opaque<T> {
  private readonly [Brand]: T;
}

export type { Opaque };
```

</dd>
</dl>

Then we’ll use this type

<dl>
<dt><code>opaque.ts</code></dt>
<dd>

```ts
import Opaque from './opaque';
```

</dd>
</dl>



[^number-is-nan]: Well, and also to notice that this is using `isNaN` rather than [the better choice, `Number.isNaN`](http://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN).

[^li-nan]: So yes, that means that if you ever come across some chunk of LinkedIn’s web user interface which shows you “NaN”, this may be involved.
