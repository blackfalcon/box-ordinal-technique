#Zombie Raiders

## Content Choreography
This is a slimed down example of the great work done by [Jordan Moore](http://www.jordanm.co.uk/contentchoreography). The basic proof of concept is, how can we manage content placement depending on user experience?

##What does it do?
What was pretty awesome about Jordan's example was how the elements reordered depending on the user's device experience. Nice. Reading up on the techniques used in [W3Schools](http://www.w3schools.com/cssref/css3_pr_box-ordinal-group.asp) I recreated the example in a much simpler light. 

##Progressive enhancement meets adaptive design
The key feature that makes this work is a combination of ``flexbox`` and ``box-ordinal-group``. Where we get progressive, all browsers that support these featured also support ``@media`` queries. 

For basic layout I am using standard block elements and floats. To add this spice of awesome, using the ``@media`` query we are then removing the float, adding the flex and assigning layout order. 

**Example code**
```scss
// all browsers understand these base styles
section {
	max-width: 60em;
	margin: 0 auto;
}

article {
	background: aqua;
	float: left;
	width: 65%;
}

//browsers that support @media get this dash of awesome
@media screen and (max-width: 1024px) {
	
	// assign the flexbox attributes to the parent container
	section {
		display:-webkit-box;
		-webkit-box-orient:vertical;
	}
	
	// set the placement of the content box
	article {
		box-ordinal-group: 2;
		-moz-box-ordinal-group: 2;
		-webkit-box-ordinal-group: 2;
		
		// remove float and set width
		float: none;
		width: auto;
	}
}

```

##Key points to consider
Some of the key points in the technique are:
* All block elements that float only float above the @media breakpoint
* It is only below the @media breakpoint that all floats are set to ``none``, widths set to ``auto`` and the parent block is instructed to use flexbox.

Take a look at the code and hope this helps. And be sure to look for a sass version in the future :D