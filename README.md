Download Link: https://assignmentchef.com/product/solved-cs0445-project-3-sudoku-solving
<br>
In this assignment, you will be implementing a <strong>backtracking</strong> algorithm to solve Sudoku puzzles. If you aren’t familiar (or even if you are and need a refresher), <a href="https://www.sudoku.name/rules/en">have a look at this site</a>.

Starting point

<a href="/teaching/classes/cs0445/projects/cs0445_proj3_materials.zip">Download and extract these materials.</a> Contained are:

<ul>

 <li>Sudoku.java, <strong>the file you will modify.</strong></li>

 <li>5 .su files, which are <strong>plain text files</strong> containing Sudoku puzzles to solve.

  <ul>

   <li>Since they’re plain text files (like java files), you can open them in your text/code editor.</li>

  </ul></li>

</ul>

Sudoku.java contains the following:

<ul>

 <li>a main method which can accept some command-line arguments.</li>

 <li>the readBoard method, which reads a board from a file. main calls this.

  <ul>

   <li>“Unsolved” (empty) cells contain 0s.</li>

  </ul></li>

 <li>the printBoard method, which prints the board to the console, which will be very helpful.</li>

 <li>the solve backtracking template method.</li>

 <li>and finally, 8 “skeleton” methods for you to fill out.

  <ul>

   <li>you know, cause Halloween. &#x1f480;</li>

  </ul></li>

</ul>

<h2>Testing</h2>

<strong>We will be testing your code on the command line.</strong> You are welcome to use an IDE, but before submitting, please test that your Java files can be compiled and run on the command line without it.

We should be able to run your program like so:

java Sudoku -t

to run all the test methods, or:

java Sudoku 2-easy.su

to load and solve a Sudoku board file.

The main we gave you handles this command-line interface. But right now, nothing happens &#x1f642;

<h2>Your task</h2>

This is a tough project. As such, <strong>60% of the grade is for correctness, and 40% is for the thoroughness of your testing methods.</strong>

You will implement four methods to solve the problem: isFullSolution, reject, extend, and next.

To complement those four, there are four testing methods: testIsFullSolution, testReject, testExtend, and testNext. Each of these should make <strong>several tests</strong> of the corresponding solving methods.

<h3>The puzzle-solving algorithm</h3>

By implementing the four solving methods, you will be constructing a backtracking solver program. Important points:

<ul>

 <li>You must not change any of the original numbers already on the board.</li>

 <li>You must implement all the Sudoku rules: each row, column, and 3×3 square may only contain each number once.</li>

 <li>You only need to find <em>one</em> solution, not all solutions. Once you find a solution, you can stop.</li>

 <li>If a board is not solvable, your program must say so.</li>

</ul>

<h3>The puzzle-solving methods</h3>

These methods make up the four parts of the backtracking template. These methods are <strong>not recursive!</strong> Only the solve method is, and we already wrote that for you &#x1f609;

<ul>

 <li>boolean isFullSolution(int[][] board)

  <ul>

   <li>This takes a board as a 2D array, and returns true if it is complete (no empty cells) and satisfies all the rules.</li>

   <li>If there are any empty cells, or if there are any rule violations, it returns false.</li>

  </ul></li>

 <li>boolean reject(int[][] board)

  <ul>

   <li>This takes a <em>partial</em> solution, and returns true if it is <strong>impossible</strong> to continue with this board.</li>

   <li>For example, if there are two 3’s on one row, there is no reason to keep solving this board.</li>

  </ul></li>

 <li>int[][] extend(int[][] board)

  <ul>

   <li>This takes a <em>partial</em> solution, and constructs a <strong>new</strong> partial solution.

    <ul>

     <li>When I say “new” I mean use new to allocate a new 2D array!</li>

    </ul></li>

   <li>What I mean by “constructs a new partial solution” is it <strong>places a number into a previously-empty cell.</strong></li>

   <li>If there are no more possible cells to place a number in, it should return <strong>null.</strong></li>

  </ul></li>

 <li>int[][] next(int[][] board)

  <ul>

   <li>The partner to extend. This takes a <em>partial</em> solution, and constructs another <strong>new</strong> partial solution.</li>

   <li>It will <strong>change the most-recently-placed number</strong> to the next possible option.

    <ul>

     <li>So if the most-recently-placed number was a 1, this would change it to a 2…</li>

     <li>…or a 2 to a 3, or a 3 to a 4, and so on.</li>

    </ul></li>

   <li>If there are no options for the most-recently-placed number, it should return <strong>null.</strong></li>

  </ul></li>

</ul>

<strong>Do not write all the methods at once.</strong> Start with isFullSolution and reject. Test them extensively with your testing methods (by running your program with java Sudoku -t).

<h3>The testing methods</h3>

Re-read starting at Chapter 2.16 to review the concepts behind writing test methods. Write your testing methods <em>at the same time you write the solving methods.</em> Have a look at <a href="/teaching/classes/cs0445/examples/Ex18QueensBacktracking.java">this 8-Queens example</a> to see some example testing methods.

For each of the testing methods, try to follow these guidelines:

<ul>

 <li>Come up with a variety of partial solutions that will test all possible paths through your solving method.</li>

 <li>Call the method with those partial solutions.</li>

 <li>Check that the method actually returns what you expect it to return.</li>

 <li>Print out the test cases and results, so that you can easily see if things are looking right.</li>

 <li>Include enough test cases that you are convinced that your solving method is working properly.</li>

</ul>

You can make new board files following the guidelines below, and then use readBoard to load them for testing.

For example, if I were testing the reject method, I would give it…

<ul>

 <li>a board with two of the same number in the same row.</li>

 <li>a board with two of the same number in the same column.</li>

 <li>a board with two of the same number in a 3×3 square.

  <ul>

   <li>(probably a few versions of that, to be thorough.)</li>

  </ul></li>

 <li>the boards we gave you (1-trivial.su etc.) to make sure it <em>doesn’t</em> reject those.</li>

 <li>a solved board (look online for one) to make sure it <em>doesn’t</em> reject that.</li>

</ul>

<h2>Example boards</h2>

We’ve included 5 example boards (the .su files). If you open them in your text editor, you will see they look something like this:

3__79425_2__56_19779_82_4_3_2__78_4157_1_6_821483_29769_7_856_44526_7839_164397_5

There are 9 rows, and each has 9 columns. Any non-number character is treated as an empty (unsolved) cell.

You can open one of the existing files and “File &gt; Save As…” to make your own boards. Make a bunch! It’s fine!