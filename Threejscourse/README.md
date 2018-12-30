Three.js Course

1. Cube Animation
- Creating the scene
 To actually be able to display anything with three.js, we need three things: scene, camera and renderer, so that we can render the scene with camera.
 
    var scene = new THREE.Scene();
    var camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

    var renderer = new THREE.WebGLRenderer();
    renderer.setSize( window.innerWidth, window.innerHeight );
    document.body.appendChild( renderer.domElement );

 To create a cube, add the next code.

    var geometry = new THREE.BoxGeometry( 1, 1, 1 );
    var material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
    var cube = new THREE.Mesh( geometry, material );
    scene.add( cube );

    camera.position.z = 5;

- Rendering the scene

    If you copied the code from above into the HTML file we created earlier, you wouldn't be able to see anything. This is because we're not actually rendering anything yet. For that, we need what's called a render or animate loop.

    function animate() {
	requestAnimationFrame( animate );
	renderer.render( scene, camera );
    }
    animate();

    This will create a loop that causes the renderer to draw the scene every time the screen is refreshed (on a typical screen this means 60 times per second). If you're new to writing games in the browser, you might say "why don't we just create a setInterval ?" The thing is - we could, but requestAnimationFrame has a number of advantages. Perhaps the most important one is that it pauses when the user navigates to another browser tab, hence not wasting their precious processing power and battery life.

- Animating the cube

    If you insert all the code above into the file you created before we began, you should see a green box. Let's make it all a little more interesting by rotating it.

    Add the following right above the renderer.render call in your animate function:

    cube.rotation.x += 0.01;
    cube.rotation.y += 0.01;

    This will be run every frame (normally 60 times per second), and give the cube a nice rotation animation. Basically, anything you want to move or change while the app is running has to go through the animate loop. You can of course call other functions from there, so that you don't end up with a animate function that's hundreds of lines.
    

