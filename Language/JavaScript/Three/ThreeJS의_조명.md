Three.js에서 조명은

DirectionalLight (태양광) 

AmbientLight (주변광)

HemisphereLight (반구빛)

PointLight (점광)

RectAreaLight (직역등)

SpotLight (스포트라이트)

등으로 여러가지 형태가 존재한다.


※ 사용 환경 : react + next.js + typescript + three.js + fiber + drei


1. DirectionalLight (태양광)

    ```
    // DirectionalLight (태양광)는 특정 방향으로 방출되는 빛으로
    // 광원으로부터 오는 모든 빛은 평행하며 무한하고 또한 그림자를 생성할 수 있다.
    
    <directionalLight
        color={색상: Color}
        intensity={밝기: Float}
        castShadow={그림자: Boolean}
        position={위치: Vector3}
        target={타겟: Object3D} />
    ```

2. AmbientLight (주변광)

    ```
    // AmbientLight (주변광)는 모든 개체를 모든 방향에서 동일하게 비추는 조명으로
    // 이 조명은 방향이 없기 때문에 그림자를 생성할 수 없다.
    
    <ambientLight
        color={색상: Color}
        intensity={밝기: Float} />
    ```

3. HemisphereLight (반구빛)

    ```
    // HemisphereLight (반구빛)는 하늘색에서 바닥색으로 색이 바래지는 조명으로
    // 그림자를 생성할 수 없다.
    
    <HemisphereLight
        color={하늘색: Color}
        groundColor={바닥색: Color}
        intensity={밝기: Float}
        position={위치: Vector3 } />
    ```

4. PointLight (점광)

    ```
    // PointLight (점광)는 광원으로부터 모든 방향으로 방출되는 조명으로
    // 그림자를 생성할 수 있다.
    
    <PointLight
        color={하늘색: Color}
        intensity={밝기: Float}
        castShadow={그림자: Boolean}
        type={타입: String}
        // distance에 대한 타입을 지정하며
        // Default(선형 감쇠)와 Physically(역제곱 감쇠)로 나뉜다.
        distance={거리: Float}
        // 광원으로부터 지정한 거리까지 밝기가 감쇠한다.
        decay={붕괴}
        // 빛의 거리에 따라 빛이 어두워지는 양으로
        // 물리적으로 올바른 렌더링을 위해 기본값을 변경하지 않도록 한다.
        power={전원}
        // 루멘(lm) 단위로 밝기를 변경한다.
        position={위치: Vector3 } />
    ```

5. RectAreaLight (직역등)

    ```
    // RectAreaLight (직역등)는 직사각형 평면의 면 전체에 균일하게 빛을 방출하는 조명으로
    // 그림자를 지원하지 않는다.
    
    <RectAreaLight
        color={하늘색: Color}
        intensity={밝기: Float}
        width={너비: Float}
        height={높이: Float}
        power={전원}
        // 루멘(lm) 단위로 밝기를 변경한다.
        position={위치: Vector3 } />
    ```

6. SpotLight (스포트라이트)

    ```
    // SpotLight (스포트라이트)는 광원에서 멀어질수록 크기가 커지는 원뿔 형태의 조명으로
    // 그림자를 생성할 수 있다.
    
    <SpotLight
        color={하늘색: Color}
        intensity={밝기: Float}
        castShadow={그림자: Boolean}
        angle={각도: Float}
        distance={거리: Float}
        // 광원으로부터 지정한 거리까지 밝기가 감쇠한다.
        type={타입: String}
        // distance에 대한 타입을 지정하며
        // Default(선형 감쇠)와 Physically(역제곱 감쇠)로 나뉜다.
        decay={붕괴}
        // 빛의 거리에 따라 빛이 어두워지는 양으로
        // 물리적으로 올바른 렌더링을 위해 기본값을 변경하지 않도록 한다.
        penumbra={반음부}
        power={전원}
        // 루멘(lm) 단위로 밝기를 변경한다.
        position={위치: Vector3 }
        target={타겟: Object3D} />
    ```

7. 참고자료 - Three.js 공식 문서

    ```
    https://threejs.org/docs/index.html
    ```