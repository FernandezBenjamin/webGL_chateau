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
				controls.minPolarAngle = 0; // radians
				controls.maxPolarAngle = Math.PI/2;  // radians
				camera.position.set(0, 300, 600);
				controls.update();



				scene = new THREE.Scene();
//				var texture = new THREE.TextureLoader().load( 'hardwood2_roughness.jpg' );
				var texture = new THREE.TextureLoader().load( 'brick2.jpg' );
				var briquesBl = new THREE.TextureLoader().load('briquesbl.jpg');
				var textureBrRo = new THREE.TextureLoader().load('brickRo3.jpg');
				var textBriBlGr = new THREE.TextureLoader().load('briquesblgr.jpg');
				var textOr = new THREE.TextureLoader().load('or.jpg');
				var textGrille = new THREE.TextureLoader().load('grillev3.png');
				var textBl2 = new THREE.TextureLoader().load('briquesbl2.jpg');
				var textPelouse = new THREE.TextureLoader().load('pelouse.jpg');
				var textfenetre = new THREE.TextureLoader().load('fenetre.png');
				var textRoseFenetre = new THREE.TextureLoader().load('textRoseFenetre.png');
				var textRoseFenetre2 = new THREE.TextureLoader().load('textRoseFenetre2.png');

/* ************************* Le materiau ************************* */
				var material = new THREE.MeshBasicMaterial( { map: texture } );
				var couleurPlateau = new THREE.MeshBasicMaterial( {color: 0xffff00} );
				var matBriquesBleues = new THREE.MeshBasicMaterial({map : briquesBl});
				var matBriquesRoses = new THREE.MeshBasicMaterial({map: textureBrRo});
				var matBriBlGr = new THREE.MeshBasicMaterial({map : textBriBlGr});
				var matOr = new THREE.MeshBasicMaterial({map : textOr});
				var matGrille = new THREE.MeshBasicMaterial({map : textGrille});
				var matBl2 = new THREE.MeshBasicMaterial({map : textBl2});
				var matfenetre = new THREE.MeshBasicMaterial({map : textfenetre});
				var matRoseFene = new THREE.MeshBasicMaterial({map : textRoseFenetre});
				var matRoseFene2 = new THREE.MeshBasicMaterial({map : textRoseFenetre2});


/* ************ Le plateau ************ */
				var plateau = new THREE.BoxBufferGeometry(1000, 2, 1500);

				affplateau = new THREE.Mesh(plateau, couleurPlateau);
				affplateau.position.set(0, -25, -150);

//				scene.add(affplateau);




/********************* Partie Avant (portail) RDC **********************/

				var murAvantDroit = new THREE.BoxBufferGeometry( 30, 150, 15); 
				affmurAvantDroit = new THREE.Mesh(murAvantDroit, matBriBlGr);
				affmurAvantDroit.position.set(50, 50, 0);

				var murAvantGauche = new THREE.BoxBufferGeometry( 30, 150, 15);
				affmurAvantGauche = new THREE.Mesh(murAvantGauche, matBriBlGr);
				affmurAvantGauche.position.set(-50, 50, 0);

				var murAvantCentre = new THREE.BoxBufferGeometry( 80, 150, 15);
				affmurAvantCentre = new THREE.Mesh(murAvantCentre, matGrille);
				affmurAvantCentre.position.set(0, 50, 38);

				var murAvantDroitP = new THREE.BoxBufferGeometry( 15, 150, 40);
				affmurAvantDroitP = new THREE.Mesh(murAvantDroitP, matBriBlGr);
				affmurAvantDroitP.position.set(47, 50, 25);

				var murAvantGaucheP = new THREE.BoxBufferGeometry( 15, 150, 40);
				affmurAvantGaucheP = new THREE.Mesh(murAvantGaucheP, matBriBlGr);
				affmurAvantGaucheP.position.set(-47, 50, 25);

				var tourRDCAvantDroite = new THREE.CylinderGeometry( 20, 20 , 180, 32);
				affTourRDCAvantDroite = new THREE.Mesh(tourRDCAvantDroite, matBriBlGr);
				affTourRDCAvantDroite.position.set(70, 65, 0);

				var piedTourRDCAvantDroite = new THREE.ConeGeometry(35, 80, 35);
				affPiedTourRDCAvantDroite = new THREE.Mesh(piedTourRDCAvantDroite, matBriBlGr);
				affPiedTourRDCAvantDroite.position.set(70, 15, 0);

				var toitTourRDCAvantDroit = new THREE.ConeGeometry( 30, 55, 30 );
				affToitTourRDCAvantDroit = new THREE.Mesh(toitTourRDCAvantDroit, matBriquesBleues);
				affToitTourRDCAvantDroit.position.set(70, 180, 0);

				var tourRDCAvantDroitP2 = new THREE.CylinderGeometry( 30, 30 , 30, 32);
				affTourRDCAvantDroitP2 = new THREE.Mesh(tourRDCAvantDroitP2, matBriBlGr);
				affTourRDCAvantDroitP2.position.set(70, 125, 0);

				var tourRDCAvantGauche = new THREE.CylinderGeometry( 20, 20 , 180, 32);
				affTourRDCAvantGauche = new THREE.Mesh(tourRDCAvantGauche, matBriBlGr);
				affTourRDCAvantGauche.position.set(-70, 65, 0);

				var piedTourRDCAvantGauche = new THREE.ConeGeometry(35, 80, 35);
				affPiedTourRDCAvantGauche = new THREE.Mesh(piedTourRDCAvantGauche, matBriBlGr);
				affPiedTourRDCAvantGauche.position.set(-70, 15, 0);

				var tourRDCAvantGaucheP2 = new THREE.CylinderGeometry( 30, 30 , 30, 32);
				affTourRDCAvantGaucheP2 = new THREE.Mesh(tourRDCAvantGaucheP2, matBriBlGr);
				affTourRDCAvantGaucheP2.position.set(-70, 125, 0);

				var toitTourRDCAvantGauche = new THREE.ConeGeometry( 30, 55, 30 );
				affToitTourRDCAvantGauche = new THREE.Mesh(toitTourRDCAvantGauche, matBriquesBleues);
				affToitTourRDCAvantGauche.position.set(-70, 180, 0);





				scene.add(affmurAvantDroit, affmurAvantGauche, affTourRDCAvantDroite,affmurAvantCentre, affPiedTourRDCAvantDroite, affTourRDCAvantDroitP2, affToitTourRDCAvantDroit, affTourRDCAvantGauche, affPiedTourRDCAvantGauche, affTourRDCAvantGaucheP2, affToitTourRDCAvantGauche, affmurAvantDroitP, affmurAvantGaucheP);

/********************* Partie Avant(Sans portail) RDC **********************/


				var murAvantDroitSP = new THREE.BoxBufferGeometry( 150, 150, 15);
				affmurAvantDroitSP = new THREE.Mesh(murAvantDroitSP, matBriBlGr);
				affmurAvantDroitSP.position.set(160, 50, -30);
				affmurAvantDroitSP.rotation.y += 60;

				var murAvantGaucheSP = new THREE.BoxBufferGeometry( 150, 150, 15);
				affmurAvantGaucheSP = new THREE.Mesh(murAvantGaucheSP, matBriBlGr);
				affmurAvantGaucheSP.position.set(-160, 50, -30);
				affmurAvantGaucheSP.rotation.y += -60;

				var tourRDCAvantDroiteSP = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCAvantDroiteSP = new THREE.Mesh(tourRDCAvantDroiteSP, matBriBlGr);
				affTourRDCAvantDroiteSP.position.set(250, 65, -55);

				var piedTourRDCAvantDroiteSP = new THREE.ConeGeometry(40, 80, 40);
				affPiedTourRDCAvantDroiteSP = new THREE.Mesh(piedTourRDCAvantDroiteSP, matBriBlGr);
				affPiedTourRDCAvantDroiteSP.position.set(250, 15, -55);

				var toitTourRDCAvantDroitSP = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCAvantDroitSP = new THREE.Mesh(toitTourRDCAvantDroitSP, matBriquesBleues);
				affToitTourRDCAvantDroitSP.position.set(250, 185, -55);

				var tourRDCAvantGaucheSP = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCAvantGaucheSP = new THREE.Mesh(tourRDCAvantGaucheSP, matBriBlGr);
				affTourRDCAvantGaucheSP.position.set(-250, 65, -55);

				var piedTourRDCAvantGaucheSP = new THREE.ConeGeometry(35, 80, 35);
				affPiedTourRDCAvantGaucheSP = new THREE.Mesh(piedTourRDCAvantGaucheSP, matBriBlGr);
				affPiedTourRDCAvantGaucheSP.position.set(-250, 15, -55);

				var toitTourRDCAvantGaucheSP = new THREE.ConeGeometry( 40, 70, 40);
				affToitTourRDCAvantGaucheSP = new THREE.Mesh(toitTourRDCAvantGaucheSP, matBriquesBleues);
				affToitTourRDCAvantGaucheSP.position.set(-250, 185, -55);


				scene.add(affmurAvantDroitSP, affmurAvantGaucheSP, affTourRDCAvantDroiteSP, affPiedTourRDCAvantDroiteSP, affToitTourRDCAvantDroitSP, affTourRDCAvantGaucheSP, affPiedTourRDCAvantGaucheSP, affToitTourRDCAvantGaucheSP);


/********************* Partie RDC droit *********************/

				var murRDCDroitP1 = new THREE.BoxBufferGeometry( 180, 150, 15);
				affmurRDCDroitP1 = new THREE.Mesh(murRDCDroitP1, matBriBlGr);
				affmurRDCDroitP1.position.set(290, 50, -110);
				affmurRDCDroitP1.rotation.y += 20;

				var tourCarréeRDCDroit = new THREE.BoxBufferGeometry(80, 180, 80);
				afftourCarréeRDCDroit = new THREE.Mesh(tourCarréeRDCDroit, matBriBlGr);
				afftourCarréeRDCDroit.position.set(350, 65, -220);
				afftourCarréeRDCDroit.rotation.y += 20;

				var murRDCDroitP2 = new THREE.BoxBufferGeometry( 15, 150, 120);
				affmurRDCDroitP2 = new THREE.Mesh(murRDCDroitP2, matBriBlGr);
				affmurRDCDroitP2.position.set(350, 50, -322);

				var tourRDCDroitCylindreP1 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCDroitCylindreP1 = new THREE.Mesh(tourRDCDroitCylindreP1, matBriBlGr);
				affTourRDCDroitCylindreP1.position.set(350, 65, -410);

				var piedTourRDCDroitCylindreP1 = new THREE.ConeGeometry(35, 80, 35);
				affPiedTourRDCDroitCylindreP1 = new THREE.Mesh(piedTourRDCDroitCylindreP1, matBriBlGr);
				affPiedTourRDCDroitCylindreP1.position.set(350, 15, -410);

				var toitTourRDCDroitCylindriqueP1 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCDroitCylindriqueP1 = new THREE.Mesh(toitTourRDCDroitCylindriqueP1, matBriquesBleues);
				affToitTourRDCDroitCylindriqueP1.position.set(350, 185, -410);

				var murRDCDroitP3 = new THREE.BoxBufferGeometry( 15, 150, 60);
				affmurRDCDroitP3 = new THREE.Mesh(murRDCDroitP3, matBriBlGr);
				affmurRDCDroitP3.position.set(350, 50, -460);

				var murRDCDroitP4 = new THREE.BoxBufferGeometry( 15, 150, 100);
				affmurRDCDroitP4 = new THREE.Mesh(murRDCDroitP4, matBriBlGr);
				affmurRDCDroitP4.position.set(323, 50, -528);
				affmurRDCDroitP4.rotation.y += 10;


				scene.add(affmurRDCDroitP1, afftourCarréeRDCDroit, affmurRDCDroitP2, affTourRDCDroitCylindreP1, affPiedTourRDCDroitCylindreP1, affToitTourRDCDroitCylindriqueP1, affmurRDCDroitP3, affmurRDCDroitP4);


/********************* Partie RDC Gauche *********************/

				var murRDCGaucheP1 = new THREE.BoxBufferGeometry( 60, 150, 15);
				affmurRDCGaucheP1 = new THREE.Mesh(murRDCGaucheP1, matBriBlGr);
				affmurRDCGaucheP1.position.set(-290, 50, -90);
				affmurRDCGaucheP1.rotation.y -= 10;

				var murRDCGaucheP2 = new THREE.BoxBufferGeometry(15, 150, 120);
				affmurRDCGaucheP2 = new THREE.Mesh(murRDCGaucheP2, matBriBlGr);
				affmurRDCGaucheP2.position.set(-313, 50, -162);

				var tourRDCGaucheCylindreP1 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCGaucheCylindreP1 = new THREE.Mesh(tourRDCGaucheCylindreP1, matBriBlGr);
				affTourRDCGaucheCylindreP1.position.set(-313, 65, -250);

				var piedTourRDCGaucheCylindreP1 = new THREE.ConeGeometry(35, 80, 35);
				affPiedTourRDCGaucheCylindreP1 = new THREE.Mesh(piedTourRDCGaucheCylindreP1, matBriBlGr);
				affPiedTourRDCGaucheCylindreP1.position.set(-313, 15, -250);

				var toitTourRDCGaucheCylindriqueP1 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCGaucheCylindriqueP1 = new THREE.Mesh(toitTourRDCGaucheCylindriqueP1, matBriquesBleues);
				affToitTourRDCGaucheCylindriqueP1.position.set(-313, 185, -250);

				var murRDCGaucheP3 = new THREE.BoxBufferGeometry(15, 150, 120);
				affmurRDCGaucheP3 = new THREE.Mesh(murRDCGaucheP3, matBriBlGr);
				affmurRDCGaucheP3.position.set(-313, 50, -340);

				var tourCarréeRDCDroit = new THREE.BoxBufferGeometry(80, 180, 80);
				afftourCarréeRDCDroit = new THREE.Mesh(tourCarréeRDCDroit, matBriBlGr);
				afftourCarréeRDCDroit.position.set(350, 65, -220);
				afftourCarréeRDCDroit.rotation.y += 20;

				var tourRDCGaucheCylindreP2 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCGaucheCylindreP2 = new THREE.Mesh(tourRDCGaucheCylindreP2, matBriBlGr);
				affTourRDCGaucheCylindreP2.position.set(-313, 65, -400);

				var piedTourRDCGaucheCylindreP2 = new THREE.ConeGeometry(35, 80, 35);
				affPiedTourRDCGaucheCylindreP2 = new THREE.Mesh(piedTourRDCGaucheCylindreP2, matBriBlGr);
				affPiedTourRDCGaucheCylindreP2.position.set(-313, 15, -400);

				var toitTourRDCGaucheCylindriqueP2 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCGaucheCylindriqueP2 = new THREE.Mesh(toitTourRDCGaucheCylindriqueP2, matBriquesBleues);
				affToitTourRDCGaucheCylindriqueP2.position.set(-313, 185, -400);

				var murRDCGaucheP4 = new THREE.BoxBufferGeometry(15, 150, 180);
				affmurRDCGaucheP4 = new THREE.Mesh(murRDCGaucheP4, matBriBlGr);
				affmurRDCGaucheP4.position.set(-313, 50, -450);

				var tourCarréeRDCGauche = new THREE.BoxBufferGeometry(80, 180, 80);
				afftourCarréeRDCGauche = new THREE.Mesh(tourCarréeRDCGauche, matBriBlGr);
				afftourCarréeRDCGauche.position.set(-320, 65, -570);



				scene.add(affmurRDCGaucheP1, affmurRDCGaucheP2, affTourRDCGaucheCylindreP1, affPiedTourRDCGaucheCylindreP1, affToitTourRDCGaucheCylindriqueP1, affmurRDCGaucheP3, affTourRDCGaucheCylindreP2, affPiedTourRDCGaucheCylindreP2, affToitTourRDCGaucheCylindriqueP2, affmurRDCGaucheP4, afftourCarréeRDCGauche);


/********************* Partie RDC Arriere *********************/


				var murRDCArriereP1 = new THREE.BoxBufferGeometry(15, 150, 150);
				affmurRDCArriereP1 = new THREE.Mesh(murRDCArriereP1, matBriBlGr);
				affmurRDCArriereP1.position.set(228, 50, -589);
				affmurRDCArriereP1.rotation.y -= 5;

				var murRDCArriereP2 = new THREE.BoxBufferGeometry(60, 150, 15);
				affmurRDCArriereP2 = new THREE.Mesh(murRDCArriereP2, matBriBlGr);
				affmurRDCArriereP2.position.set(68, 50, -605);

				var tourRDCArriereCylindreP1 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCArriereCylindreP1 = new THREE.Mesh(tourRDCArriereCylindreP1, matBriBlGr);
				affTourRDCArriereCylindreP1.position.set(128, 65, -610);

				var piedTourRDCArriereCylindreP1 = new THREE.ConeGeometry(35, 80, 35);
				affPiedTourRDCArriereCylindreP1 = new THREE.Mesh(piedTourRDCArriereCylindreP1, matBriBlGr);
				affPiedTourRDCArriereCylindreP1.position.set(128, 15, -610);

				var toitTourRDCArriereCylindriqueP1 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCArriereCylindriqueP1 = new THREE.Mesh(toitTourRDCArriereCylindriqueP1, matBriquesBleues);
				affToitTourRDCArriereCylindriqueP1.position.set(128, 185, -610);

				var tourCarréeRDCArriere = new THREE.BoxBufferGeometry(80, 180, 80);
				afftourCarréeRDCArriere = new THREE.Mesh(tourCarréeRDCArriere, matBriBlGr);
				afftourCarréeRDCArriere.position.set(0, 65, -630);

				var murRDCArriereP3 = new THREE.BoxBufferGeometry(60, 150, 15);
				affmurRDCArriereP3 = new THREE.Mesh(murRDCArriereP3, matBriBlGr);
				affmurRDCArriereP3.position.set(-68, 50, -605);

				var tourRDCArriereCylindreP2 = new THREE.CylinderGeometry( 30, 30 , 180, 32);
				affTourRDCArriereCylindreP2 = new THREE.Mesh(tourRDCArriereCylindreP2, matBriBlGr);
				affTourRDCArriereCylindreP2.position.set(-128, 65, -610);

				var piedTourRDCArriereCylindreP2 = new THREE.ConeGeometry(35, 80, 35);
				affPiedTourRDCArriereCylindreP2 = new THREE.Mesh(piedTourRDCArriereCylindreP2, matBriBlGr);
				affPiedTourRDCArriereCylindreP2.position.set(-128, 15, -610);

				var toitTourRDCArriereCylindriqueP2 = new THREE.ConeGeometry( 40, 70, 40 );
				affToitTourRDCArriereCylindriqueP2 = new THREE.Mesh(toitTourRDCArriereCylindriqueP2, matBriquesBleues);
				affToitTourRDCArriereCylindriqueP2.position.set(-128, 185, -610);

				var murRDCArriereP4 = new THREE.BoxBufferGeometry(15, 150, 150);
				affmurRDCArriereP4 = new THREE.Mesh(murRDCArriereP4, matBriBlGr);
				affmurRDCArriereP4.position.set(-228, 50, -589);
				affmurRDCArriereP4.rotation.y += 5;



				scene.add(affmurRDCArriereP1, afftourCarréeRDCArriere, affTourRDCArriereCylindreP1, affPiedTourRDCArriereCylindreP1, affToitTourRDCArriereCylindriqueP1, affmurRDCArriereP2, affmurRDCArriereP3, affTourRDCArriereCylindreP2, affPiedTourRDCArriereCylindreP2, affToitTourRDCArriereCylindriqueP2, affmurRDCArriereP4);




/********************* Partie 1erEtage *********************/

				var partieAvant1erEtageBase = new THREE.BoxBufferGeometry(150, 250, 150);
				affPartieAvant1erEtageBase = new THREE.Mesh(partieAvant1erEtageBase, matBriquesRoses);
				affPartieAvant1erEtageBase.position.set(0, 100, -160);

				var partieAvant1erEtageHaut = new THREE.BoxBufferGeometry(190, 60, 130);
				affpartieAvant1erEtageHaut = new THREE.Mesh(partieAvant1erEtageHaut, matBriquesRoses);
				affpartieAvant1erEtageHaut.position.set(0, 216, -130);

				var partieAvant1erEtageHautDroit = new THREE.BoxBufferGeometry(30, 60, 150);
				affpartieAvant1erEtageHautDroit = new THREE.Mesh(partieAvant1erEtageHautDroit, matBriquesRoses);
				affpartieAvant1erEtageHautDroit.position.set(80, 216, -150);

				var partieAvant1erEtageHautGauche = new THREE.BoxBufferGeometry(30, 60, 150);
				affpartieAvant1erEtageHautGauche = new THREE.Mesh(partieAvant1erEtageHautGauche, matBriquesRoses);
				affpartieAvant1erEtageHautGauche.position.set(-80, 216, -150);

	            var pyramidgeometry = new THREE.CylinderGeometry(20, 135, 160, 4, false);
	            pyramid = new THREE.Mesh(pyramidgeometry, matBl2);
	            pyramid.position.set(0, 327, -160);
	            pyramid.rotation.y += 2.35;

	            var fenetre1 = new THREE.CylinderGeometry(30, 30, 30, 60);
	            afffenetre1 = new THREE.Mesh(fenetre1, matfenetre);
	            afffenetre1.position.set(0, 240, -75);
	            afffenetre1.rotation.x += 1.6;

				var tourAvant1erEtageDroit = new THREE.CylinderGeometry( 15, 15, 60, 32);
				affTourAvant1erEtageDroit = new THREE.Mesh(tourAvant1erEtageDroit, matBriquesRoses);
				affTourAvant1erEtageDroit.position.set(-95, 230, -55);

				var toitTourAvant1erEtageDroit = new THREE.ConeGeometry( 18, 30, 18);
				affToitTourAvant1erEtageDroit = new THREE.Mesh(toitTourAvant1erEtageDroit, matBriquesBleues);
				affToitTourAvant1erEtageDroit.position.set(-95, 275, -55);

				var tourAvant1erEtageGauche = new THREE.CylinderGeometry( 15, 15, 60, 32);
				affTourAvant1erEtageGauche = new THREE.Mesh(tourAvant1erEtageGauche, matBriquesRoses);
				affTourAvant1erEtageGauche.position.set(95, 230, -55);

				var toitTourAvant1erEtageGauche = new THREE.ConeGeometry( 18, 30, 18);
				affToitTourAvant1erEtageGauche = new THREE.Mesh(toitTourAvant1erEtageGauche, matBriquesBleues);
				affToitTourAvant1erEtageGauche.position.set(95, 275, -55);

				var partieBase1erEtage = new THREE.BoxBufferGeometry(500, 180, 200);
				affPartieBase1erEtage = new THREE.Mesh(partieBase1erEtage, matBriquesRoses);
				affPartieBase1erEtage.position.set(0, 65, -250);

	            var pyramidgeometry2 = new THREE.CylinderGeometry(80, 150, 70, 4, false);
	            pyramid2 = new THREE.Mesh(pyramidgeometry2, matBriquesBleues);
	            pyramid2.position.set(150, 190, -250);
	            pyramid2.rotation.y += 2.35;

				var tourPyramidGeometry2 = new THREE.CylinderGeometry( 12, 12, 140, 32);
				affTourPyramidGeometry2 = new THREE.Mesh(tourPyramidGeometry2, matBriquesRoses);
				affTourPyramidGeometry2.position.set(160, 250, -230);

				var toitTourPyramidGeometry2 = new THREE.ConeGeometry( 15, 100, 15);
				affToitTourPyramidGeometry2 = new THREE.Mesh(toitTourPyramidGeometry2, matOr);
				affToitTourPyramidGeometry2.position.set(160, 360, -230);

				var partieBase1erEtagePart2 = new THREE.BoxBufferGeometry(200, 50, 200);
				affPartieBase1erEtagePart2 = new THREE.Mesh(partieBase1erEtagePart2, matRoseFene);
				affPartieBase1erEtagePart2.position.set(-150, 180, -250);

	            var pyramidgeometry3 = new THREE.CylinderGeometry(80, 150, 70, 4, false);
	            pyramid3 = new THREE.Mesh(pyramidgeometry3, matBriquesBleues);
	            pyramid3.position.set(-150, 240, -250);
	            pyramid3.rotation.y += 2.35;

				var partieBase1erEtageArriere = new THREE.BoxBufferGeometry(400, 160, 150);
				affPartieBase1erEtageArriere = new THREE.Mesh(partieBase1erEtageArriere, matRoseFene2);
				affPartieBase1erEtageArriere.position.set(0, 55, -425);

	            var pyramidgeometry4 = new THREE.CylinderGeometry(50, 110, 60, 4, false);
	            pyramid4 = new THREE.Mesh(pyramidgeometry4, matBriquesBleues);
	            pyramid4.position.set(130, 165, -425);
	            pyramid4.rotation.y += 2.35;

	            var pyramidgeometry5 = new THREE.CylinderGeometry(50, 110, 60, 4, false);
	            pyramid5 = new THREE.Mesh(pyramidgeometry5, matBriquesBleues);
	            pyramid5.position.set(-130, 165, -425);
	            pyramid5.rotation.y += 2.35;

				var partieBase1erEtageArriereV2 = new THREE.BoxBufferGeometry(150, 160, 60 );
				affPartieBase1erEtageArriereV2 = new THREE.Mesh(partieBase1erEtageArriereV2, matRoseFene2);
				affPartieBase1erEtageArriereV2.position.set(0, 55, -520);

	            var pyramidgeometry6 = new THREE.CylinderGeometry(50, 110, 60, 4, false);
	            pyramid6 = new THREE.Mesh(pyramidgeometry6, matBriquesBleues);
	            pyramid6.position.set(0 , 165, -475);
	            pyramid6.rotation.y += 2.35;

				var tourGaucheGrosse = new THREE.BoxBufferGeometry(70, 450, 70);
				affTourGaucheGrosse = new THREE.Mesh(tourGaucheGrosse, matBriquesRoses);
				affTourGaucheGrosse.position.set(-240, 200, -160);

				var tourGaucheGrossePart2 = new THREE.BoxBufferGeometry(80, 60, 80);
				affTourGaucheGrossePart2 = new THREE.Mesh(tourGaucheGrossePart2, matBriquesRoses);
				affTourGaucheGrossePart2.position.set(-240, 400, -160);

	            var pyramidgeometryTour = new THREE.CylinderGeometry(0, 60, 80, 4, false);
	            pyramidTour = new THREE.Mesh(pyramidgeometryTour, matBriquesBleues);
	            pyramidTour.position.set(-240 , 470, -160);
	            pyramidTour.rotation.y += 2.35;



				scene.add(affPartieAvant1erEtageBase, affpartieAvant1erEtageHaut, affpartieAvant1erEtageHautDroit, affpartieAvant1erEtageHautGauche, pyramid, affTourAvant1erEtageDroit, affToitTourAvant1erEtageDroit, affTourAvant1erEtageGauche, affToitTourAvant1erEtageGauche, affPartieBase1erEtage, pyramid2, affTourPyramidGeometry2, affToitTourPyramidGeometry2, affPartieBase1erEtagePart2, pyramid3, affPartieBase1erEtageArriere, affPartieBase1erEtageArriereV2, pyramid4, pyramid5, pyramid6, affTourGaucheGrosse, affTourGaucheGrossePart2, pyramidTour, afffenetre1);



/********************* Partie 2emeEtage *********************/


				var partieBase2emeEtage = new THREE.BoxBufferGeometry(200, 140, 200);
				affPartieBase2emeEtage = new THREE.Mesh(partieBase2emeEtage, matBriquesRoses);
				affPartieBase2emeEtage.position.set(0, 200, -300);

	            var pyramid2emeEtage = new THREE.CylinderGeometry(110, 150, 70, 4, false);
	            affpyramid2emeEtage = new THREE.Mesh(pyramid2emeEtage, matBriquesBleues);
	            affpyramid2emeEtage.position.set(0 , 300, -300);
	            affpyramid2emeEtage.rotation.y += 2.35;

				scene.add(affPartieBase2emeEtage, affpyramid2emeEtage);



/********************* Partie 2emeEtage *********************/


				var tour2emeEtage = new THREE.CylinderGeometry( 35, 35, 240, 32);
				affTour2emeEtage = new THREE.Mesh(tour2emeEtage, matBriquesRoses);
				affTour2emeEtage.position.set(40, 430, -280);

				var tour2emeEtagePart1 = new THREE.CylinderGeometry( 45, 45, 25, 32);
				affTour2emeEtagePart1 = new THREE.Mesh(tour2emeEtagePart1, matBriquesRoses);
				affTour2emeEtagePart1.position.set(40, 510, -280);

				var tour2emeEtagePart1V2 = new THREE.CylinderGeometry( 45, 0, 50, 32);
				affTour2emeEtagePart1V2 = new THREE.Mesh(tour2emeEtagePart1V2, matBriquesRoses);
				affTour2emeEtagePart1V2.position.set(40, 473, -280);

				var tour2emeEtagePart2 = new THREE.CylinderGeometry( 45, 45, 25, 32);
				affTour2emeEtagePart2 = new THREE.Mesh(tour2emeEtagePart2, matBriquesRoses);
				affTour2emeEtagePart2.position.set(40, 450, -280);

				var tour2emeEtagePart2V2 = new THREE.CylinderGeometry( 45, 0, 50, 32);
				affTour2emeEtagePart2V2 = new THREE.Mesh(tour2emeEtagePart2V2, matBriquesRoses);
				affTour2emeEtagePart2V2.position.set(40, 413, -280);

				var toitTour2emeEtage = new THREE.ConeGeometry( 45, 100, 45);
				affToitTour2emeEtage = new THREE.Mesh(toitTour2emeEtage, matBriquesBleues);
				affToitTour2emeEtage.position.set(40, 600, -280);


				var tour2emeEtage2 = new THREE.CylinderGeometry( 25, 25, 350, 32);
				affTour2emeEtage2 = new THREE.Mesh(tour2emeEtage2, matBriquesRoses);
				affTour2emeEtage2.position.set(-120, 300, -350);

				var tour2emeEtage2V2 = new THREE.CylinderGeometry( 35, 35, 30, 32);
				affTour2emeEtage2V2 = new THREE.Mesh(tour2emeEtage2V2, matBriquesRoses);
				affTour2emeEtage2V2.position.set(-120, 430, -350);

				var tour2emeEtage2VPart2 = new THREE.CylinderGeometry( 35, 0, 50, 32);
				affTour2emeEtage2VPart2 = new THREE.Mesh(tour2emeEtage2VPart2, matBriquesRoses);
				affTour2emeEtage2VPart2.position.set(-120, 390, -350);

				var toitTour2emeEtage2 = new THREE.ConeGeometry( 5, 50, 5);
				affToitTour2emeEtage2 = new THREE.Mesh(toitTour2emeEtage, matBriquesBleues);
				affToitTour2emeEtage2.position.set(-120, 510, -350);

	            var fenetre2 = new THREE.CylinderGeometry(20, 20, 30, 60);
	            afffenetre2 = new THREE.Mesh(fenetre2, matfenetre);
	            afffenetre2.position.set(40, 560, -245);
	            afffenetre2.rotation.x += 1.6;



				scene.add(affTour2emeEtage, affTour2emeEtagePart1, affTour2emeEtagePart1V2, affTour2emeEtagePart2, affTour2emeEtagePart2V2, affToitTour2emeEtage, affTour2emeEtage2, affTour2emeEtage2V2, affTour2emeEtage2VPart2, affToitTour2emeEtage2, afffenetre2);







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
