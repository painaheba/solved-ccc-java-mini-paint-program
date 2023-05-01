Download Link: https://assignmentchef.com/product/solved-ccc-java-mini-paint-program
<br>
Java Mini Paint Program:

MiniPaint provides a set of “tools” for drawing different kinds of shapes, (lines, rectangles, ovals, text, and images). The user can use the mouse to draw using the current tool and can click on buttons to change the brush-shape. There are also buttons to clear the screen, and to set various options, such as toggling between outline shapes and filled shapes, setting the line and fill colours, setting the line width and setting the text size.

Core




Implement MiniPaint so that it will




Have the appropriate fields.

Set up the user interface correctly

Select the  Line, Rect, Oval, or Caption tool correctly (and remember the text for the caption).

(The doSetLine etc, methods)

Draw a line between the mouse pressed and mouse released points if the current shape is Line.

(The doMouse and drawALine methods).

Draw a rectangle or oval between the mouse pressed and mouse released points if the current shape is Rect or Oval. The shape should be an outline or filled, depending on the Fill/NoFill button.

(The doMouse, drawARectangle and  drawAnOval methods).

For the core, drawARectangle and drawAnOval only need to draw the shapes correctly when the user drags from the top-left corner to the bottom-right corner.

Draw a text caption where the mouse is released if the current tool is Caption.

(The doMouse and drawCaption methods)

Make the Fill/NoFill button work, so that drawing rectangles and ovals will be filled or outline, depending on the Fill/NoFill button.

Make the Line Width and Text Size sliders set the line width and text size.

Hint: The most common difficulty that students have is working out exactly when and where everything should happen. Make sure that you watch the demo video and notice what happens when buttons are clicked and what happens when the mouse is pressed, released, or dragged on the graphics pane. Notice especially that when you click on the buttons (except the Clear button), the program does not draw anything – all it does is to remember which button was chosen. It is only when you release the mouse somewhere that it actually draws a shape (or image). What shape it draws depends on what tool it is currently set to.




Completion




Add the following features to your program:




Make the mouse draw ovals or rectangles correctly when the user drags from any corner to the diagonally opposite corner.

(Hint: given the two points, work out the values of left, top, width, and height.)

Make the Line Color and Fill Color buttons work, and make lines, ovals, rectangles and captions use the two colours correctly.

Make the Image button ask for a filename and set the tool correctly, and then have the mouse draw the image within the rectangle specified by the pressed and released mouse positions (just like the rectangles) (or at its natural size if the two positions are within 5 pixels of each other).

Make the Eraser and the Freehand buttons work.

For these tools, you need a mouseMotionListener, and the mouse must respond to “dragged” events by either erasing a circular region around the mouse or extending the freehand line to the mouse position.

Challenge




There are lots of ways in which this program could be made nicer to use. For example you could add some of the following (or something else interesting):




Make the drawing actions “rubber-band” – as the user drags the mouse, the program should show the line or the rectangle being dragged out. However, it should not destroy the bits of the drawing that it is dragged over. Hint: use the invertLine, invertRect or invertOval methods

Make the Fill/NoFill and Colour buttons display the currently selected state and colour in some way.

Add a Polygon button and a slider that lets the user add a regular polygon (triangle, square, pentagon, hexagon, etc) to the drawing. The slider controls how many sides the polygon will have.

Add a “Curve” button which will allow the user to draw nice curved lines. Curved lines need at least three points to specify them. Ideally, the user should be able to keep adding points to a curve. (Look up Bezier curves to do this really nicely!)

import ecs100.*;

import java.awt.Color;

import javax.swing.JColorChooser;

import javax.swing.JButton;




/**

* A simple drawing program.

* The user can select from a variety of tools and options using the buttons and

*   elements down the left side, and can use the mouse to add elements to the drawing

*   according to the current tool and options

* Note, most of the “action” in the program happens in response to mouse events;

*   the buttons, textFields, and sliders mostly record information that is used

*   later by the mouse responding.

*/







public class MiniPaint{




// fields to remember:

//  – the “tool” – what will be drawn when the mouse is next released.

//                 may be a shape, or an image, or a caption,

//    [Completion] or freehand, or eraser

//  – whether the shape should be filled or not

//  – the position the mouse was pressed,

//  – the string for the text caption

//  – the width of the lines and the font size of the text captions.

//  – [Completion] the name of the image file

//  – [Completion] the colors for the border and fill for shapes and captions




private String tool = “Line”;   // the current tool, governing what the mouse will do.

// Initial value is “Line”;  changed by the buttons.




// More fields

/*# YOUR CODE HERE */




/**

* Set up the interface: buttons, textfields, sliders,

* listening to the mouse

*/

public void setupGUI(){

UI.addButton(“Clear”, UI::clearGraphics);

UI.addButton(“Line”, this::doSetLine);

/*# YOUR CODE HERE */




UI.addButton(“Quit”, UI::quit);

UI.setDivider(0.0);  // Hide the text area.

}







// Methods to respond to the buttons, textfield, and sliders

// Mostly, These methods just save information to the fields.




/** Respond to the Line button */

public void doSetLine(){

/*# YOUR CODE HERE */




}




// The method header for doSetLine was given as an example; you will need other methods

// for each button/textfield/slider

// See hints in the Assignment description.










/**

* Respond to mouse events

* When pressed, remember the position.

* When released, draw what is specified by current tool

* Uses the value stored in the field to determine which kind of tool to draw.

*  It should call the drawALine, drawARectangle, drawAnOval, etc, methods

*  passing the pressed and released positions

* [Completion] should respond to “dragged” events also to do erasing and freehand drawing

*/

public void doMouse(String action, double x, double y) {

/*# YOUR CODE HERE */




}




/**

* Draw a line between the two positions (x1, y1) and (x2, y2)

*/

public void drawALine(double x1, double y1, double x2, double y2){

/*# YOUR CODE HERE */




}




/**

* Draw a rectangle between the two diagonal corners

* [Completion] Works out the left, top, width, and height

* Then draws the rectangle, based on the options

*/

public void drawARectangle(double x1, double y1, double x2, double y2){

/*# YOUR CODE HERE */




}




/**

* Draw an oval to fit the rectangle between the the two diagonal corners

* [Completion] Works out the left, top, width, and height

* Then draws the oval, based on the options

*/

public void drawAnOval(double x1, double y1, double x2, double y2){

/*# YOUR CODE HERE */




}




/**

* Draws the current caption at the mouse released point.

*/

public void drawCaption(double x, double y){

/*# YOUR CODE HERE */




}







/** [Completion]

* Draws the current image between the two diagonal corners, unless

*  they are very close, and then just draws the image at its natural size

*  Works out the left, top, width, and height

* Then draws the image, if there is one.

*/

public void drawAnImage(double x1, double y1, double x2, double y2){

/*# YOUR CODE HERE */




}

























// Main:  constructs a new MiniPaint object and set up GUI

public static void main(String[] arguments){

MiniPaint mp = new MiniPaint();

mp.setupGUI();

}







output:

}