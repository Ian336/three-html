<script setup>
import { onMounted, ref } from 'vue'
import * as THREE from 'three'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls'
const scene = new THREE.Scene()
const camera = new THREE.PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  1000
)
camera.position.z = 100
scene.add(camera)
const axesHelper = new THREE.AxesHelper(100)
scene.add(axesHelper)

const arr = []
// const geometry = new THREE.BufferGeometry()

const arc = new THREE.CatmullRomCurve3([
  new THREE.Vector3(-50, 20, 90),
  new THREE.Vector3(-10, 40, 40),
  new THREE.Vector3(0, 0, 0),
  new THREE.Vector3(60, -60, 0),
  new THREE.Vector3(70, 0, 80),
])
const geometry = new THREE.TubeGeometry(arc, 40, 2, 30)
// const points = arc.getPoints(50)
// geometry.setFromPoints(points)
// const r = 100
// const n = 50
// const sp = (2 * Math.PI) / n
// for (let i = 0; i < n + 1; i++) {
//   var angle = i * sp
//   const x = r * Math.cos(angle)
//   const y = r * Math.sin(angle)
//   arr.push(x, y, 0)
// }
// const vertices = new Float32Array(arr)
// const attribute = new THREE.BufferAttribute(vertices, 3)
// geometry.attributes.position = attribute
const material = new THREE.MeshLambertMaterial({
  color: 0xff0000,
  side: THREE.DoubleSide,
})
const line = new THREE.Mesh(geometry, material)
const ambient = new THREE.AmbientLight(0xffffff, 0.5)
scene.add(ambient)
const directionalLight = new THREE.DirectionalLight(0xffffff, 1)
directionalLight.position.set(100, 60, 50)
scene.add(directionalLight)
scene.add(line)
const renderer = new THREE.WebGLRenderer()
renderer.setSize(window.innerWidth, window.innerHeight)
const controls = new OrbitControls(camera, renderer.domElement)
onMounted(() => {
  document.body.appendChild(renderer.domElement)
  function render() {
    renderer.render(scene, camera)
    requestAnimationFrame(render)
  }
  render()
})
// const box=new THREE.BoxGeometry(1,1,1)
// const material=new THREE.MeshBasicMaterial({color:16776960})
// const cube=new THREE.Mesh(box,material)
// cube.position.x=1
// // cube.rotation.set(Math.PI/4,0,0)

// scene.add(cube)
// const render=new THREE.WebGLRenderer()
// render.setSize( window.innerWidth, window.innerHeight );
// console.log(render);
// document.body.appendChild( render.domElement )

// const ray=new THREE.Ray()

// ray.origin.set(1,0,3)
// ray.direction=new THREE.Vector3(1,0,0)
// const p1=new THREE.Vector3(100,25,0)
// const p2=new THREE.Vector3(100,-25,25)
// const p3=new THREE.Vector3(100,-25,-25)
// const point=new THREE.Vector3()
// const result=ray.intersectTriangle(p1,p2,p3,false,point)
// console.log(result,point);
// // render.render(scene,camera)
// const axesHelper=new THREE.AxesHelper(10)
// scene.add(axesHelper)

// const controls=new OrbitControls(camera,render.domElement )

// function render1(){
//   // cube.position.x=cube.position.x+0.1
//   if(cube.position.x>=10){
//     cube.position.x=0
//   }
//   render.render(scene,camera)
//   requestAnimationFrame(render1)
// }

// render1()

// init

// const camera = new THREE.PerspectiveCamera( 70, window.innerWidth / window.innerHeight, 0.01, 10 );
// camera.position.z = 1;

// const scene = new THREE.Scene();

// const geometry = new THREE.BoxGeometry( 0.2, 0.2, 0.2 );
// const material = new THREE.MeshNormalMaterial();

// const mesh = new THREE.Mesh( geometry, material );
// scene.add( mesh );

// const renderer = new THREE.WebGLRenderer( { antialias: true } );
// renderer.setSize( window.innerWidth, window.innerHeight );
// renderer.setAnimationLoop( animation );
// document.body.appendChild( renderer.domElement );

// // animation

// function animation( time ) {

// 	mesh.rotation.x = time / 2000;
// 	mesh.rotation.y = time / 1000;

// 	renderer.render( scene, camera );

// }

// const count = ref(0)
// const test=()=>{
//   xuzhi.requestFullscreen()
// }
onMounted(() => {
  // const canvas = document.getElementById('canvas')
  // const ctx = canvas.getContext('2d')
  // let r = 500
  // let angle = 360
  const render = () => {
    ctx.clearRect(0, 0, canvas.width, canvas.height)
    angle -= 0.1
    r -= 0.7

    ctx.beginPath()
    // ctx.moveTo(500, 500)
    // ctx.translate(40,40)
    const x = r * Math.cos(angle)
    const y = r * Math.sin(angle)
    ctx.arc(x + 500, y + 500, 20, 0, Math.PI * 2)

    ctx.strokeStyle = 'green'
    ctx.stroke()
    ctx.closePath()
    requestAnimationFrame(render)
  }
  // render()
  // ctx.strokeStyle='red'
  // ctx.fillStyle='red'

  // ctx.lineTo(5,40)
  // ctx.lineTo(45,40)
  // ctx.lineTo(45,5)
  // ctx.closePath()
  // ctx.translate(20,20)
  // ctx.lineTo(10,10)
  // ctx.lineTo(10,10)
  // ctx.fill()
})
</script>

<template>
  <!-- <canvas
    id="canvas"
    width="1000"
    height="800"
   
  ></canvas> -->
  <!-- <div id="xuzhi" @click="test">12999</div>
  <div style="background: radial-gradient(ellipse at left , #0000ff, #ff0000);width: 100px;height: 100px;">
    14214214
  </div> -->
  <div></div>
</template>
