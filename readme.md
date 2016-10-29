
#Semantic-UI Color Generator
Generating your new color class for semantic-ui components **_effort-less!_**

> ###_The best color in the whole world is the one that looks good on you!_
~*coco chanel*

+ If you are a frontend engineer and believe that color play a crucial part of your visual artwork, **this will fit on you!**,
+ If you use semantic-ui a lot, **try this!** and look how colorful person you'll be come.
+ If you aware that semantic-ui is great but lack of colors that fits to your need, you knew how to customize it but you're to lazy to do it. or maybe you've tried and finally back off confused with every chaining [@variable](http://lesscss.org/features/#variables-feature) been made, congrats! **Yes, Obviously this meant for you!**

>You can call it a [**Mixin**](http://lesscss.org/features/#mixins-parametric-feature), but i prefer to call it a **Generator**, because you only need to define one line of code, so that you can achieved hundreds and more lines of code to get semantic-ui components **_colored and generated automatically_**, **i guarantee this will save you precious time.**

-------------
### How to start a project with this
##### Basic requirement
1. Basic understanding of [less](http://lesscss.org/#) css 
2. Know how to compile less to css.
   + you can use [SublimeText](https://www.sublimetext.com/) extension, [Brackets](http://brackets.io/), or any code editor that support less to compile it
   + using [Grunt](http://gruntjs.com/plugins) or [Gulp](http://gulpjs.com/plugins/) taks runner even better
   + using precompiler like [Prepros](https://prepros.io/), [Koala](http://koala-app.com/), etc. is **_Recommended_** *since it only an light task.
3. Basic knowledge of [semantic-ui](http://semantic-ui.com)

##### Starting Up
1. [Clone][cloneRepo] or [download][downloadZip] the source code
2. Define color and which component you want to be colored.
3. Compile it, and include [semantic.color.css][colorcss] to your _index.html_.

------------

Have you tried the [demo][demosite] page? take a look at the **_custom color_** on the left menu section, there is six new color i created. I call it in _class_ as: **_flatgold, concrete, darkgreen, autumnbrown, darkblue, and litecream._** here is the generated [code][colorcss].

Those custom colors now **_AutoMagically_** available for **_12 components._**

> **Here is the List of Components:** 
**[grid](http://semantic-ui.com/collections/grid.html#colored)**, **[table](http://semantic-ui.com/collections/table.html#colored)**, **[segment](http://semantic-ui.com/elements/segment.html#colored)**, **[card](http://semantic-ui.com/views/card.html#colored)**, **[message](http://semantic-ui.com/collections/message.html#colored)**, **[progress](http://semantic-ui.com/modules/progress.html#color)**, **[menu](http://semantic-ui.com/collections/menu.html#colored)**, **[icon](http://semantic-ui.com/elements/icon.html#colored)**, **[header](http://semantic-ui.com/elements/header.html#colored)**, **[label](http://semantic-ui.com/elements/label.html#colored)**, **[button](http://semantic-ui.com/elements/button.html#colored)**, **[dimmer](http://semantic-ui.com/modules/dimmer.html)**. 


```html
		<div class="ui grid">
			<div class="flatgold row">
				<div class="concrete column">
					<!-- Your Great Content -->
				</div>
			</div>
		</div>
		<!-- or -->
		<button class="ui darkgreen button">
			<i class="flatgold user icon"> User </i>
		</button>
```
>Except for **dimmer** you need to **_define your color_** at **_variation_** [settings](http://semantic-ui.com/modules/dimmer.html#/settings) in the javascript code, because the **dimmer.js** code only manipulate the `<div class="ui dimmer"></div>`, so it wont take any effect if you define it in HTML eq: `<div class="ui red dimmer"></div>`, maybe there will be a consideration for future enhancement after this. 

```js
		// So if you want red dimmer define it like this
		$('#containerWhereDimmerLives')
	        .dimmer({
	          on: 'hover',
	          variation: 'red'
	        });
```

See the [official documentation](http://semantic-ui.com/) for **_detail example_** calling up the other components.


Done for the intro, now get straight to the **Interesting part**
![generator demo][demo]

>That custom color were created only by writing _(.less)_ code below 

```less
	.GENERATE-UI-COLOR(flatgold, @flatgold);
	.GENERATE-UI-COLOR(concrete, @concrete);
	.GENERATE-UI-COLOR(darkgreen, @darkGreen);
	.GENERATE-UI-COLOR(autumnbrown, @autumnBrown);
	.GENERATE-UI-COLOR(darkblue, @darkblue);
	.GENERATE-UI-COLOR(litecream, @liteCream);
```
>Of course i considering the need of generating color only for specific components, here to do that:

```less
	/* generate colored button */
	.GENERATE-COLORED-BUTTON(colorClass, @colorVariable);

	/* generate colored card */
	.GENERATE-COLORED-CARD(colorClass, @colorVariable);

	/* generate colored grid */
	.GENERATE-COLORED-GRID(colorClass, @colorVariable);

	/* generate colored segment */
	.GENERATE-COLORED-SEGMENT(colorClass, @colorVariable);

	/* generate colored header */
	.GENERATE-COLORED-HEADER(colorClass, @colorVariable);

	/* generate colored message */
	.GENERATE-COLORED-MESSAGE(colorClass, @colorVariable);

	/* generate colored icon */
	.GENERATE-COLORED-ICON(colorClass, @colorVariable);

	/* generate colored label */
	.GENERATE-COLORED-LABEL(colorClass, @colorVariable);

	/* generate colored dimmer */
	.GENERATE-COLORED-DIMMER(colorClass, @colorVariable);

	/* generate colored table */
	.GENERATE-COLORED-TABLE(colorClass, @colorVariable);

	/* generate colored menu */
	.GENERATE-COLORED-MENU(colorClass, @colorVariable);
```

**What happen there?** that's pretty interesting question but i'm afraid i cannot clearly explain it to you.
basically i just **_extract_** the original css **_selector_** for every components into a single component generator, i also took and redifining existing **_global variables_** into **_local variables_** specific for every components, so you can call it like that. global variable will still work here if you want it, just _import_ them!

**Is it Customizable?** _No!! i'm kidding.._ Of course **it is!** find it at [/generators][generatorFolder] folder. 
let say you open the [ui-colored-menu.generator.less][menuGenerator], take a look the code. every **variable** will be start with [@](http://lesscss.org/features/#variables-feature), customize it meet to your need! if you use this **original folder structure** this generator will **compile** your code to **[semantic.color.css][colorcss]**, and **use** **[semantic.color.less][colorless]** to define what color and component you want to generate. 
if you **_look closer_** i also make a **variable for classes**, then i call it back using **interpolation syntax**. not only for coloring, **_with this recipe i think it will open possibilities for translating classes or other tweaks._**

--------
##### Known Bugs
+ Grid
  > you should define how many column you want to use for your layout in **grid** or **row**, otherwise the layout will break

  ```html
	<!-- This Example Working fine -->
	<div class="ui three column grid">
		<div class="column"></div>
		<div class="column"></div>
		<div class="column"></div>
	</div>

	<!-- or -->

	<div class="ui grid">
		<div class="two column row">
			<div class="column"></div>
			<div class="column"></div>
		</div>
	</div>


	<!-- This Example will break the layout-->
	<div class="ui grid">
		<div class="column"></div>
		<div class="column"></div>
		<div class="column"></div>
	</div>

	<!-- or -->

	<div class="ui grid">
		<div class="row">
			<div class="column"></div>
			<div class="column"></div>
			<div class="column"></div>
		</div>
	</div>

  ```
  > i'll fix this later, as soon as i have time. or you want to help? just let me know

[colorcss]: colorcss
[colorless]: colorless
[menuGenerator]: menu
[demo]: ./showcase/assets/images/generator_color.gif
[generatorFolder]: generatorFolder/generators
[demoSite]: demosite
[downloadZip]: downloadUrl
[cloneRepo]: repoUrl