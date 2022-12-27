1. Next.js 설치

    ```
    npx create-next-app@latest --typescript
    ```

2. Three.js + fiber + drei 설치

    ```
    npm install three @types/three @react-three/fiber @react-three/drei
    ```

3. mesh 생성

    ```
    import * as THREE from 'three'
    import * as React from 'react'
    import { useRef, useState } from 'react'
    import { useFrame } from '@react-three/fiber'
    import { a, useSpring } from "@react-spring/three"

    export default function SphereStandardMesh(props: JSX.IntrinsicElements['mesh']) {
        const ref = useRef<THREE.Mesh>(null!)
        const [hovered, hover] = useState(false)
        const { scale, opacity } = useSpring({ scale: hovered ? 1.2 : 1, opacity: hovered ? 0.0 : 1.0 })

        useFrame((state, delta) => {
            ref.current.rotation.x = 0.01
        })

        return (
            // @ts-ignore
            <a.mesh
                {...props}
                ref={ref}
                scale={scale}
                onPointerOver={(event) => hover(true)}
                onPointerOut={(event) => hover(false)} >
                <sphereGeometry args={[1, 20, 15]} />
                <a.meshStandardMaterial
                    color={'gray'}
                    opacity={opacity}
                    flatShading
                    transparent />
            </a.mesh>
        )
    }
    ```

4. scene, 카메라, 조명, mesh 생성 및 렌더링

    ```
    import * as React from 'react'
    import { Canvas } from '@react-three/fiber'
    import Style from 'styles/Home.module.css'
    import Mesh from '../mesh/SphereStandardMesh';


    export default function Home() {
        return (
            // scene 생성
            <div className={Style.scene}>
                // 카메라 생성
                <Canvas camera={{position: [0, 0, 3]}}>
                    // 조명 생성
                    <ambientLight intensity={0.5}/>
                    <spotLight position={[10, 10, 10]} angle={0.15} penumbra={1}/>
                    // mesh 생성
                    <Mesh position={[0, 0, 0]}/>
                </Canvas>
            </div>
        )
    }
    ```