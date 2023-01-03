React state 사용법

1. state란 일반 변수와 다르게 값이 변하게 되면 렌더링이 일어남

2. state와 함께 setState, useState 가 사용됨

3. state를 사용하기 위해 useState import

    ```
    import React, { useState } from "react";
    ```

4. state 기본 문법

    ```
    const [state, setState] = useState(초기값)

    setState(변경값);
    ```

5. 이전 state 값 사용 시 prevState를 이용