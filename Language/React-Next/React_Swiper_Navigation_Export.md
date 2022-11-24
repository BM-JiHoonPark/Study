1. Swiper 사용 시 Navigation을 Swiper Section 밖에 노출시킬 경우 Swiper를 재 랜더링 시킨다.

2. Swiper를 재 랜더링 시키기 위해 변수와 useEffect를 생성

    ```
    const [swiper, setSwiper] = useState();

    useEffect(() => {
    }, [swiper]);
    ```

3. Navigation을 포함한 Swiper를 생성

    ```
    <Swiper
        modules={[Navigation]}
        navigation={true}
        className="mySwiper">
        <SwiperSlide>Slide 1</SwiperSlide>
        <SwiperSlide>Slide 2</SwiperSlide>
        <SwiperSlide>Slide 3</SwiperSlide>
        <SwiperSlide>Slide 4</SwiperSlide>
        <SwiperSlide>Slide 5</SwiperSlide>
    </Swiper>
    ```

4. Custom Navigation을 생성한다.

    ```
    <div className="swiper-button">prev</div>
    <div className="swiper-button">next</div>
    ```

5. useRef를 사용하여 Custom Navigation Document를 가져온다.

    ```
    const prevRef = useRef();
    const nextRef = useRef();
    ```

    ```
    <div className="swiper-button" ref={prevRef}>prev</div>
    <div className="swiper-button" ref={nextRef}>next</div>
    ```

6. onSwiper Option을 이용하여 Swiper가 생성 완료된 시점에서 재 랜더링

    ```
    <Swiper
        modules={[Navigation]}
        navigation={true}
        onSwiper={(swiper) => setSwiper(swiper)}
        className="mySwiper">
        <SwiperSlide>Slide 1</SwiperSlide>
        <SwiperSlide>Slide 2</SwiperSlide>
        <SwiperSlide>Slide 3</SwiperSlide>
        <SwiperSlide>Slide 4</SwiperSlide>
        <SwiperSlide>Slide 5</SwiperSlide>
    </Swiper>
    ```

7. Swiper의 기본 Navigation 대신 Custom Navigation을 적용

    ```
    useEffect(() => {
    if (swiper) {
        swiper.params.navigation.prevEl = prevRef.current;
        swiper.params.navigation.nextEl = nextRef.current;
        swiper.navigation.init();
        swiper.navigation.update();
    }
    }, [swiper]);
    ```

8. Sample Code

    ```
    import React, { useEffect, useState, useRef } from "react";
    import { Swiper, SwiperSlide } from "swiper/react"; // basic
    import SwiperCore, { Navigation } from "swiper";
    import "swiper/css"; //basic
    import "swiper/css/navigation";
    import "swiper/css/pagination";

    export default function App() {
        const [swiper, setSwiper] = useState();
        const prevRef = useRef();
        const nextRef = useRef();

        useEffect(() => {
            if (swiper) {
            swiper.params.navigation.prevEl = prevRef.current;
            swiper.params.navigation.nextEl = nextRef.current;
            swiper.navigation.init();
            swiper.navigation.update();
            }
        }, [swiper]);

        return (
            <>
                <div className="swiper-button" ref={prevRef}>prev</div>
                <Swiper
                    modules={[Navigation]}
                    navigation={true}
                    onSwiper={(swiper) => setSwiper(swiper)}
                    className="mySwiper">
                <SwiperSlide>Slide 1</SwiperSlide>
                <SwiperSlide>Slide 2</SwiperSlide>
                <SwiperSlide>Slide 3</SwiperSlide>
                <SwiperSlide>Slide 4</SwiperSlide>
                <SwiperSlide>Slide 5</SwiperSlide>
                </Swiper>
                <div className="swiper-button" ref={nextRef}>next</div>
            </>
        );
    }
    ```