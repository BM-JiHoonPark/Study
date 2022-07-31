1. Scroll 시 Fade In 이벤트 구현을 위해 IntersectionObserver 사용이 필요

2. Scrollama Lib를 이용하여 IntersectionObserver 사용

3. Scrollama 공식 오픈소스 URL

    ```
    https://github.com/russellgoldenberg/scrollama
    ```

4. Scrollama Lib Install

    ```
    npm Install scrollama intersection-observer
    ```

5. Scrollama Import

    ```
    import scrollama from "scrollama";
    ```

6. Scrollama 기본 문법

    ```
    const scroller = scrollama();

    scroller
    .setup({
        step: ".step",
    })
    .onStepEnter((response) => {
        // { element, index, direction }
    })
    .onStepExit((response) => {
        // { element, index, direction }
    });


    <div class="step" data-step="a"></div>
    <div class="step" data-step="b"></div>
    <div class="step" data-step="c"></div>
    ```

7. Scrollama는 비동기적으로 실행되어야하므로 useEffect 내부에 실행

    ```
    const scroller = scrollama();
    useEffect(() => {
        scroller
            .setup({
            step: ".step",
            })
            .onStepEnter((response) => {
                // { element, index, direction }
            });
    }, []);
    ```