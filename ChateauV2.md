<!DOCTYPE html>
<html lang="en">
	<head>
		<title>Chateau Benji-Cyril</title>
		<meta charset="utf-8">
		<meta name="Chateau Benji-Cyril" content="width=device-width, user-scalable=no, minimum-scale=1.0, maximum-scale=1.0">
		<style>
			body {
				margin: 0px;
				background-color: #FFFFFF;
				overflow: hidden;
			}
		</style>
	</head>
	<body>

		<script src="three.js"></script>
    <script src="OrbitControls.js"></script> <!-- Controle de la souris -->

		<script>
			var camera, controls, scene, renderer;
			var mesh;
			init();
			animate();






			function init() {

				camera = new THREE.PerspectiveCamera( 70, window.innerWidth / window.innerHeight, 1, 10000 );
				controls = new THREE.OrbitControls( camera );//Controle par souris
				camera.position.set(50, 400, 350);
				controls.update();



				scene = new THREE.Scene();
//				var texture = new THREE.TextureLoader().load( 'hardwood2_roughness.jpg' );
				var texture = new THREE.TextureLoader().load( 'brick2.jpg' );
				var briquesBl = new THREE.TextureLoader().load('briquesbl.jpg');
				var textureBrRo = new THREE.TextureLoader().load('brickRo.jpg');

/* ************************* La texture ************************* */
				var material = new THREE.MeshBasicMaterial( { map: texture } );
				var couleurPlateau = new THREE.MeshBasicMaterial( {color: 0xffff00} );
				var matBriquesBleues = new THREE.MeshBasicMaterial({map : briquesBl});
				var matBriquesRoses = new THREE.MeshBasicMaterial({map: textureBrRo});



/* ************ Le plateau ************ */
				var plateau = new THREE.BoxBufferGeometry(1000, 2, 1500);

				affplateau = new THREE.Mesh(plateau, couleurPlateau);
				affplateau.position.set(0, -25, -150);

				scene.add(affplateau);




/********************* Partie Avant (portail) RDC **********************/

				var murAvantDroit = new THREE.BoxBufferGeometry( 30, 150, 15); 
				affmurAvantDroit = new THREE.Mesh(murAvantDroit, material);
				affmurAvantDroit.position.set(40, 50, 0);

				var murAvantGauche = new THREE.BoxBufferGeometry( 30, 150, 15);
				affmurAvantGauche = new THREE.Mesh(murAvantGauche, material);
				affmurAvantGauche.position.set(-40, 50, 0);

				var murAvantDroitP = new THREE.BoxBufferGeometry( 15, 150, 40);
				affmurAvantDroitP = new THREE.Mesh(murAvantDroitP, material);
				affmurAvantDroitP.position.set(35, 50, 25);

				var murAvantGaucheP = new THREE.BoxBufferGeometry( 15, 150, 40);
				affmurAvantGaucheP = new THREE.Mesh(murAvantGaucheP, material);
				affmurAvantGaucheP.position.set(-35, 50, 25);

				var tourRDCAvantDroite = new THREE.CylinderGeometry( 20, 20 , 180, 32);
				affTourRDCAvantDroite = new THREE.Mesh(tourRDCAvantDroite, material);
				affTourRDCAvantDroite.position.set(70, 65, 0);

				var toitTourRDCAvantDroit = new THREE.ConeGeometry( 30, 55, 30 );
				affToitTourRDCAvantDroit = new THREE.Mesh(toitTourRDCAvantDroit, matBriquesBleues);
				affToitTourRDCAvantDroit.position.set(70, 180, 0);

				var tourRDCAvantDroitP2 = new THREE.CylinderGeometry( 30, 30 , 30, 32);
				affTourRDCAvantDroitP2 = new THREE.Mesh(tourRDCAvantDroitP2, matBriquesBleues);
				affTourRDCAvantDroitP2.position.set(70, 125, 0);

				var tourRDCAvantGauche = new THREE.CylinderGeometry( 20, 20 , 180, 32);
				affTourRDCAvantGauche = new THREE.Mesh(tourRDCAvantGauche, material);
				affTourRDCAvantGauche.position.set(-70, 65, 0);

				var tourRDCAvantGaucheP2 = new THREE.CylinderGeometry( 30, 30 , 30, 32);
				affTourRDCAvantGaucheP2 = new THREE.Mesh(tourRDCAvantGaucheP2, matBriquesBleues);
				affTourRDCAvantGaucheP2.position.set(-70, 125, 0);

				var toitTourRDCAvantGauche = new THREE.ConeGeometry( 30, 55, 30 );
				affToitTourRDCAvantGauche = new THREE.Mesh(toitTourRDCAvantGauche, matBriquesBleues);
				affToitTourRDCAvantGauche.position.set(-70, 180, 0);

				scene.add(affmurAvantDroit, affmurAvantGauche, affTourRDCAvantDroite, affTourRDCAvantDroitP2, affToitTourRDCAvantDroit, affTourRDCAvantGauche, affTourRDCAvantGaucheP2, affToitTourRDCAvantGauche, affmurAvantDroitP, affmurAvantGaucheP);

/********************* Partie Avant(Sans portail) RDC **********************/


				var murAvantDroitSP = new THREE.BoxBufferGeometry( 150, 150, 15);
				affmurAvantDroitSP = new THREE.Mesh(murAvantDroitSP, material);
				affmurAvantDroitSP.position.set(160, 50, -30);
				affmurAvantDroitSP.rotation.y += 60;

				var murAvantGaucheSP = new THREE.BoxBufferGeometry( 150, 150, 15);
				affmurAvantGaucheSP = new THREE.Mesh(murAvantGaucheSP, material);
				affmurAvantGaucheSP.position.set(-160, 50, -30);
				affmurAvantGaucheSP.rotation.y += -60;

				var tourRDCAvantDroiteSP = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCAvantDroiteSP = new THREE.Mesh(tourRDCAvantDroiteSP, material);
				affTourRDCAvantDroiteSP.position.set(250, 65, -55);

				var toitTourRDCAvantDroitSP = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCAvantDroitSP = new THREE.Mesh(toitTourRDCAvantDroitSP, matBriquesBleues);
				affToitTourRDCAvantDroitSP.position.set(250, 185, -55);

				var tourRDCAvantGaucheSP = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCAvantGaucheSP = new THREE.Mesh(tourRDCAvantGaucheSP, material);
				affTourRDCAvantGaucheSP.position.set(-250, 65, -55);

				var toitTourRDCAvantGaucheSP = new THREE.ConeGeometry( 40, 70, 40);
				affToitTourRDCAvantGaucheSP = new THREE.Mesh(toitTourRDCAvantGaucheSP, matBriquesBleues);
				affToitTourRDCAvantGaucheSP.position.set(-250, 185, -55);


				scene.add(affmurAvantDroitSP, affmurAvantGaucheSP, affTourRDCAvantDroiteSP, affToitTourRDCAvantDroitSP, affTourRDCAvantGaucheSP, affToitTourRDCAvantGaucheSP);


/********************* Partie RDC droit *********************/

				var murRDCDroitP1 = new THREE.BoxBufferGeometry( 180, 150, 15);
				affmurRDCDroitP1 = new THREE.Mesh(murRDCDroitP1, material);
				affmurRDCDroitP1.position.set(290, 50, -110);
				affmurRDCDroitP1.rotation.y += 20;

				var tourCarréeRDCDroit = new THREE.BoxBufferGeometry(80, 180, 80);
				afftourCarréeRDCDroit = new THREE.Mesh(tourCarréeRDCDroit, material);
				afftourCarréeRDCDroit.position.set(350, 65, -220);
				afftourCarréeRDCDroit.rotation.y += 20;

				var murRDCDroitP2 = new THREE.BoxBufferGeometry( 15, 150, 120);
				affmurRDCDroitP2 = new THREE.Mesh(murRDCDroitP2, material);
				affmurRDCDroitP2.position.set(350, 50, -322);

				var tourRDCDroitCylindreP1 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCDroitCylindreP1 = new THREE.Mesh(tourRDCDroitCylindreP1, material);
				affTourRDCDroitCylindreP1.position.set(350, 65, -410);

				var toitTourRDCDroitCylindriqueP1 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCDroitCylindriqueP1 = new THREE.Mesh(toitTourRDCDroitCylindriqueP1, matBriquesBleues);
				affToitTourRDCDroitCylindriqueP1.position.set(350, 185, -410);

				var murRDCDroitP3 = new THREE.BoxBufferGeometry( 15, 150, 60);
				affmurRDCDroitP3 = new THREE.Mesh(murRDCDroitP3, material);
				affmurRDCDroitP3.position.set(350, 50, -460);

				var murRDCDroitP4 = new THREE.BoxBufferGeometry( 15, 150, 100);
				affmurRDCDroitP4 = new THREE.Mesh(murRDCDroitP4, material);
				affmurRDCDroitP4.position.set(323, 50, -528);
				affmurRDCDroitP4.rotation.y += 10;


				scene.add(affmurRDCDroitP1, afftourCarréeRDCDroit, affmurRDCDroitP2, affTourRDCDroitCylindreP1, affToitTourRDCDroitCylindriqueP1, affmurRDCDroitP3, affmurRDCDroitP4);


/********************* Partie RDC Gauche *********************/

				var murRDCGaucheP1 = new THREE.BoxBufferGeometry( 60, 150, 15);
				affmurRDCGaucheP1 = new THREE.Mesh(murRDCGaucheP1, material);
				affmurRDCGaucheP1.position.set(-290, 50, -90);
				affmurRDCGaucheP1.rotation.y -= 10;

				var murRDCGaucheP2 = new THREE.BoxBufferGeometry(15, 150, 120);
				affmurRDCGaucheP2 = new THREE.Mesh(murRDCGaucheP2, material);
				affmurRDCGaucheP2.position.set(-313, 50, -162);

				var tourRDCGaucheCylindreP1 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCGaucheCylindreP1 = new THREE.Mesh(tourRDCGaucheCylindreP1, material);
				affTourRDCGaucheCylindreP1.position.set(-313, 65, -250);

				var toitTourRDCGaucheCylindriqueP1 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCGaucheCylindriqueP1 = new THREE.Mesh(toitTourRDCGaucheCylindriqueP1, matBriquesBleues);
				affToitTourRDCGaucheCylindriqueP1.position.set(-313, 185, -250);

				var murRDCGaucheP3 = new THREE.BoxBufferGeometry(15, 150, 120);
				affmurRDCGaucheP3 = new THREE.Mesh(murRDCGaucheP3, material);
				affmurRDCGaucheP3.position.set(-313, 50, -340);

				var tourCarréeRDCDroit = new THREE.BoxBufferGeometry(80, 180, 80);
				afftourCarréeRDCDroit = new THREE.Mesh(tourCarréeRDCDroit, material);
				afftourCarréeRDCDroit.position.set(350, 65, -220);
				afftourCarréeRDCDroit.rotation.y += 20;

				var tourRDCGaucheCylindreP2 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCGaucheCylindreP2 = new THREE.Mesh(tourRDCGaucheCylindreP2, material);
				affTourRDCGaucheCylindreP2.position.set(-313, 65, -400);

				var toitTourRDCGaucheCylindriqueP2 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCGaucheCylindriqueP2 = new THREE.Mesh(toitTourRDCGaucheCylindriqueP2, matBriquesBleues);
				affToitTourRDCGaucheCylindriqueP2.position.set(-313, 185, -400);

				var murRDCGaucheP4 = new THREE.BoxBufferGeometry(15, 150, 180);
				affmurRDCGaucheP4 = new THREE.Mesh(murRDCGaucheP4, material);
				affmurRDCGaucheP4.position.set(-313, 50, -450);

				var tourCarréeRDCGauche = new THREE.BoxBufferGeometry(80, 180, 80);
				afftourCarréeRDCGauche = new THREE.Mesh(tourCarréeRDCGauche, material);
				afftourCarréeRDCGauche.position.set(-320, 65, -570);



				scene.add(affmurRDCGaucheP1, affmurRDCGaucheP2, affTourRDCGaucheCylindreP1, affToitTourRDCGaucheCylindriqueP1, affmurRDCGaucheP3, affTourRDCGaucheCylindreP2, affToitTourRDCGaucheCylindriqueP2, affmurRDCGaucheP4, afftourCarréeRDCGauche);


/********************* Partie RDC Arriere *********************/


				var murRDCArriereP1 = new THREE.BoxBufferGeometry(15, 150, 150);
				affmurRDCArriereP1 = new THREE.Mesh(murRDCArriereP1, material);
				affmurRDCArriereP1.position.set(228, 50, -589);
				affmurRDCArriereP1.rotation.y -= 5;

				var murRDCArriereP2 = new THREE.BoxBufferGeometry(60, 150, 15);
				affmurRDCArriereP2 = new THREE.Mesh(murRDCArriereP2, material);
				affmurRDCArriereP2.position.set(68, 50, -605);

				var tourRDCArriereCylindreP1 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCArriereCylindreP1 = new THREE.Mesh(tourRDCArriereCylindreP1, material);
				affTourRDCArriereCylindreP1.position.set(128, 65, -610);

				var toitTourRDCArriereCylindriqueP1 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCArriereCylindriqueP1 = new THREE.Mesh(toitTourRDCArriereCylindriqueP1, matBriquesBleues);
				affToitTourRDCArriereCylindriqueP1.position.set(128, 185, -610);

				var tourCarréeRDCArriere = new THREE.BoxBufferGeometry(80, 180, 80);
				afftourCarréeRDCArriere = new THREE.Mesh(tourCarréeRDCArriere, material);
				afftourCarréeRDCArriere.position.set(0, 65, -630);

				var murRDCArriereP3 = new THREE.BoxBufferGeometry(60, 150, 15);
				affmurRDCArriereP3 = new THREE.Mesh(murRDCArriereP3, material);
				affmurRDCArriereP3.position.set(-68, 50, -605);

				var tourRDCArriereCylindreP2 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCArriereCylindreP2 = new THREE.Mesh(tourRDCArriereCylindreP2, material);
				affTourRDCArriereCylindreP2.position.set(-128, 65, -610);

				var toitTourRDCArriereCylindriqueP2 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCArriereCylindriqueP2 = new THREE.Mesh(toitTourRDCArriereCylindriqueP2, matBriquesBleues);
				affToitTourRDCArriereCylindriqueP2.position.set(-128, 185, -610);

				var murRDCArriereP4 = new THREE.BoxBufferGeometry(15, 150, 150);
				affmurRDCArriereP4 = new THREE.Mesh(murRDCArriereP4, material);
				affmurRDCArriereP4.position.set(-228, 50, -589);
				affmurRDCArriereP4.rotation.y += 5;



				scene.add(affmurRDCArriereP1, afftourCarréeRDCArriere, affTourRDCArriereCylindreP1, affToitTourRDCArriereCylindriqueP1, affmurRDCArriereP2, affmurRDCArriereP3, affTourRDCArriereCylindreP2, affToitTourRDCArriereCylindriqueP2, affmurRDCArriereP4);




/********************* Partie 1erEtage *********************/

				var partieAvant1erEtageBase = new THREE.BoxBufferGeometry(150, 250, 150);
				affPartieAvant1erEtageBase = new THREE.Mesh(partieAvant1erEtageBase, material);
				affPartieAvant1erEtageBase.position.set(0, 100, -160);

				var partieAvant1erEtageHaut = new THREE.BoxBufferGeometry(190, 60, 130);
				affpartieAvant1erEtageHaut = new THREE.Mesh(partieAvant1erEtageHaut, material);
				affpartieAvant1erEtageHaut.position.set(0, 216, -130);

				var partieAvant1erEtageHautDroit = new THREE.BoxBufferGeometry(30, 60, 150);
				affpartieAvant1erEtageHautDroit = new THREE.Mesh(partieAvant1erEtageHautDroit, material);
				affpartieAvant1erEtageHautDroit.position.set(80, 216, -150);

				var partieAvant1erEtageHautGauche = new THREE.BoxBufferGeometry(30, 60, 150);
				affpartieAvant1erEtageHautGauche = new THREE.Mesh(partieAvant1erEtageHautGauche, material);
				affpartieAvant1erEtageHautGauche.position.set(-80, 216, -150);

	            var pyramidgeometry = new THREE.CylinderGeometry(30, 135, 70, 4, false);
	            pyramid = new THREE.Mesh(pyramidgeometry, matBriquesBleues);
	            pyramid.position.set(0, 282, -160);
	            pyramid.rotation.y += 2.35;

				var tourAvant1erEtageDroit = new THREE.CylinderGeometry( 15, 15, 60, 32);
				affTourAvant1erEtageDroit = new THREE.Mesh(tourAvant1erEtageDroit, material);
				affTourAvant1erEtageDroit.position.set(-95, 230, -55);

				var toitTourAvant1erEtageDroit = new THREE.ConeGeometry( 18, 30, 18);
				affToitTourAvant1erEtageDroit = new THREE.Mesh(toitTourAvant1erEtageDroit, matBriquesBleues);
				affToitTourAvant1erEtageDroit.position.set(-95, 275, -55);

				var tourAvant1erEtageGauche = new THREE.CylinderGeometry( 15, 15, 60, 32);
				affTourAvant1erEtageGauche = new THREE.Mesh(tourAvant1erEtageGauche, material);
				affTourAvant1erEtageGauche.position.set(95, 230, -55);

				var toitTourAvant1erEtageGauche = new THREE.ConeGeometry( 18, 30, 18);
				affToitTourAvant1erEtageGauche = new THREE.Mesh(toitTourAvant1erEtageGauche, matBriquesBleues);
				affToitTourAvant1erEtageGauche.position.set(95, 275, -55);

				var partieBase1erEtage = new THREE.BoxBufferGeometry(500, 180, 200);
				affPartieBase1erEtage = new THREE.Mesh(partieBase1erEtage, material);
				affPartieBase1erEtage.position.set(0, 65, -250);

	            var pyramidgeometry2 = new THREE.CylinderGeometry(80, 150, 70, 4, false);
	            pyramid2 = new THREE.Mesh(pyramidgeometry2, matBriquesBleues);
	            pyramid2.position.set(150, 190, -250);
	            pyramid2.rotation.y += 2.35;

				var tourPyramidGeometry2 = new THREE.CylinderGeometry( 12, 12, 80, 32);
				affTourPyramidGeometry2 = new THREE.Mesh(tourPyramidGeometry2, material);
				affTourPyramidGeometry2.position.set(160, 230, -230);

				var toitTourPyramidGeometry2 = new THREE.ConeGeometry( 15, 30, 15);
				affToitTourPyramidGeometry2 = new THREE.Mesh(toitTourPyramidGeometry2, matBriquesBleues);
				affToitTourPyramidGeometry2.position.set(160, 280, -230);

				var partieBase1erEtagePart2 = new THREE.BoxBufferGeometry(200, 50, 200);
				affPartieBase1erEtagePart2 = new THREE.Mesh(partieBase1erEtagePart2, material);
				affPartieBase1erEtagePart2.position.set(-150, 180, -250);

	            var pyramidgeometry3 = new THREE.CylinderGeometry(80, 150, 70, 4, false);
	            pyramid3 = new THREE.Mesh(pyramidgeometry3, matBriquesBleues);
	            pyramid3.position.set(-150, 240, -250);
	            pyramid3.rotation.y += 2.35;



				scene.add(affPartieAvant1erEtageBase, affpartieAvant1erEtageHaut, affpartieAvant1erEtageHautDroit, affpartieAvant1erEtageHautGauche, pyramid, affTourAvant1erEtageDroit, affToitTourAvant1erEtageDroit, affTourAvant1erEtageGauche, affToitTourAvant1erEtageGauche, affPartieBase1erEtage, pyramid2, affTourPyramidGeometry2, affToitTourPyramidGeometry2, affPartieBase1erEtagePart2, pyramid3);























































				renderer = new THREE.WebGLRenderer();
				renderer.setPixelRatio( window.devicePixelRatio );
				renderer.setSize( window.innerWidth, window.innerHeight );
				document.body.appendChild( renderer.domElement );
				//
				window.addEventListener( 'resize', onWindowResize, false );
			}




			function onWindowResize() {
				camera.aspect = window.innerWidth / window.innerHeight;
				camera.updateProjectionMatrix();
				renderer.setSize( window.innerWidth, window.innerHeight );
			}


			function animate() {
				requestAnimationFrame( animate );
				controls.update();
				renderer.render( scene, camera );
			}


		</script>

	</body>
</html>
