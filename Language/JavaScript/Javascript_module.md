문법 수준에서 모듈을 지원하기 시작한 것은 ES2015부터로 아래와 같은 문법으로 사용한다.

```
// index.html
<!DOCTYPE html>
<html lang="en">
.
.
.
    <body>
        <script src="math.js"></script>
        <script src="app.js"></script>
    </body>
</html>

// math.js
function sum(a, b) {
    return a + b;
}

// app.js
console.log(sum(1 + 2));


// console
3
```

위 방식을 이용할 경우 전역 스코프에 모든 함수가 선언되므로 관리가 힘들다.

이러한 문제를 예방하기 위해 IIFE(Immediately Invoked Functino Expression, 즉시 실행 함수 표현)를 사용했다.

```
// math.js
var math = math || {};

(function () {
    function sum(a, b) {
        return a + b;
    }

    math.sum = sum;
})();

// app.js
console.log(math.sum(1 + 2))


// console
3
```

외에도 AMD, UMD, CommonJS 등의 모듈 명세가 존재한다.

이렇게 각 커뮤니티에서 각자의 스펙을 제안하다가 ES2015에서 표준 모듈 시스템을 내 놓았다.

```
// index.html
<!DOCTYPE html>
<html lang="en">
.
.
.
    <body>
        <script type="module" src="app.js"></script>
    </body>
</html>

// math.js
export defalut function sum(a, b) {
    return a + b;
}

// app.js
import Math from './math.js';
console.log(Math(1 + 2));
=====
import * as math from './math.js';
console.log(math.sum(1 + 2));
=====
import { sum } from './math.js';
console.log(sum(1 + 2));


// console
3
```