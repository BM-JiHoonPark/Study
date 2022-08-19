1. Javascript에서 정렬 시 .sort() 함수를 사용

2. sort 문법

    ```
    // 기본 문법
    arr.sort([compareFunction]);


    // 숫자 정렬
    arr.sort(function(a, b) {
        return a - b;
    });

    // 숫자 정렬 간소화
    arr.sort((a, b) => a - b);


    // value 기준 정렬
    arr.sort(function (a, b) {
        if (a.value > b.value) {
            return 1;
        }
        if (a.value < b.value) {
            return -1;
        }
        // a must be equal to b
        return 0;
    });

    // value 기준 정렬 간소화
    arr.sort((a, b) => a.value > b.value ? 1 : a.value < b.value ? -1 : 0 );
    ```
