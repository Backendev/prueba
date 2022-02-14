<template>
  <div id="canvas"></div>
</template>

<script>
import * as THREE from "three";

export default {
  name: "HelloWorld",
  data() {
    return {
      background: 0x0080ff,
      alpha: 0,
      canvas: "canvas",
      width: "100%",
      height: window.innerHeight+"px",
      pading:0
    };
  },
  methods: {

    init: function() {
      let container = document.getElementById(this.canvas);
      container.style.width = this.width;
      container.style.height = this.height;
      const light = new THREE.AmbientLight( 0x404040 );
      this.renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
      this.renderer.setClearColor(this.background, this.alpha);
      this.renderer.setSize(container.clientWidth, container.clientHeight);
      container.appendChild(this.renderer.domElement);
      this.scene = new THREE.Scene();
      //console.log(container.clientWidth / container.clientHeight);
      this.camera = new THREE.OrthographicCamera(
        container.clientWidth /-50,
        container.clientWidth /50,
        container.clientHeight/50,
        container.clientHeight/-50,
        1,
        100
      );

      this.camera.position.z = 10;

      this.scene = new THREE.Scene();
      // const bola = new PinaCollada('../assets/models/bola',1)
      //const loader = new ColladaLoader();
      const geometry = new THREE.BoxGeometry(1,1, 1);
      const material = new THREE.MeshNormalMaterial();
      const material2 = new THREE.MeshNormalMaterial();
      
      //this.pinaCollada('bola', 1.2);
      
      //this.pinaCollada2('bola',1,material2)
      //this.pinaCollada2('bola',1,material2)
      //this.scene.add(this.mesh2)
      //console.log(this.mesh2)
      this.mesh = new THREE.Mesh(geometry, material);
      this.scene.add(this.mesh);
      //this.scene.add(this.mesh2);
      this.scene.add(light)
      
      //this.loadOBJ()
      //this.loadOBJ2()
      //this.loadGLTF()








      this.ani();
    },
    ani: function() {
      // console.log("estoy ejecutandome");
      requestAnimationFrame(this.ani);
      this.mesh.rotation.z += 0.01;
      //this.mesh2.rotation.z += 0.01;
      this.mesh.rotation.x += 0.02;
      this.mesh.rotation.z += 0.03;
      this.renderer.render(this.scene, this.camera);
    },
  },
  mounted() {
    this.init();
  },
};
</script>
<style>
  
</style>