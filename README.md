Download Link: https://assignmentchef.com/product/solved-comp472-assignment-2-the-%cf%87-puzzle
<br>
<h1>1           The <em>χ</em>-Puzzle</h1>

In this assignment you will implement and analyse a variety of search algorithms to solve the <em>χ</em>-Puzzle.

<h2>1.1         Rules of the Puzzle</h2>

The <em>χ</em>-Puzzle is a type of sliding-puzzle played on a wrapping board. The rules of the <em>χ</em>-Puzzle are the following:

<ol>

 <li>The puzzle is an 2 × 4 board with 8 tiles (7 numbered and 1 empty).</li>

 <li><em>Regular moves: </em>Regular horizontal and vertical moves of sliding-puzzles are allowed and have a cost of 1.</li>

 <li><em>Wrapping moves: </em>If the empty tile is at a corner position, then the numbered tile at the other end of the same row can slide into it. These moves are more expensive than regular moves, and have a cost of 2.</li>

 <li><em>Diagonal moves: </em>If the empty tile is at a corner position, then the numbered tile diagonally adjacent to it inside the board, as well as the numbered tile in the opposed corner can be moved into it. These moves are more expensive than regular moves, and have a cost of 3.</li>

 <li>The goal of the puzzle is to reach either one of the 2 goals below with the lowest cost.</li>

</ol>

<table width="206">

 <tbody>

  <tr>

   <td width="24">1</td>

   <td width="24">2</td>

   <td width="24">3</td>

   <td width="24">4</td>

   <td rowspan="2" width="17"> </td>

   <td width="24">1</td>

   <td width="24">3</td>

   <td width="24">5</td>

   <td width="24">7</td>

  </tr>

  <tr>

   <td width="24">5</td>

   <td width="24">6</td>

   <td width="24">7</td>

   <td width="24">0</td>

   <td width="24">2</td>

   <td width="24">4</td>

   <td width="24">6</td>

   <td width="24">0</td>

  </tr>

 </tbody>

</table>

<h2>1.2         Examples</h2>

Here are a few examples, to better understand the rules of the puzzle.

<table width="95">

 <tbody>

  <tr>

   <td width="24">4</td>

   <td width="24">2</td>

   <td width="24">3</td>

   <td width="24">1</td>

  </tr>

  <tr>

   <td width="24">5</td>

   <td width="24">6</td>

   <td width="24">7</td>

   <td width="24">0</td>

  </tr>

 </tbody>

</table>

<strong>Example 1         </strong>Assume that the initial board is:

Then there are 5 possible moves:

1-2: regular moves – the 1 can move down into the 0 (with a cost of 1 – see rule #2 above) and the 7 can move right into the 0 (with a cost of 1 – see rule #2 above);

3: wrapping move – the 5 can move into the 0 (with a cost of 2 – rule #3 above).

4-5: diagonal moves – the 3 can move diagonally into the 0 (with a cost of 3 – see rule #4 above) and the 4 can can move diagonally into the 0 (with a cost of 3 – see rule #4 above);

.

These would lead to the following successor nodes:

<table width="541">

 <tbody>

  <tr>

   <td width="326">


    <table width="318">

     <tbody>

      <tr>

       <td width="24">4</td>

       <td width="24">2</td>

       <td width="24">3</td>

       <td width="24">0</td>

       <td rowspan="2" width="17"> </td>

       <td width="24">4</td>

       <td width="24">2</td>

       <td width="24">3</td>

       <td width="24">1</td>

       <td rowspan="2" width="17"> </td>

       <td width="24">4</td>

       <td width="24">2</td>

       <td width="24">3</td>

       <td width="24">1</td>

      </tr>

      <tr>

       <td width="24">5</td>

       <td width="24">6</td>

       <td width="24">7</td>

       <td width="24">1</td>

       <td width="24">5</td>

       <td width="24">6</td>

       <td width="24">0</td>

       <td width="24">7</td>

       <td width="24">0</td>

       <td width="24">6</td>

       <td width="24">7</td>

       <td width="24">5</td>

      </tr>

     </tbody>

    </table></td>

   <td width="215">


    <table width="206">

     <tbody>

      <tr>

       <td width="24">4</td>

       <td width="24">2</td>

       <td width="24">0</td>

       <td width="24">1</td>

       <td rowspan="2" width="17"> </td>

       <td width="24">0</td>

       <td width="24">2</td>

       <td width="24">3</td>

       <td width="24">1</td>

      </tr>

      <tr>

       <td width="24">5</td>

       <td width="24">6</td>

       <td width="24">7</td>

       <td width="24">3</td>

       <td width="24">5</td>

       <td width="24">6</td>

       <td width="24">7</td>

       <td width="24">4</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

<table width="95">

 <tbody>

  <tr>

   <td width="24">1</td>

   <td width="24">2</td>

   <td width="24">3</td>

   <td width="24">4</td>

  </tr>

  <tr>

   <td width="24">5</td>

   <td width="24">6</td>

   <td width="24">0</td>

   <td width="24">7</td>

  </tr>

  <tr>

   <td width="24"> </td>

   <td width="24"> </td>

   <td width="24"> </td>

   <td width="24"> </td>

  </tr>

  <tr>

   <td width="24">1</td>

   <td width="24">0</td>

   <td width="24">3</td>

   <td width="24">4</td>

  </tr>

  <tr>

   <td width="24">5</td>

   <td width="24">6</td>

   <td width="24">2</td>

   <td width="24">7</td>

  </tr>

 </tbody>

</table>

<strong>Example 2                            </strong>Assume that the initial board is, then there are 3 possible moves: (3, 6, 7).

<strong>Example 3                            </strong>Assume that the initial board is, then there are 3 possible moves: (6, 1, 3).

<h1>2           Your Task</h1>

Implement a solution for the <em>χ</em>-board using the following 3 search algorithms:

<ol>

 <li>Uniform Cost (UCS)</li>

 <li>Greedy Best First (GBFS)</li>

 <li>Algorithm <em>A<sup>? </sup></em>(<em>A<sup>?</sup></em>)</li>

</ol>

For GBFS and <em>A<sup>?</sup></em>, you must develop and experiment with 2 different heuristics <em>h</em><sub>1 </sub>and <em>h</em><sub>2</sub>. <em>h</em><sub>1 </sub>and <em>h</em><sub>2 </sub>should both be used with GBFS and with <em>A<sup>?</sup></em>.

For the demo (see Section 4.1) you will run your code with the following naive heuristic, <em>h</em><sub>0</sub>.

<em> ,</em>regardless of the values of <em>x</em><sub>1</sub><em>,x</em><sub>2</sub><em>,x</em><sub>3</sub><em>,x</em><sub>3</sub><em>,x</em><sub>4</sub><em>,x</em><sub>5</sub><em>,x</em><sub>6</sub><em>,x</em><sub>7</sub>

<sup></sup>1<em>,    </em>otherwise

The 2 heuristics that you developed (<em>h</em><sub>1 </sub>and <em>h</em><sub>2</sub>) cannot be equal to <em>h</em><sub>0</sub>.

<h2>2.1         Programming Environment</h2>

To program the project, you must use Python 3.8. In addition, you must use GitHub (make sure your project is private while developing).

<h2>2.2         The Input</h2>

Your code should be able to receive the path of an input file that contains initial puzzles. The input file will contain a sequence of lines, containing the values of the initial puzzle where each tile will be represented by a unique integer (0 to 7), where the zero will denote the empty tile. For example, the input file could contain:

1 0 3 7 5 2 6 4 puzzle #0

<ul>

 <li>3 7 5 2 6 4 1 puzzle #1</li>

 <li>0 3 7 5 2 6 4 puzzle #2</li>

</ul>

<table width="95">

 <tbody>

  <tr>

   <td width="24">1</td>

   <td width="24">0</td>

   <td width="24">3</td>

   <td width="24">7</td>

  </tr>

  <tr>

   <td width="24">5</td>

   <td width="24">2</td>

   <td width="24">6</td>

   <td width="24">4</td>

  </tr>

 </tbody>

</table>

where puzzle #0 represents

There is no need to check the validity of the input file; you can assume that it will be correct.

<h2>2.3         Output</h2>

For each input puzzle and each search algorithm, your program should generate 2 output files: one for the solution path, and one for the search path. This means that for each line of the input file (see Section 2.2), your program should generate 10 text files:

Solution files                                   Search files

# ucs solution.txt                           # ucs search.txt

# gbfs-h1 solution.txt                   # gbfs-h1 search.txt

# gbfs-h2 solution.txt                   # gbfs-h2 search.txt

# astar-h1solution.txt # astar-h1 search.txt

# astar-h2solution.txt # astar-h2 search.txt

where # is the puzzle number starting at zero.

For example, for puzzle #0 in of the input file in Section 2.2, you should generate:

Solution files                                   Search files

0 ucs solution.txt                           0 ucs search.txt

0 gbfs-h1 solution.txt                   0 gbfs-h1 search.txt

0 gbfs-h2 solution.txt                   0 gbfs-h2 search.txt

0 astar-h1solution.txt 0 astar-h1 search.txt

0 astar-h2solution.txt 0 astar-h2 search.txt

<h3>2.3.1         Solution Files</h3>

Each solution file will contain the final solution found by the algorithm, or the string no solution. If a solution is found, the format of the file should be:

<ol>

 <li>on line 1: 0 0 (two zero’s) followed by the initial configuration (each tile separated by a space)</li>

 <li>for each subsequent line: the token to move, a space, the cost of the move, a space, the new configuration of the board (each tile separated by a space)</li>

 <li>the final line should contain the cost of the entire solution path, a space, then the execution time in seconds.</li>

</ol>

<em>0, 0, then the initial puzzle move tile 1 with a cost of 1, which will lead to the new configuration</em>

…

<em>cost of the solution path and execution time</em>

<table width="100">

 <tbody>

  <tr>

   <td width="100">no solution</td>

  </tr>

 </tbody>

</table>

If your program cannot find a solution after 60 seconds, then it should output:in both the solution and the search files.

<h3>2.3.2         Search Files</h3>

Each search file will contain the search path (the list of nodes that have been searched) by the algorithm. The search files should contain 1 line for each node searched. Each line should contain the <em>f</em>(<em>n</em>), <em>g</em>(<em>n</em>) and <em>h</em>(<em>n</em>) values of the node separated by a space, followed by the configuration of the puzzle. For example:

15 10 5 4 2 3 1 5 6 7 0 <em>f</em>(<em>n</em>) = 15<em>,g</em>(<em>n</em>) = 10<em>,h</em>(<em>n</em>) = 5, state = 4 2 3 1 5 6 7 0

9 3 6 4 2 3 0 5 6 7 1                       <em>f</em>(<em>n</em>) = 9<em>,g</em>(<em>n</em>) = 3<em>,h</em>(<em>n</em>) = 6, state = 4 2 3 0 5 6 7 1

If the value of <em>f</em>(<em>n</em>), <em>g</em>(<em>n</em>) or <em>h</em>(<em>n</em>) are irrelevant for a specific search algorithm, just display its value as zero (0).

<h2>2.4         Analysis</h2>

Once your code is running, you will need to analyse and compare the performance of the algorithms and the heuristics. Generate a file with 50 random puzzles, then use this file as input to your 5 algorithms and compile the following data for each algorithm:

<ol>

 <li>average &amp; total length of the solution and search paths,</li>

 <li>average &amp; total number of no solution,</li>

 <li>average &amp; total cost and execution time,</li>

 <li>optimality of the solution path.</li>

</ol>

Prepare a few slides explaining your heuristics and presenting and analysing the above data. You will present these slides at the demo (see Section 4.1.1). Your analysis should compare the data above across search algorithms and across heuristics.

<h2>2.5         Scaling Up</h2>

Once your analysis is done (see Section 2.4), take your best-performing algorithm and run it on a scaled-up version of the puzzle. This means that instead of using a 2 × 4 puzzle, increase the dimensions of the puzzle gradually and perform tests with random puzzles to see how the size of the puzzle influences the performance of your search. You can remove the 60-second time-out for this experiment. Note that on puzzles with more than 2 rows, the <em>wrapping moves </em>(applicable when the empty tile is at a corner position) allows the numbered tile at the other end of the same row as the empty tile to slide into it – but also allows the numbered tile at the other end of the same <u>column </u>as the empty tile to slide into it.

Prepare 1 or 2 slides presenting your analysis of the scaled-up puzzle, to present at the demo (see Section 4.1.1).

<h1>3           Competition (Just for fun)</h1>

Just for the fun of it, we will organize a competition to compare the solutions found by different teams with the same set of input puzzles. This competition will not count for points, we are just doing this for fun (and for the thrill of having your team publicly acknowledged on the Moodle page as the winner of the competition!).

For the competition, we will give all teams a file with random puzzles, and teams will be ranked based on the total cost of the solutions and execution time. More details on the competition will be posted on Moodle.

<h1>4           Deliverables</h1>

The submission of the project will consist of 2 deliverables: the code and a demo.

<h2>4.1         The Demos</h2>

You will have to demo your code to the TAs. Regardless of the demo time, you will demo the program that was uploaded as the official submission on or before the due date. The schedule of the demos will be posted on Moodle. The demos will consist in 2 parts: a small presentation of your analysis and a Q/A.

<h3>4.1.1         Presentation of your analysis</h3>

Prepare a few slides for a 5 minute presentation explaining your heuristics, your analysis and your scaled-up experiment (see Sections 2.4 and 2.5).

<h3>4.1.2         Q/A</h3>

No special preparation is necessary for the Q/A part of the demo. Your TA will give you a small input file of puzzles (the 2 version) and you will run all 5 algorithms with <em>h</em><sub>0</sub>. Your will generate the corresponding output files and upload them on EAS during the demo.

In addition, your TA will ask each student questions on the code/assignment, and the student will be required to answer the TA satisfactorily. Hence every member of team is expected to attend the demo. Your individual grade will be a function of your individual Q/A (see Section 5).

<h1>5           Evaluation Scheme</h1>

Students in teams can be assigned different grades based on their individual contribution to the project. Individual grades will be based on:

<ol>

 <li>a peer-evaluation done after the deadline.</li>

 <li>the contribution of each student as indicated on GitHub.</li>

 <li>the Q/A of each student during the demo.</li>

</ol>

The team grade will be based on: