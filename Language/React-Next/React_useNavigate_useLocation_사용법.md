1. react-router-dom Lib에서 useNavigate와 useLocation을 import 받는다.

    ```
    import { useNavigate, useLocation } from 'react-router-dom';
    ```

2. Lib의 hook 들을 변수에 담는다.

    ```
    const location = useLocation();
    const navigate = useNavigate();
    ```

3. useNavigate 문법

    ```
    navigate(URL, { replace, state });
    ```

4. useLocation 문법

    ```
    const state = location.state.value
    ```