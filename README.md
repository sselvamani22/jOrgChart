#Readme


##Overview of the original Plugin

Follow me [@sselvamani22](http://twitter.com/sselvamani22)

jQuery OrgChart is a plugin that allows you to render structures with nested elements in a easy-to-read tree structure. To build the tree all you need is to make a single line call to the plugin and supply the HTML element Id for a nested unordered list element that is representative of the data you'd like to display. If drag-and-drop is enabled you'll be able to reorder the tree which will also change the underlying list structure. 
This orgChart will support on json. I used taffydb for querying the json data.


Features include:

* Very easy to use given a nested unordered list element.
* Drag-and-drop functionality allows reordering of the tree and underlying `<ul>` structure.
* Showing/hiding a particular branch of the tree by clicking on the respective node.
* Nodes can contain any amount of HTML except `<li>` and `<ul>`.
* Easy to style.
* Now you can add nodes!
* You can edit existing nodes labels.
* Now you can delete nodes.


----
##Differences

* You can specify that sub-trees should start collapsed, which is useful for very large trees.
* You can add more extra node from top right side box.
* When you delete node from orgchart it will add to extra node place.
* When you hover the node it will show some additional data.
* Different color will display on different rows.


----

##Expected Markup & Example Usage

To get up and running you'll need a few things. 

-----

###The JavaScript Libraries & CSS

You need to include the jQuery as well as the jOrgChart libraries. For example:

	<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.4/jquery.min.js"></script>
	<script type="text/javascript" src="js/jquery.jOrgChart.js"></script>

Download and add FancyBox2 http://fancyapps.com/fancybox/

If you want to use the drag-and-drop functionality you'll need to include jQuery UI too:

	<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8.9/jquery-ui.min.js"></script>
	
The core CSS is necessary to perform some of the basic styling i.e.

    <link rel="stylesheet" href="css/jquery.jOrgChart.css"/>

	
For handle the json code you need to add taffydb

    <script type="text/javascript" src="js/taffy.js"></script>

----

###The HTML

You'll need to construct a nest unordered list that represents your node nesting. For example:

	<ul id="org" style="display:none">

	</ul>

If you want to add more node then you need to include this code in body
	
	
	<ul id="upload-chart">
		<li id="Albert" class="node child"><span class="label_node"><a href="#">Albert</a><br><i>Data Architect</i> </span><div class="details"><p><strong>rank:</strong>Vice President</p><p><strong>department:</strong>Research and Development</p></div></li>
		<li id="Moser" class="node child"><span class="label_node"><a href="#">Moser</a><br><i>technical engineer </i></span><div class="details"><p><strong>rank:</strong>Manager</p><p><strong>department:</strong>IT</p></div></li>
		<li id="Meinert" class="node child"><span class="label_node"><a href="#">Meinert</a><br><i>Maintenance Service Engineer</i></span><div class="details"><p><strong>rank:</strong>Vice President</p><p><strong>department:</strong>Research and Development</p></div></li>
		<li id="Mic" class="node child"><span class="label_node"><a href="#">Mic</a><br><i>Chairman of the Board, President</i></span><div class="details"><p><strong>rank:</strong>Manager</p><p><strong>department:</strong>IT</p></div></li>
	</ul>
	
if you dont want to display drag extra node then you can handle this using either css or jquery
	
This plugin works by generating the tree as a series of nested tables. Each node in the tree is represented with `<div class="node">`. You can include any amount of HTML markup in your `<li>` **except** for other `<ul>` or `<li>` elements. Your markup will be used within the node's `<div>` element. Any classes you attach to the `<li>` elements will be copied to the associated node, allowing you to highlight particular parts of the tree. The special `collapsed` class described above doesn't get copied to the node.


-----

###The jQuery Call
Add this function somewhere in your document:
	
	function init_tree(){
      var opts = {
        chartElement : '#chart', //your tree container
        dragAndDrop  : true
      };
      $("#chart").html(""); //clean your container
      $("#org").jOrgChart(opts); //creates the jOrgChart
    }

And the cherry on the top is the usual call on document load of the function you just make. For example:

	jQuery(document).ready(function() {
	    init_tree();
	});
	
In order to preserve adding, editing and deleting nodes capabilities, please leave the jquery events listeners for *.edit*, *.del*, *.add*, *#edit_node*, *#add_node*.
Of course, you can alter these methods to fit your requirements.
	
This call will append the markup for the OrgChart to the `<body>` element by default, but you can specify this as part of the options.


------

##Demo Page

Demo of the code is available here [here](http://sselvamani22.github.io/jOrgChart "DEMO").

-----

##Configuration

Here the below configurations.

1. **chartElement** - used to specify which HTML element you'd like to append the OrgChart markup to. *[default='body']*
2. **depth** - tells the code what depth to parse to. The default value of "-1" instructs it to parse like it's 1999. *[default=-1]*
3. **chartClass** - the name of the style class that is assigned to the generated markup. *[default='jOrgChart']*
4. **dragAndDrop** - determines whether the drag-and-drop feature of tree node elements is enabled. *[default=false]*
5. **expand** - To view the expand and collapse button on parent nodes. *[default=false]*
6. **control** - Enable options to ADD, EDIT and DELETE the nodes. *[default=false]*
7. **rowcolor** - Display the nodes on different color based upon rows. *[default=true]*

