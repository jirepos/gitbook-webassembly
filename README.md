# 소개 

이 책은 두 개의 하위 책들로 구성되어 있습니다. 

1. wasm-pack
2. wasm-bindgen


##  WebAssembley

웹 어셈블리(WebAssembly, WASM)는 웹 브라우저에서 실행되도록 설계된 낮은 수준의 휴대용 이진 형식이다. 웹 브라우저에서 사용되는 주요 프로그래밍 언어인 자바스크립트보다 빠르고 효율적으로 설계되었다.

웹 어셈블리는 C, C++, 러스트와 같은 언어로 작성된 코드를 웹 어셈블리로 컴파일하여 웹 브라우저에서 실행할 수 있도록 모든 프로그래밍 언어의 컴파일 대상이 되도록 설계되었다. 이를 통해 개발자는 특정 작업에 자바스크립트보다 성능이 뛰어난 언어를 사용하면서도 웹 브라우저에서 실행할 수 있다.

웹어셈블리는 자바스크립트와 함께 실행되도록 설계되어 개발자들이 웹 애플리케이션을 구축하기 위한 자바스크립트의 유연성과 사용 편의성, 그리고 더 많은 컴퓨팅 파워를 요구하는 작업을 위한 웹어셈블리의 성능이라는 두 가지 장점을 모두 사용할 수 있다.

웹 어셈블리는 진화하는 표준이며, 이에 대한 지원은 현대 웹 브라우저에 지속적으로 추가되고 있다. WebAssembly에 대해 자세히 알아보려면 [https://webassembly.org/](https://webassembly.org/)에서 공식 WebAssembly 웹 사이트를 방문할 수 있다.



WebAssembly(wasm)는 광범위한 사양을 가진 간단한 기계 모델 및 실행 가능한 형식이다. 휴대 가능하고 컴팩트하며 기본 속도 또는 그와 비슷한 속도로 실행되도록 설계되었다. 

프로그래밍 언어로서 WebAssembly는 방식은 다르지만 동일한 구조를 나타내는 두 가지 형식으로 구성된다. As a programming language, WebAssembly is comprised of two formats that represent the same structures, albeit in different ways:

1. .wat text forma(called wat for "**W**eb**A**ssembly **T**ext")은 S-expressions를 사용한다. Scheme 및 Clojure와 같은 Lisp 계열 언어와 유사하다. 
2. .wasm 바이너리 형식은 하위 수준이며 wasm 가상 머신에서 직접 사용하기 위한 것이다. 개념적으로 ELF 및 Mach-O와 유사하다. 

예를 드러, wat에서 factorial function은 아래와 같다. 
```wat
(module
  (func $fac (param f64) (result f64)
    local.get 0
    f64.const 1
    f64.lt
    if (result f64)
      f64.const 1
    else
      local.get 0
      local.get 0
      f64.const 1
      f64.sub
      call $fac
      f64.mul
    end)
  (export "fac" (func $fac)))
```

wasm 파일이 어떻게 생겼는지 궁금하다면 위의 코드와 함께 [wat2wasm 데모](https://webassembly.github.io/wabt/demo/wat2wasm/)를 사용할 수 있다.



## Linear Memory 
WebAssembly는 매우 간단한 메모리 모델을 가지고 있습니다. wasm 모듈은 기본적으로 플랫 바이트 배열인 단일 '선형 메모리'에 액세스할 수 있다. 이 메모리는 페이지 크기(64K)의 배수만큼 커질 수 있다. 축소할 수 없다.




## 왜 rust를 사용해야 하는가?
Rust가 WebAssembly 애플리케이션을 만드는 데 좋은 선택인 몇 가지 이유가 있다. 

*  Rust는 컴파일되고 정적으로 유형이 지정된 언어이므로 JavaScript와 같은 동적으로 유형이 지정된 언어보다 WebAssembly로 더 효율적으로 컴파일될 수 있다. 
* Rust는 메모리 안전 및 데이터 경합 방지에 중점을 두어 브라우저에서 실행되는 보안 애플리케이션을 개발하는 데 매우 적합하다. 
* WebAssembly 애플리케이션을 쉽게 구축할 수 있게 해주는 라이브러리 및 도구의 생태계가 성장하고 있다. 예를 들어 wasm-bindgen 라이브러리를 사용하면 JavaScript에서 Rust 함수를 쉽게 호출할 수 있고 그 반대도 가능하다. 
* Rust에는 언어와 도구를 지속적으로 개선하는 크고 활동적인 개발자 커뮤니티가 있으므로 시간이 지남에 따라 유지 관리하고 확장해야 하는 프로젝트에 적합하다. 


공식적으로 RUST에서 WebAssembly에 대한 내용을 다루고 있는데  [Rust 🦀 and WebAssembly](https://rustwasm.github.io/docs/book/introduction.html)의 내용도 참고하여 참고하여 정리할 것이다. 



