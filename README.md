Download Link: https://assignmentchef.com/product/solved-cs1331-homework-08-a-game-of-life
<br>
<span style="font-size: 2.61792em; letter-spacing: -1px;">Problem Description</span>

You were uploading some changes to the Matrix (fixing some bugs regarding fidget spinners) when finally instead of clicking “submit” you accidentally clicked “delete everything”. You had mentioned in a team meeting that it really doesn’t make sense to have a “delete everything” button, but your boss Carl has a sense of flare and insisted on keeping it for dramatic effect. And so, just like that, the Matrix disapeared with billions of humans now without a simulation to live in. To prevent the humans from waking up and

revolting, program a simple simulation to keep things under control.

<h1>Solution Description</h1>

Your task will be to simulate a population of cells. Your simulation will consist of a 2D array that we will call our universe. This 2D array will contain all of the Cells that make up our basic universe. For this assignment you have been provided Cell.java, a simple class that will represent a cell. Like all cells, a Cell is either dead or alive.

You will also be provided part of the Board.java class – to complete this assignment you should correctly fill in the body of each method as specified. You may create more methods and fields if you like but you may not modify the existing method headers.

The following fields are included in the provided code and should remain as is:

private Cell[][] universe; private int dimensionLength = 0; private int generationCount = 0;

<strong>The following are methods for you to complete:</strong>

<ul>

 <li><strong>public Board(int dimensionLength, int[][] seed)</strong></li>

</ul>

This constructor should do the following: 1. Assign instance variable dimensionLength the value of the respective parameter. 2. Instantiate universe to be a 2D Cell array of size dimensionLength x dimensionLength 3. Loop through each Cell in universe and instantiate them with the default constructor 4. Call method applySeed with the seed array (more on this later – see the applySeed section)

For this homework you may assume dimensionLength will be at least 4, and `seed` will contain at least o

<ul>

 <li><strong>private void applySeed(int[][] seed)</strong></li>

</ul>

This method determines what cells will start off alive in universe. Loop through universe and make the Cells “alive” where the corresponding entry in the seed array is not 0. You may assume that seed has the same dimensions of universe.

Ex) if seed[3][2] == 3, then universe[3][2].setAlive(true)

<ul>

 <li><strong>private int getCellStatus(Cell[][] arr, int x, int y)</strong></li>

</ul>

Return <em>0 </em>if arr[x][y] is out of bounds or the Cell at that location is dead; otherwise return 1. This method is used by the provided getAliveNeighbors method.

<ul>

 <li><strong>public void tick()</strong></li>

</ul>

This method should progress the universe one step forward and increment generationCount by one accordingly. During this method you should iterate through universe and for each Cell decide if it should be dead or alive based on the following criteria. Note: You should consider these factors only for the current generation of cells. The updated values of cells should not be taken into account when computing the next generation. (Hint: it might be helpful to store a temporary universe array to temporarily store the updated cells)

<em>Be sure to use the provided </em><em>getAliveNeighbors method to help you implement this method.</em>

<ol>

 <li><strong>Underpopulation</strong>: Any living cell with less than two neighbors dies</li>

 <li><strong>Overpopulation</strong>: Any living cell with more than three neighbors dies</li>

 <li><strong>Continuation</strong>: Any living cell with either two or three neighbors continues to live</li>

 <li><strong>Reproduction</strong>: Any dead cell with exactly three neigbors becomes alive <strong>The following methods have been provided to you:</strong></li>

</ol>

<strong>public String toString()</strong>

Will return a simple visualization of universe and generationCount <strong>private int getAliveNeighbors(Cell[][] arr, int x, int y)</strong>

This method depends on your correct implementation of the above getCellStatus method. It will return the number of living neighbors for any given cell. <em>You need not do anything for this method, however</em>

<em>understanding it is crucial for this assignment.</em>

<h1>Testing</h1>

We encourage you to write your own tests for this assignment. Create a Test.java file, instantiate a Board and try out different seeds. You can use something like the following:

<table width="632">

 <tbody>

  <tr>

   <td width="632"><strong>public class </strong>Test { <strong>public </strong>static void main(String[] args) { int[][] seed = {{0, 1, 0, 0, 1},{0, 0, 1, 1, 1},{0, 0, 0, 0, 0},{0, 0, 0, 0, 1},{1, 1, 0, 0, 0}};Board b = <strong>new </strong>Board(5, seed); System.out.println(b);<strong>for </strong>(int i = 0; i &lt; 10; i++) {b.tick();System.out.println(b);}}}</td>

  </tr>

 </tbody>

</table>

<h1>Inspiration</h1>

This problem is an implementation of <em>Conway’s Game Of Life</em>. It’s just a peak into the world of cellular automata!

<h1>Rubric</h1>

<h2>• [22] constructor</h2>

<ul>

 <li>[4] Assign distanceLength resepective value and make variable private</li>

 <li>[4] Instantiate universe correctly and make variable private</li>

 <li>[11] Universe has no null values</li>

 <li>[3] applySeed method is called</li>

 <li>[15] applySeed

  <ul>

   <li>[15] Correctly sets initial state</li>

  </ul></li>

 <li>[10] getCellStatus

  <ul>

   <li>[4] Returns 0 if out of bounds</li>

   <li>[3] Returns 0 if dead</li>

   <li>[3] Returns 1 if alive</li>

  </ul></li>

 <li>[55] tick

  <ul>

   <li>[3] Increments generationCount</li>

   <li>[13] Underpopulation</li>

   <li>[13] Overpopulation</li>

   <li>[13] Continuation</li>

   <li>[13] Reproduction</li>

  </ul></li>

</ul>

<strong>Import Restrictions</strong>

You may not import anything for this homework assignment.

<h1>Feature Restrictions</h1>

There are a few features and methods in Java that overly simplify the concepts we are trying to teach or break our auto grader. For that reason, do not use any of the following in your final submission:

<ul>

 <li>var (the reserved keyword)</li>

 <li>exit</li>

 <li>try/catch blocks</li>

</ul>

<h1>Javadocs</h1>

For this assignment, you will be commenting your code with Javadocs. Javadocs are a clean and useful way to document your code’s functionality. For more information on what Javadocs are and why they are awesome, the <a href="http://www.oracle.com/technetwork/java/javase/documentation/index-137868.html">online overview</a> for them is extremely detailed and helpful.

You can generate the javadocs for your code using the command below, which will put all the files into a folder called javadoc:

$ javadoc *.java -d javadoc

The relevant tags that you need to include are @author, @version, @param, and @return. Here is an example of a properly Javadoc’d class:

<strong>import </strong>java.util.Scanner;

<em>/**</em>

<ul>

 <li>This class represents a Dog object<em>.</em></li>

 <li><strong>@author </strong>George P<em>. </em>Burdell</li>

 <li><strong>@version </strong><em>0</em></li>

</ul>

<table width="632">

 <tbody>

  <tr>

   <td width="632"><em>*/ </em><strong>public class </strong>Dog {<em>/**</em>* Creates an awesome dog <em>(</em>NOT a dawg<em>!)</em><em>*/ </em><strong>public </strong>Dog() { …}<em>/**</em>* This method takes in two ints and returns their sum* <strong>@param a </strong>first number* <strong>@param b </strong>second number <em>* </em><strong>@return </strong>sum of a and b<em>*/ </em><strong>public </strong>int add(int a, int b) {…}}</td>

  </tr>

 </tbody>

</table>

A more thorough tutorial for Javadocs can be found <a href="https://cs1331.gitlab.io/cs1331-style-guide.html">here</a>. Take note of a few things:

<ol>

 <li>Javadocs are begun with /** and ended with */.</li>

 <li>Every class you write must be Javadoc’d and the @author and @verion tag included. The comments for a class should start with a brief description of the role of the class in your program.</li>

 <li>Every non-private method you write must be Javadoc’d and the @param tag included for every method parameter. The format for an @param tag is @param &lt;name of parameter as written in method header&gt; &lt;description of parameter&gt;. If the method has a non-void return type, include the @return tag which should have a simple description of what the method returns, semantically.</li>

</ol>

<ul>

 <li></li>

</ul>