# wasm-pack


이 도구는 JavaScript, 브라우저 또는 Node.js와 상호 운용하려는 Rust로 생성된 WebAssembly를 구축하고 작업하기 위한 원스톱 상점이 되고자 합니다. wasm-pack은 npm 레지스트리에 게시하거나 웹팩과 같이 이미 사용하고 있는 워크플로우에서 자바스크립트 패키지와 함께 사용할 수 있는 Rust로 생성된 WebAssembly 패키지를 빌드하는 데 도움이 됩니다.


자세한 내용은 [Welcome to the wasm-pack docs!]( https://rustwasm.github.io/docs/wasm-pack/introduction.html)을 참고한다.


## Quickstart
1. Install rust using rustup.
2. Install this tool.
3. Run wasm-pack new hello-wasm.
4. cd hello-wasm
5. Run wasm-pack build.
7. This tool generates files in a pkg dir
8. To publish to npm, run wasm-pack publish. You may need to login to the registry you want to publish to. You can login using wasm-pack login.



