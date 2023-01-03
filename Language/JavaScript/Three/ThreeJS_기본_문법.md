실제로 Three.js로 무엇이든 표시할 수 있으려면 카메라로 장면을 렌더링 할 수 있도록 장면, 카메라 및 렌더러의 세 가지가 필요

```
// Scene 생성
const scene = new THREE.Scene();
// Camera 생성 및 설정 (field of view, aspect ratio, near, far)
// field of wiew(FOV) : 주어진 순간에 디스플레이에 표시되는 장면의 범위로 값은 도 단위
// aspect ratio : 이미지가 찌그러져 보이는 것을 방지하기 위해 대부분 요소의 너비를 높이로 나눈 값을 사용
// near : near 값보다 카메라에 가까이 있는 개체는 렌더링되지 않음
// far : far 값보다 카메라에 멀리 떨어져 있는 개체는 렌더링되지 않음
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

// Renderer 생성
const renderer = new THREE.WebGLRenderer();
// Rendering 할 크기를 설정
renderer.setSize( window.innerWidth, window.innerHeight );
// HTML 문서에 요소를 추가
document.body.appendChild( renderer.domElement );
```

Scene에 개체 추가

```
// 큐브 형태의 기하학적 구조
const geometry = new THREE.BoxGeometry( 1, 1, 1 );
// 개체의 재질 및 그에 적용될 속성 개체
const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
// 기하학적 형상을 취하고 재질을 적용한 개체
const cube = new THREE.Mesh( geometry, material );
// 생성된 개체를 호출
scene.add( cube );

camera.position.z = 5;
```

아직 렌더링을 하지 않았기 때문에 아무것도 볼 수 없으므로 render or animate loop 를 사용하여 화면이 새로 고쳐질 때마다 렌더러가 장면을 그리는 루프를 생성 (일반적으로 초당 60회)

```
function animate() {
	requestAnimationFrame( animate );

    // 애니메이션 추가
    cube.rotation.x += 0.01;
    cube.rotation.y += 0.01;

	renderer.render( scene, camera );
}
animate();
```

참고자료 : three.js 공식 문서

```
https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene
```