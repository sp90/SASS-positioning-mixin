<h1>Shorthand positioning mixin</h1>
<p>Uses the same syntax as a margin/padding to set properties for <code>top | right | bottom | left</code> of an element</p>
<p>Generally you are setting at least two offsets when positioning along with its position type</p>

<h2>The mixin</h2>
<code>
	@mixin pos ($offsets, $shorthand: "a") {...}
</code>

<h2>Properties</h2>
<p>This contains shorthands for positions like "fixed" can be shorted to "f" here is a list of the shorthands</p>
* relative
	* rel
	* r
* absolute
	* a
	* ab
	* abs
* fixed
	* f
	* fix

<p>If you dont write a position type it will fallback to position: absolute;</p>
<p>make it ignore the properties see the examples below</p>

<h2>Examples</h2>
<pre>
	<code>
	.arrow { 
		@include pos(5px null null -10px); 
	}
	.arrow { 
		position: absolute; 
		top: 5px; 
		left: -10px; 
	}
	
	//anchor some text to the bottom on an element
	.caption { 
		@include pos(null 0 0, fix); 
	}
	.caption { 
		position: fixed; 
		right: 0; 
		bottom: 0; 
		left: 0; 
	}
	
	//full screen modal
	.modal { 
		@include pos (0, f); 
	}
	.modal { 
		position: absolute; 
		top: 0; 
		right: 0; 
		bottom: 0; 
		left: 0; 
	}
	
	//remove any previous offsets 
	.main-nav {
		@include pos(0 null null -100%, f);
		
		&.active { 
			left: 0; 
		}
	}
	
	@media (min-width: 40em) {
		//needs relative for absolute children, but remove any offset
		.main-nav { 
			@include pos (auto, r);
		}
	}
	</code>
</pre>
