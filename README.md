Download Link: https://assignmentchef.com/product/solved-cnt4714-project5-sneakyqueens
<br>
This is a warm-up assignment to get you thinking mathematically, algorithmically, and <em>cleverly</em>. It will encourage you to think in terms of implementing efficient solutions to problems, since your program needs to have a worst-case runtime that does not exceed O(<em>m</em> + <em>n</em>) (linear runtime). It’s also a fairly gentle return to Java for those who haven’t used it in a while, and involves a direct application of the base conversion knowledge you gained in Computer Science 1 (albeit with a minor twist).

You might find this problem very tricky at first. It’s important to struggle with it. Don’t be discouraged if you don’t solve it right away. Maybe walk away, take a break, and come back to it later (perhaps even the following day). You might be amazed by what your brain can do if you let it work on a problem in the background and/or if you come back to a problem well-rested, with a fresh perspective.

Please feel free to seek out help in office hours if you’re lost, and remember that it’s okay to have conceptual discussions with other students about this problem, as long as you’re not sharing code (or pseudocode, which is practically the same thing). Just keep in mind that you’ll benefit more from this problem if you struggle with it a bit before discussing it with anyone else.

<h1>Deliverables</h1>

SneakyQueens.java

<strong><em>Note!</em></strong> The capitalization and spelling of your filename matter!

<strong><em>Note!</em></strong> Code must be tested on Eustis, but submitted via Webcourses.

<h1>1.        Problem Statement</h1>

You will be given a list of coordinate strings for queens on an arbitrarily large square chess board, and you need to determine whether any of the queens can attack one another in the given configuration.

In the game of chess, queens can move any number of spaces in any of eight directions: up, down, left, right, or any of four possible diagonal directions (up-left, up-right, down-left, or down-right). For example, the queen on the following board (denoted with a letter ‘Q’) can move to any position marked with an asterisk (‘*’), and no other positions:

<strong><em>Figure 1:</em></strong><em> The queen at position d3 can move to any square marked with an asterisk.</em>

Thus, on the following board, none of the queens (denoted with the letter ‘Q’) can attack one another:

<strong><em>Figure 2:</em></strong><em> A 4×4 board in which none of the queens can attack one another.</em>

In contrast, on the following board, the queens at <em>c6</em> and <em>h6</em> can attack one another, as can the queens at <em>f4</em> and <em>h6</em>:

<strong><em>Figure 3:</em></strong><em> An 8×8 board in which some of the queens can attack one another.</em>

<h1>2.        Coordinate System</h1>

One standard notation for the location of a chess piece on an 8×8 board is to give its column, followed by its row, as a single string with no spaces. In this coordinate system, columns are labeled <em>a</em> through <em>h</em> (from left to right), and rows to be numbered 1 through 8 (from bottom to top).

So, for example, the board in Figure 2 (above, on pg. 2) has queens at positions <em>a3</em>, <em>b1</em>, <em>c4</em>, and <em>d2</em>.

Because you’re going to be dealing with much larger chess boards in this program, you’ll need some sort of notation that allows you to deal with boards that have more than the 26 columns we can denote with the letters <em>a</em> through <em>z</em>. Here’s how that will work:

Columns will be labeled <em>a</em> through<em> z</em> (from left to right). After column <em>z</em>, the next 26 columns will be labeled <em>aa </em>through <em>az</em>. After column <em>az</em>, the next 26 columns will be labeled <em>ba</em> through <em>bz</em>, and so on. After column <em>zz</em>, the next 26 columns will be labeled <em>aaa</em> through <em>aaz</em>.

Essentially, the columns are given in a base 26 numbering scheme, where digits 1 through 26 are represented using <em>a</em> through <em>z</em>. However, this counting system is a bit jacked up since there’s no character to represent the value zero. (That’s part of the fun.)

All the letters in these strings will be lowercase, and all the strings are guaranteed to be valid representations of board positions. They will not contain spaces or any other unexpected characters.

<em>For example:</em>

<ol>

 <li>In the coordinate string <em>a1</em>, the <em>a</em> tells us the piece is in the first column (from the left), and the 1 tells us the piece is in the first row (from the bottom).</li>

 <li>Similarly, the string <em>z32</em> denotes a piece in the 26<sup>th</sup> column (from the left) and 32<sup>nd</sup> row (from the bottom).</li>

 <li>The string <em>aa19</em> represents a piece in the 27<sup>th</sup> column (from the left) and 19<sup>th</sup> row (from the bottom).</li>

 <li>The string <em>fancy58339</em> would represent a piece in the 2,768,999<sup>th</sup> column (from the left) and the 58,339<sup>th</sup> row (from the bottom). (However, as you’ll see below, 2,768,999 exceeds the maximum width of the chess boards you’ll be required to handle.)</li>

</ol>

Converting these strings to their corresponding numeric coordinates is one of a few key algorithmic / mathemagical challenges you face in this assignment. You might want to write a separate helper method that does that for you.

<h1>3.        Runtime Requirements</h1>

In order to pass all test cases, the worst-case runtime of your solution cannot exceed O(<em>m</em> + <em>n</em>), where <em>m</em> is both the length and width of the square chess board, and <em>n</em> is the number of coordinate strings to be processed. This figure assumes that the length of each coordinate string is bounded by some constant, which means you needn’t account for that length in your runtime analysis, provided that the entire length of each string is processed or examined only some small, constant number of times (e.g., once or twice).

Equivalently, you may conceive of all the string lengths as being less than or equal to <em>k</em>, in which case the worstcase runtime that your solution cannot exceed would be expressed as O(<em>m</em> + <em>nk</em>).

<strong><em>Note!</em></strong> O(<em>m</em> + <em>n</em>) is just another way of writing O(<sub>MAX</sub>{<em>m</em>, <em>n</em>}), meaning that your runtime can be linear with respect to <em>m</em> or <em>n</em> – whichever one happens to be the dominant term for any individual test case.

<h1>4.        Method and Class Requirements</h1>

Implement the following methods in a class named <em>SneakyQueens</em>. Please note that they are all <strong><em>public</em></strong> and <strong><em>static</em></strong>. You may implement helper methods as you see fit.

<strong>public static boolean </strong> allTheQueensAreSafe(ArrayList&lt;String&gt; coordinateStrings, int boardSize)

<strong>Description:</strong> Given an ArrayList of coordinate strings representing the locations of the queens on a <em>boardSize</em> × <em>boardSize</em> chess board, return true if none of the queens can attack one another. Otherwise, return false.

<strong>Parameter Restrictions:</strong> <em>boardSize</em> will be a positive integer, with <em>boardSize</em> ≤ 60,000, describing both the length and width of the square board. (So, if <em>boardSize</em> = 8, then we have an 8 × 8 board.) <em>coordinateStrings</em> will be non-null, and any strings within that ArrayList will follow the format described above for valid coordinates on a <em>boardSize</em> × <em>boardSize</em> board.

<strong>Output:</strong> This method should <strong><u>not</u></strong> print anything to the screen. Printing stray characters to the screen (including newline characters) is a leading cause of test case failure.

<strong>public static double</strong> difficultyRating()

Return a double indicating how difficult you found this assignment on a scale of 1.0 (ridiculously easy) through 5.0 (insanely difficult).

<strong>public static double</strong> hoursSpent()

Return an estimate (greater than zero) of the number of hours you spent on this assignment.

<h1>5.        Compiling and Testing SneakyQueens on Eustis (and the <em>test-all.sh</em> Script!)</h1>

Recall that your code must compile, run, and produce precisely the correct output on Eustis in order to receive full credit. Here’s how to make that happen:

<ol>

 <li>To compile your program with one of my test cases:</li>

</ol>

javac SneakyQueens.java TestCase01.java

<ol start="2">

 <li>To run this test case and redirect your output to a text file:</li>

</ol>

java TestCase01 &gt; myoutput01.txt

<ol start="3">

 <li>To compare your program’s output against the sample output file I’ve provided for this test case:</li>

</ol>

diff myoutput01.txt sample_output/TestCase01-output.txt

If the contents of <em>myoutput01.txt</em> and <em>TestCase01-output.txt</em> are exactly the same, <em>diff</em> won’t print anything to the screen. It will just look like this:

<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="9fecfafef1ece5dffaeaecebf6ec">[email protected]</a>:~$ diff myoutput01.txt sample_output/TestCase01-output.txt <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="b0c3d5d1dec3caf0d5c5c3c4d9c3">[email protected]</a>:~$ _

Otherwise, if the files differ, <em>diff</em> will spit out some information about the lines that aren’t the same.

<ol start="4">

 <li>I’ve also included a script, <em>test-all.sh</em>, that will compile and run all six test cases for you. You can run it on Eustis by placing it in a directory with <em>java</em> and all the test case files and typing:</li>

</ol>

bash test-all.sh