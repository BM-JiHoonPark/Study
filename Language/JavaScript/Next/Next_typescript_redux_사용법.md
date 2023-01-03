1. redux 설치

    ```
    npm install redux react-redux next-redux-wrapper @reduxjs/toolkit
    ```

2. type을 정의할 interface를 생성

    interface/common.tsx

    ```
    export interface counterType {
        count: number;
    }
    ```

3. reducer를 정의할 module을 생성

    store/modules/module.tsx

    ```
    import {counterType} from "interface/common";

    export const INCREASE = 'counter/INCREASE' as const;
    export const DECREASE = 'counter/DECREASE' as const;

    export const increase = () => {
        return {
            type: INCREASE
        }
    }

    export const decrease = () => {
        return {
            type: DECREASE
        }
    }

    type counterAction =
        | ReturnType<typeof increase>
        | ReturnType<typeof decrease>;

    const initialState: counterType = {
        count: 0,
    }

    export default function counter(
        state: counterType = initialState,
        action: counterAction
    ): counterType {
        switch (action.type) {
            case INCREASE:
                return { count: state.count + 1 };
            case DECREASE:
                return { count: state.count - 1 };
            default:
                return state;
        }
    }
    ```

4. reducer들을 관리할 index 파일 생성

    store/modules/index.tsx

    ```
    import { combineReducers } from 'redux';
    import counter from './module';

    const rootReducer = combineReducers({
        counter
    });

    export default rootReducer;

    export type RootState = ReturnType<typeof rootReducer>;
    ```

5. store 생성

    store/index.tsx

    ```
    import {legacy_createStore as createStore, applyMiddleware, Middleware, StoreEnhancer, Store} from "redux"
    import rootReducer from "./modules";
    import { MakeStore, createWrapper } from "next-redux-wrapper";

    const bindMiddleware = (middleware: Middleware[]): StoreEnhancer => {
        if (process.env.NODE_ENV !== 'production') {
            const { composeWithDevTools } = require('redux-devtools-extension');
            return composeWithDevTools(applyMiddleware(...middleware));
        }
        return applyMiddleware(...middleware);
    }

    const makeStore: MakeStore<Store> = () => {
        const store = createStore(rootReducer, {}, bindMiddleware([]));
    return store
    }

    export const wrapper = createWrapper<Store>(makeStore, { debug: true });
    ```

6. _app.tsx 파일 수정

    ```
    import { wrapper } from "../store";

    function App({ Component, pageProps }: AppProps) {
    return (
        <Layout>
            <Component {...pageProps} />
        </Layout>
    )
    }

    export default wrapper.withRedux(App);
    ```

7. redux 사용

    ```
    import { useCallback } from 'react';
    import { useDispatch, useSelector } from 'react-redux';
    import { RootState } from 'store/modules'
    import { increase, decrease } from 'store/modules/module';

    .
    .
    .

    const dispatch = useDispatch();
    const {value} = useSelector((state: RootState) => state.counter)

    const upEvent = useCallback(() => {
        dispatch(increase())
    }, [])

    const downEvent = useCallback(() => {
        dispatch(decrease())
    }, [])

    .
    .
    .

    return (
        <div>
            <div>{value}</div>
            <div>
                <button onClick={upEvent}>Up</button>
                <button onClick={downEvent}>Down</button>
            </div>
        </div>
    )
    }
    ```