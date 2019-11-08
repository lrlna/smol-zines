## Rust + Wasm

A zine on what is Wasm and how to work with it in Rust!

Good resoures and reading materials:
- [WebAssembly
  Concepts](https://developer.mozilla.org/en-US/docs/WebAssembly/Concepts)
- [Wasm
  Portability](https://webassembly.org/docs/portability/#assumptions-for-efficient-execution)
- [RustWasm book](https://rustwasm.github.io/book/)
- [Wasm's Memory
  Model](https://webassembly.github.io/spec/core/syntax/modules.html#syntax-mem)
- [Wasm Memory,
  Illustrated](https://hacks.mozilla.org/2017/07/memory-in-webassembly-and-why-its-safer-than-you-think/)
Printing instructions are available [here](./instructions.md).

Happy Reading!

_Edit:_
_Previous version of this zine stated that memory is not shared between
Wasm and JS. It is indeed shared. Otherwise lots of the things that make Wasm in
the browser work would not work!!_

_Previous version of this zine also said a Table stores references in a typed
array, they are in fact stored in an object._

![rust wasm zine](./img/rust-wasm.png)
