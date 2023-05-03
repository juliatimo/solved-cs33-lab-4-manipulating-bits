Download Link: https://assignmentchef.com/product/solved-cs33-lab-4-manipulating-bits
<br>
5/5 - (1 vote)




1 Introduction

The purpose of this assignment is to become more familiar with bit-level representations of integers. You’ll do this by solving a series of programming “puzzles.” Many of these puzzles are quite artificial, but you’ll find yourself thinking much more about bits in working your way through them.

2 Logistics

This is an individual project. All submission will be done electronically on CCLE.

3 Handout Instructions

The data lab assignment has been published on the CCLE class webpage. Download the datalab-handout.tar file from the assignment page.

Start by copying datalab-handout.tar to a (protected) directory on a Linux machine in which you plan to do your work. Then give the command

<pre>  unix&gt; tar xvf datalab-handout.tar.</pre>

This will cause a number of files to be unpacked in the directory. The only file you will be modifying and turning in is bits.c.

1

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

The bits.c file contains a skeleton for each of the 15 programming puzzles. Your assignment is to complete each function skeleton using only straightline code for the integer puzzles (i.e., no loops or con- ditionals) and a limited number of C arithmetic and logical operators. Specifically, you are only allowed to use the following eight operators:

! ̃ &amp; ˆ | + &lt;&lt; &gt;&gt;

A few of the functions further restrict this list. Also, you are not allowed to use any constants longer than 8 bits. See the comments in bits.c for detailed rules and a discussion of the desired coding style.

4 The Puzzles

This section describes the puzzles that you will be solving in bits.c. 4.1 Bit Manipulations

Table 1 describes a set of functions that manipulate and test sets of bits. The “Rating” field gives the difficulty rating (the number of points) for the puzzle, and the “Max ops” field gives the maximum number of operators you are allowed to use to implement each function. See the comments in bits.c for more details on the desired behavior of the functions. You may also refer to the test functions in tests.c. These are used as reference functions to express the correct behavior of your functions, although they don’t satisfy the coding rules for your functions.

Name

Description

Rating

Max Ops

<pre>bitAnd(x,y)getByte(x,n)logicalShift(x,n)rotateRight(x,n)conditional(x, y, z)bang(x)</pre>

<pre>bitParity(x)</pre>

Computex &amp; yusingonly|and ̃. Get byte n from x.Shift right logical.Rotate x to the right by n. Computex ? y : z.

Compute !n without using ! operator. Return 1 if x contains an odd number of 0’s.

1 2 3 3 3 4 4

8

6 20 25 16 12 20

Table 1: Bit-Level Manipulation Functions.

4.2 Two’s Complement Arithmetic

Table 2 describes a set of functions that make use of the two’s complement representation of integers. Again, refer to the comments in bits.c and the reference versions in tests.c for more information.

2

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

Name

Description

Rating

Max Ops

<pre>isTmax(x)fitsBits(x,n)divpwr2(x,n)negate(x)isPositive(x)isGreater(x,y)subOK(x,y)ilog2(x)</pre>

Return 1 if x is the maximum, tc number, else 0. Return 1 if x fit in n bits, else 0.Compute x/2n.Return -x.

Return1ifx &gt; 0,else0.Return1ifx &gt; y,else0.Return1ifcancomputex – ywithoutoverflow,else0. Compute ⌊log2(x)⌋.

1 2 2 2 3 3 3 4

<pre>10151558242090</pre>

5 Evaluation

Table 2: Arithmetic Functions

Your score will be computed out of a maximum of 75 points based on the following distribution:

40 Correctness points. 30 Performance points. 5 Style points.

Correctness points. The 15 puzzles you must solve have been given a difficulty rating between 1 and 4, such that their weighted sum totals to 40. We will evaluate your functions using the btest program, which is described in the next section. You will get full credit for a puzzle if it passes all of the tests performed by btest, and no credit otherwise.

Performance points. Our main concern at this point in the course is that you can get the right answer. However, we want to instill in you a sense of keeping things as short and simple as you can. Furthermore, some of the puzzles can be solved by brute force, but we want you to be more clever. Thus, for each function we’ve established a maximum number of operators that you are allowed to use for each function. This limit is very generous and is designed only to catch egregiously inefficient solutions. You will receive two points for each correct function that satisfies the operator limit.

Style points. Finally, we’ve reserved 5 points for a subjective evaluation of the style of your solutions and your commenting. Your solutions should be as clean and straightforward as possible. Your comments should be informative, but they need not be extensive.

Autograding your work

We have included some autograding tools in the handout directory — btest, dlc, and driver.pl — to help you check the correctness of your work.

• btest: This program checks the functional correctness of the functions in bits.c. To build and use it, type the following two commands:

3

6

<pre>    unix&gt; make    unix&gt; ./btest</pre>

Notice that you must rebuild btest each time you modify your bits.c file.You’ll find it helpful to work through the functions one at a time, testing each one as you go. You can

use the -f flag to instruct btest to test only a single function: unix&gt; ./btest -f bitAnd

You can feed it specific function arguments using the option flags -1, -2, and -3: unix&gt; ./btest -f bitAnd -1 7 -2 0xf

Check the file README for documentation on running the btest program.• dlc: This is a modified version of an ANSI C compiler from the MIT CILK group that you can use

to check for compliance with the coding rules for each puzzle. The typical usage is:

<pre>    unix&gt; ./dlc bits.c</pre>

The program runs silently unless it detects a problem, such as an illegal operator, too many operators, or non-straightline code in the integer puzzles. Running with the -e switch:

unix&gt; ./dlc -e bits.ccauses dlc to print counts of the number of operators used by each function. Type ./dlc -help

for a list of command line options.

• driver.pl: This is a driver program that uses btest and dlc to compute the correctness and performance points for your solution. It takes no arguments:

unix&gt; ./driver.plWe will use driver.pl to evaluate your solution.

Handin Instructions

You will only submit the bits.c file using the CCLE Data Lab assignment submission before Thurs- day, 9th July, 11:59 PM. Do not use any other file name or file extension for submission. Also, late submissions will not be accepted.

4

6.1 You coulda had a bad bits.c, non-submittal Before submission, make sure:

<ul>

 <li>that bits.c compiles, passes the dlc test, and passes the btest tests on the class machines. Specifically, we will be testing bits.c on lnxsrv02.seas.ucla.edu;</li>

 <li>that you have included your identifying information (i.e., name and UCLA ID) in bits.c;</li>

 <li>and that you have removed all extraneous print statements.7 AdviceYou are welcome to develop your solution using any system or compiler you choose. However, make surethat the version you turn in can compile and run correctly on our class machine (lnxsrv02.seas.ucla.edu). If it does not compile, we will not grade it.Do keep the following in mind when working with dlc.

  <ul>

   <li>Don’t include the &lt;stdio.h&gt; header file in your bits.c file, as it confuses dlc and results in some non-intuitive error messages. You will still be able to use printf in your bits.c file for debugging without including the &lt;stdio.h&gt; header, although gcc will print a warning that you can ignore.</li>

   <li>ThedlcprogramenforcesastricterformofCdeclarationsthanisthecaseforC++orthatisenforced by gcc. In particular, any declaration must appear in a block (what you enclose in curly braces) before any statement that is not a declaration. For example, it will complain about the following code:<pre>      int foo(int x)      {</pre><pre>        int a = x;        a *= 3;     /* Statement that is not a declaration */        int b = a;  /* ERROR: Declaration not allowed here */</pre>}If you find yourself confused or stuck, you may consult the TAs and/or Professor Ghaforyfard in office hours. Piazza is also a fine resource.Best of luck.</li>

  </ul></li>

</ul>