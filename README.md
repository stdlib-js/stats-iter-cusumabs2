<!--

@license Apache-2.0

Copyright (c) 2019 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# itercusumabs2

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Create an [iterator][mdn-iterator-protocol] which iteratively computes a cumulative sum of squared absolute values.

<section class="intro">

The cumulative sum of squared absolute values is defined as

<!-- <equation class="equation" label="eq:cumulative_sum_of_squared_absolute_values" align="center" raw="\begin{align*} s_0 &= x_0^2 \\ s_1 &= x_1^2 + s_0 \\ s_2 &= x_2^2 + s_1 \\ s_n &= x_n^2 + s_{n-1} = x_n^2 + \sum_{i=0}^{n-1} x_i^2 \end{align*}" alt="Equation for the cumulative sum of squared absolute values."> -->

```math
\begin{align*} s_0 &= x_0^2 \\ s_1 &= x_1^2 + s_0 \\ s_2 &= x_2^2 + s_1 \\ s_n &= x_n^2 + s_{n-1} = x_n^2 + \sum_{i=0}^{n-1} x_i^2 \end{align*}
```

<!-- <div class="equation" align="center" data-raw-text="\begin{align*} s_0 &amp;= x_0^2 \\ s_1 &amp;= x_1^2 + s_0 \\ s_2 &amp;= x_2^2 + s_1 \\ s_n &amp;= x_n^2 + s_{n-1} = x_n^2 + \sum_{i=0}^{n-1} x_i^2 \end{align*}" data-equation="eq:cumulative_sum_of_squared_absolute_values">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@daba99f62ed8ff3f49cf13b209c692fd9ccb6c6f/lib/node_modules/@stdlib/stats/iter/cusumabs2/docs/img/equation_cumulative_sum_of_squared_absolute_values.svg" alt="Equation for the cumulative sum of squared absolute values.">
    <br>
</div> -->

<!-- </equation> -->

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/stats-iter-cusumabs2
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var itercusumabs2 = require( '@stdlib/stats-iter-cusumabs2' );
```

#### itercusumabs2( iterator )

Returns an [iterator][mdn-iterator-protocol] which iteratively computes a cumulative sum of squared absolute values.

```javascript
var array2iterator = require( '@stdlib/array-to-iterator' );

var arr = array2iterator( [ 2.0, 1.0, 3.0, -7.0, -5.0 ] );
var it = itercusumabs2( arr );

var s = it.next().value;
// returns 4.0

s = it.next().value;
// returns 5.0

s = it.next().value;
// returns 14.0

s = it.next().value;
// returns 63.0

s = it.next().value;
// returns 88.0
```

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

## Notes

-   If an iterated value is non-numeric (including `NaN`), the function returns `NaN` for **all** future iterations. If non-numeric iterated values are possible, you are advised to provide an [`iterator`][mdn-iterator-protocol] which type checks and handles non-numeric values accordingly.

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var runif = require( '@stdlib/random-iter-uniform' );
var itercusumabs2 = require( '@stdlib/stats-iter-cusumabs2' );

// Create an iterator for generating uniformly distributed pseudorandom numbers:
var rand = runif( -10.0, 10.0, {
    'seed': 1234,
    'iter': 100
});

// Create an iterator for iteratively computing a cumulative sum of squared absolute values:
var it = itercusumabs2( rand );

// Perform manual iteration...
var v;
while ( true ) {
    v = it.next();
    if ( typeof v.value === 'number' ) {
        console.log( 'sumabs2: %d', v.value );
    }
    if ( v.done ) {
        break;
    }
}
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/stats-iter/cumeanabs2`][@stdlib/stats/iter/cumeanabs2]</span><span class="delimiter">: </span><span class="description">create an iterator which iteratively computes a cumulative arithmetic mean of squared absolute values.</span>
-   <span class="package-name">[`@stdlib/stats-iter/cusumabs`][@stdlib/stats/iter/cusumabs]</span><span class="delimiter">: </span><span class="description">create an iterator which iteratively computes a cumulative sum of absolute values.</span>
-   <span class="package-name">[`@stdlib/stats-iter/sumabs2`][@stdlib/stats/iter/sumabs2]</span><span class="delimiter">: </span><span class="description">compute the sum of squared absolute values for all iterated values.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2024. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-iter-cusumabs2.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-iter-cusumabs2

[test-image]: https://github.com/stdlib-js/stats-iter-cusumabs2/actions/workflows/test.yml/badge.svg?branch=v0.2.1
[test-url]: https://github.com/stdlib-js/stats-iter-cusumabs2/actions/workflows/test.yml?query=branch:v0.2.1

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-iter-cusumabs2/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-iter-cusumabs2?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-iter-cusumabs2.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-iter-cusumabs2/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-iter-cusumabs2/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-iter-cusumabs2/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-iter-cusumabs2/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-iter-cusumabs2/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-iter-cusumabs2/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-iter-cusumabs2/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-iter-cusumabs2/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-iter-cusumabs2/main/LICENSE

[mdn-iterator-protocol]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#The_iterator_protocol

<!-- <related-links> -->

[@stdlib/stats/iter/cumeanabs2]: https://github.com/stdlib-js/stats-iter-cumeanabs2

[@stdlib/stats/iter/cusumabs]: https://github.com/stdlib-js/stats-iter-cusumabs

[@stdlib/stats/iter/sumabs2]: https://github.com/stdlib-js/stats-iter-sumabs2

<!-- </related-links> -->

</section>

<!-- /.links -->
