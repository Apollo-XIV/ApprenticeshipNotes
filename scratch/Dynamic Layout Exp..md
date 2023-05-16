The idea for this is a page system that centers around a central div that resizes and changes dynamically with the content its displaying. This dynamic box would be able to accommodate a range of templates and custom content too.
![[Pasted image 20230516113418.png]]
This box would be able to fluidly transition between displaying various types of media, from blog posts to video, to document, and more. They key to doing this in a way that satisfies next.js' routing system is using a breakChildren function to seperate out the layout and identify what should go in the box.
![[Pasted image 20230516113609.png]]
