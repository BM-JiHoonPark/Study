React Roucter 사용법

1. npm이 최신버전인지 확인

    ```
    npm update
    ```

2. react router dom 설치

    ```
    npm install react-router-dom
    ```

3. react에서 라이브러리 호출

    ```
    import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
    ```

4. router 문법

    4-1. 하나의 Components에 하나의 Router를 연결하는 경우

    App.js
    
    ```
    import Home from "./Home"
    
    <Router>
        <Header />
        <Routes>
            <Route path="/" element={<Home />} exact></Route>
        </Routes>
        <Footer />
    </Router>
    ```
    
    Home.js
    
    ```
    export default function Home() {
      return (
        ...
      );
    }
    ```

    4-2. 하나의 Components에 여러개의 Router를 연결하는 경우
    
    App.js
    
    ```
    import Board, {News} from "./Home"
    
    <Router>
        <Header />
        <Routes>
            <Route path="/board" element={<Board />} exact></Route>
            <Route path="/board/news" element={<News />}></Route>
        </Routes>
        <Footer />
    </Router>
    ```
    
    Home.js
    
    ```
    export default function Board() {
      return (
        ...
      );
    }
    
    export function News() {
      return (
        ...
      );
    }
    ```
