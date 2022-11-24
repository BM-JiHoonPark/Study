React / Next.js 에서 Swiper는 'swiper'와 'swiper/react' 두 가지로 나뉜다.

1. Swiper intall

    ```
    npm install swiper
    ```

2. 'swiper/react' import 시 문법

    ```
    import Swiper, { Navigation, Pagination } from 'swiper/react';

    import 'swiper/css';
    import 'swiper/css/navigation';
    import 'swiper/css/pagination';
    
    export default () => {
      return (
        <Swiper
          navigation={true}
          modules={[Navigation]}
          className="mySwiper">
            <SwiperSlide>Slide 1</SwiperSlide>
            <SwiperSlide>Slide 2</SwiperSlide>
            <SwiperSlide>Slide 3</SwiperSlide>
            <SwiperSlide>Slide 4</SwiperSlide>
            <SwiperSlide>Slide 5</SwiperSlide>
            <SwiperSlide>Slide 6</SwiperSlide>
            <SwiperSlide>Slide 7</SwiperSlide>
            <SwiperSlide>Slide 8</SwiperSlide>
            <SwiperSlide>Slide 9</SwiperSlide>
        </Swiper>
      );
    };
    ```

3. 'swiper' import 시 문법

    ```
    import Swiper, { Navigation, Pagination } from 'swiper';

    import 'swiper/css';
    import 'swiper/css/navigation';
    import 'swiper/css/pagination';
    
    export default () => {
      const swiper = new Swiper('.swiper', {
          modules: [Navigation, Pagination],
      });

      return (
        <div className={"swiper"}>
            <div className={"swiper-wrapper"}>
                <div className={"swiper-slide"}>Slide 1</div>
                <div className={"swiper-slide"}>Slide 2</div>
                <div className={"swiper-slide"}>Slide 3</div>
            </div>
        </div>
      );
    };
    ```


