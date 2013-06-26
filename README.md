jquery-armyKnife
================

ArmyKnife is a super easy, super flexable jquery rotation plugin.  It can be attached to photo albums, sliders, galleries, tabs, forms and much more.

Versions
--------
1.7 - 2013-06-25

Installation
------------

	<script src="http://code.jquery.com/jquery-1.10.1.min.js"></script>
	<script src="jquery.armyKnife.min.js"></script>

Image Rotations
---------------

	<!-- html -->
	<p id="rotation">
		<img src="img1.jpg" />
		<img src="img2.jpg" />
		<img src="img3.jpg" />
		<img src="img4.jpg" />
	</p>

	<!-- basic css -->
	<style>
		#rotation {
			position	: relative;
			width		: 400px;
			height		: 200px;
			overflow	: hidden;
		}
		#rotation img {
			position	: absolute;
			top			: 0px;
			left		: 0px;
		}
	</style>

	<!-- javascript -->
	<script>
		$(function(){

			//basic example
			$("#rotation").armyKnife({
				generateNav	:	true,
				transition	:	"slide",
				navID		:	"rotation_nav",
				autoRotate	:	true
			});

			//custom nav
			$("#rotation").armyKnife({
				sections	:	"img",
				generateNav	:	true,
				transition	:	"slide",
				navID		:	"rotation_nav",
				autoRotate	:	true
			});

			//numeric nav
			$("#rotation").armyKnife({
				speed		:	1000,
				transition	:	"fade",
				generateNav	:	true,
				navType		:	"numeric",
				navID		:	"rotation_nav",
				autoRotate	:	true
			});

			//marquee effect
			$("#rotation").armyKnife({
				transition	:	"slide",
				autoRotate	:	true,
				speed		:	5000,
				easing		:	"linear",
				autoRotateDelay	:	0
			});
		});
	</script>

Form Slides
-----------

	<!-- html -->
	<form id="form_slide">
		<div>
			<h4>Step 1</h4>
			<p>Do some awesome stuff here.</p>
			<input type="text" placeholder="Name" value="" /><br />
		</div>
		<div>
			<h4>Step 2</h4>
			<p>Continue rockin' it for one more page.</p>
			<textarea placeholder="Questions? Comments?"></textarea><br />
		</div>
		<div>
			<h4>Step 3</h4>
			<p>That should do it!</p>
			<input type="submit" value="Submit" /><br />
		</div>
	</form>

	<!-- basic css -->
	<style>
		#form_slide {
			position	: relative;
			width		: 400px;
			height		: auto;
			overflow	: hidden;
		}
		#form_slide > div {
			position	: absolute;
			top			: 0px;
			left		: 0px;
			padding		: 20px;
			width		: 360px;
		}
	</style>

	<!-- javascript -->
	<script>
		$(function(){
			$("#form_slide").armyKnife({
				sections		:	"> div",
				transition		:	"slide",
				autoResize		:	true,
				showSectionButtons	:	true,
				sectionButtonClass	: 	"btn large"
			});
		});
	</script>

Tabs
----

	<!-- html -->
	<ul id="tabs_fade_nav"></ul>
	<div id="tabs_fade">
		<div title="List">
			<ul>
				...
			</ul>
		</div>
		<div title="Text">
			<p>...</p>
		</div>
		<div title="Both">
			<ul>
				...
			</ul>
			<p>...</p>
		</div>
	</div>

	<!-- css -->
	#tabs_fade {
		position	: relative;
		margin		: 0px auto;
		width		: 400px;
		height		: auto;
		overflow	: hidden;
	}
	#tabs_fade > div {
		position	: absolute;
		top			: 0px;
		left		: 0px;
		padding		: 20px;
		width		: 360px;
	}

	<!-- javascript -->
	<script>
		$(function(){
			$("#tabs_fade").armyKnife({
				sections	:	"> div",
				transition	:	"fade",
				autoResize	:	true,
				generateNav	:	true,
				navType		:	"text",
				navItemSource	:	function(section) {
					return section.attr("title");
				},
				navID		:	"tabs_fade_nav"
			});
		});
	</script>

Options
-------

	$("#myElem").armyKnife({
		speed			:	300,
		sections		:	"> *",
		startingSection		:	0,
		easing			:	"swing",		// [swing|linear]
		transition		:	"none",			// [none|slide|slideIn|slideOut|
										// fade|fadeIn|fadeOut]
		autoResize		: 	false,
		resizeSpeed		: 	200,
		autoRotate		:	false,
		autoRotateDelay		:	5000,
		generateNav		:	false,
		navType			:	"empty",		// [empty|numeric|text|custom]
		navItemSource		:	function(section) {	// REQUIRED WHEN navType = 'text' OR 'custom';
										// RESPECTIVE SECTION IS PASSED FOR EASY REFERENCE
			return "&nbsp;";
		},
		navItemCode		:	function(source) {	// REQUIRED WHEN navType = 'custom'; SECTION SOURCE
										// IS PASSED FOR EASY REFERENCE
			var btn	=	$("<a />",{
				"href"	: 	"#"
			});
			btn.html(source);
			return btn;
		},
		navID			:	false,
		navClass		:	"armyKnife-Nav",
		navTrigger		:	"click",
		itemsPerNav		:	0,			//	0 = UNLIMITED ITEMS PER NAV; RESULTS IN ONLY 1 NAV
		activeNavItemClass	:	"active",
		showSectionButtons	: 	false,
		sectionButtonClass	: 	"armyKnife-Btn",
		sectionButtonCodeNext	: 	$("<a />",{
			"href"	: 	"#"
		}),
		sectionButtonCodePrev	: 	$("<a />",{
			"href"	: 	"#"
		}),
		sectionOnEnter		:	function(o) {		//	o.current = CURRENT SECTION'S INDEX;
										// o.previous = PREVIOUS SECTION'S INDEX;
										// o.sections = ARRAY OF ALL SECTIONS
			var currentSection	=	$(this);
		},
		sectionOnExit		:	function(o) {		//	o.current = CURRENT SECTION'S INDEX;
										// o.target = TARGET SECTION'S INDEX;
										// o.sections = ARRAY OF ALL SECTIONS
			var currentSection	=	$(this);
		},
		sectionBeforeEnter	:	function(o) {
			var currentSection	=	$(this);
		},
		sectionBeforeExit	:	function(o) {
			var currentSection	=	$(this);
		},
		useContinue			:	false
	},callback);

Events
------

	$("#myElem").armyKnife("next");
	$("#myElem").armyKnife("prev");
	$("#myElem").armyKnife("goto",5);	// USE SECTION INDEX, NOT SECTION COUNT