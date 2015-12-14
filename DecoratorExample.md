###Example
<p> A <code>Shape</code> interface is created. Concrete classes  and an
abstract decorator class <code>ShapeDecorator</code> are also created. 
Both of them implement the <code>Shape</code> interface.  
<code>Shape</code> object is the instance variable for the decorator class.</p>


###Code
<b><code>Shape</code> interface</b>
<pre><code>public interface Shape {
   void draw();
}</code></pre>

<b>Concrete class <code>Rectangle</code> implementing <code>Shape</code></b>
<pre><code>public class Rectangle implements Shape {

   @Override
   public void draw() {
      System.out.println("Shape: Rectangle");
   }
}</code></pre>

<b>Concrete class <code>Circle</code> implementing <code>Shape</code></b>
<pre><code>public class Circle implements Shape {

   @Override
   public void draw() {
      System.out.println("Shape: Circle");
   }
}</code></pre>


<b>Abstract decorator class <code>ShapeDecorator</code> implementing <code>Shape</code></b>
<pre><code>public abstract class ShapeDecorator implements Shape {
   protected Shape decoratedShape;

   public ShapeDecorator(Shape decoratedShape){
      this.decoratedShape = decoratedShape;
   }

   public void draw(){
      decoratedShape.draw();
   }	
}</code></pre>


<b>Concrete decorator class <code>RedShapeDecorator</code> extending <code>ShapeDecorator</code></b>
<pre><code>public class RedShapeDecorator extends ShapeDecorator {

   public RedShapeDecorator(Shape decoratedShape) {
      super(decoratedShape);		
   }

   @Override
   public void draw() {
      decoratedShape.draw();	       
      setRedBorder(decoratedShape);
   }

   private void setRedBorder(Shape decoratedShape){
      System.out.println("Border Color: Red");
   }
}</code></pre>


<b><code>RedShapeDecorator</code> decorating <code>Shape</code> objects</b>
<pre><code>public class DecoratorPatternDemo {
   public static void main(String[] args) {

      Shape circle = new Circle();

      Shape redCircle = new RedShapeDecorator(new Circle());

      Shape redRectangle = new RedShapeDecorator(new Rectangle());
      System.out.println("Circle with normal border");
      circle.draw();

      System.out.println("\nCircle of red border");
      redCircle.draw();

      System.out.println("\nRectangle of red border");
      redRectangle.draw();
   }
}</code></pre>

<b>Output</b>
<pre><code>Circle with normal border
Shape: Circle

Circle of red border
Shape: Circle
Border Color: Red

Rectangle of red border
Shape: Rectangle
Border Color: Red</code></pre>


[<img src="https://cloud.githubusercontent.com/assets/14101008/11768481/3b7d20d6-a18b-11e5-95fe-a422966f4c03.png" width="50" height="50"></img>](https://github.com/hariniiyer/CSCI-5828_Presentation4_Software-Design-Patterns/blob/master/DecoratorFeatures.md)
[<img src="https://cloud.githubusercontent.com/assets/14101008/11768482/3d2d0bbc-a18b-11e5-8766-2e7f5b241782.png" width="50" height="50"></img>](https://github.com/hariniiyer/CSCI-5828_Presentation4_Software-Design-Patterns/blob/master/A&DCompare.md)
