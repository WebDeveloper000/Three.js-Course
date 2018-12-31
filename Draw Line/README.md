Three.js Course

2. Drawing Lines

- Creating the scene

    Let's say you want to draw a line or a circle, not a wireframe Mesh. First we need to setup the renderer, scene and camera

        var renderer = new THREE.WebGLRenderer();
        renderer.setSize( window.innerWidth, window.innerHeight );
        document.body.appendChild( renderer.domElement );

        var camera = new THREE.PerspectiveCamera( 45, window.innerWidth / window.innerHeight, 1, 500 );
        camera.position.set( 0, 0, 100 );
        camera.lookAt( 0, 0, 0 );

        var scene = new THREE.Scene();

- Adding Line Material

    Next thing we will do is define a material. For lines we have to use LineBasicMaterial or LineDashedMaterial.

        //create a blue LineBasicMaterial
        var material = new THREE.LineBasicMaterial( { color: 0x0000ff } );

- Creating Geometry and Line
    After material we will need a Geometry or BufferGeometry with some vertices (it's recommended to use a BufferGeometry as it's more performant, however for simplicity we'll use a Geometry here):

        var geometry = new THREE.Geometry();
        geometry.vertices.push(new THREE.Vector3( -10, 0, 0) );
        geometry.vertices.push(new THREE.Vector3( 0, 10, 0) );
        geometry.vertices.push(new THREE.Vector3( 10, 0, 0) );
    
    Note that lines are drawn between each consecutive pair of vertices, but not between the first and last (the line is not closed.)

    Now that we have points for two lines and a material, we can put them together to form a line.

        var line = new THREE.Line( geometry, material );

- Adding line to scene and call render

        scene.add( line );
        renderer.render( scene, camera );


