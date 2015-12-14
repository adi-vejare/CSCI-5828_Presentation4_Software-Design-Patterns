###Example
<p>The <code>DrawAPI</code> interface acts as a bridge implementer. Concrete classes <code>RedCircle</code> and
<code>GreenCircle</code> implement the <code>DrawAPI</code> interface. 
<>Shape is an abstract class and will use object of <code>DrawAPI</code>.</p>

###Code
<b>Bridge implementer interface <code>DrawAPI</code></b>
<pre><code>public interface DrawAPI {
   public void drawCircle(int radius, int x, int y);
}</code></pre>

<b>Concrete classes <code>RedCircle</code> and <code>GreenCircle</code> implementing <code>DrawAPI</code></b>
<pre><code>public class RedCircle implements DrawAPI {
   @Override
   public void drawCircle(int radius, int x, int y) {
      System.out.println("Drawing Circle[ color: red, radius: " + radius + ", x: " + x + ", " + y + "]");
   }
}</code></pre>
<pre><code>public class GreenCircle implements DrawAPI {
   @Override
   public void drawCircle(int radius, int x, int y) {
      System.out.println("Drawing Circle[ color: green, radius: " + radius + ", x: " + x + ", " + y + "]");
   }
}</code></pre>

<b>Abstract class <code>Shape</code> created using <code>DrawAPI</code>
<pre><code>public abstract class Shape {
   protected DrawAPI drawAPI;
   
   protected Shape(DrawAPI drawAPI){
      this.drawAPI = drawAPI;
   }
   public abstract void draw();	
}</code></pre>

<b>Concrete class <code>Circle</code>implementing  <code>Shape</code>
<pre><code>public abstract class Shape {
   protected DrawAPI drawAPI;
   
   protected Shape(DrawAPI drawAPI){
      this.drawAPI = drawAPI;
   }
   public abstract void draw();	
}</code></pre>


<b><code>BridgePatternDemo</code> drawing red and green circles using <code>Shape</code> and <code>DrawAPI</code></b>
<pre><code>public class BridgePatternDemo {
   public static void main(String[] args) {
      Shape redCircle = new Circle(100,100, 10, new RedCircle());
      Shape greenCircle = new Circle(100,100, 10, new GreenCircle());

      redCircle.draw();
      greenCircle.draw();
   }
}</code></pre>

<b>Output</b>
<pre><code>Drawing Circle[ color: red, radius: 10, x: 100, 100]
Drawing Circle[  color: green, radius: 10, x: 100, 100]
</code></pre>
