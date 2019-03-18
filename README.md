# explore-threejs

### install
```
npm i http-server -g
http-server -p 8888
```

### Api

```js
/**
 * The Scene
 */
const scene = new THREE.Scene();
```

```js
/**
 * The Camera
 * @param {Number} fov The vertical field of view. This dictates the size of the vertical space your camera's view can reach.
 * @param {Number} aspect This is the aspect ratio you use to create the horizontal field of view based off the vertical.
 * @param {Number} near This is the nearest plane of view (where the camera's view begins).
 * @param {Number} far This is the far plane of view (where the camera's view ends).
 */
const camera = new THREE.PerspectiveCamera(80, window.innerWidth / window.innerHeight, 0.25, 100);
/**
 * The Camera position
 * @param {Number} x
 * @param {Number} y
 * @param {Number} z
 */
camera.position.set(-20, 20, 20);
```

```js
/**
 * The Renderer
 */
const renderer = new THREE.WebGLRenderer();
/**
 * The Renderer
 * @param scene
 * @param camera
 */
renderer.render( scene, camera );
/**
 * The Renderer Animation
 * @function requestAnimationFrame 有很多的优点。最重要的一点或许就是当用户切换到其它的标签页时，它会暂停，因此不会浪费用户宝贵的处理器资源，以及损耗电池的使用寿命。
 */
function animate() {
    requestAnimationFrame( animate );
    renderer.render( scene, camera );
}
animate();
```

```js
/**
 * The Controls
 * @param camera
 */
const controls = new THREE.OrbitControls(camera);
/**
 * The focus point of the controls, the .object orbits around this. It can be updated manually at any point to change the focus of the controls.
 * @param {Number} x
 * @param {Number} y
 * @param {Number} z
 */
controls.target.set(0, 0, 0);
/**
 * Update the controls. Must be called after any manual changes to the camera's transform, or in the update loop if .autoRotate or .enableDamping are set.
 */
controls.update();
```

```js
function onWindowResize() {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
}
window.addEventListener('resize', onWindowResize, false);
```

```js
// The Stats
const stats = new Stats();
//add into the dom container
container.appendChild(stats.dom);
//add into the animate function
stats.update();
```

```js
/**
 * The Line
 * @param geometry 几何点
 * @param material 材质
 */
const line = new THREE.Line( geometry, material );
```