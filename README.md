# database-system-assignment-4-2--query-compilation-and-optimization-solved
**TO GET THIS SOLUTION VISIT:** [Database-SysteM Assignment 4.2- Query Compilation and Optimization Solved](https://www.ankitcodinghub.com/product/database-system-assignment-4-2-query-compilation-and-optimization-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;110181&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;Database-SysteM  Assignment 4.2- Query Compilation and Optimization Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
The goal of this assignment is to compile and optimize an input SQL statement, and then print the resulting, optimized query plan to the screen. I have actually implemented a parser and lexer for the subset of SQL that you need to consider, which is available for download. The first thing that you need to do is to download and look over the parser and lexer. If you are confused about lex and yacc, you can look over Dr. Dobra’s slides at http://www.cise.ufl.edu/~adobra/lectures/lex_yacc.pdf. Or a simple Google search will prove very informative as well.

The Parser

The parser that I have implemented takes a simple SQL statement, processes it, and puts the result into a set of data structures (several linked lists as well as two integer yes/no flags). The linked lists and flags that are constructed by the parser are declared in the file parser.y:

// these data structures hold the result of the parsing struct FuncOperator *finalFunction; struct TableList *tables; struct AndList *boolean;

struct NameList *groupingAtts; struct NameList *attsToSelect; int distinctAtts; int distinctFunc;

In order to access these data structures externally from the parser, simply use an extern declaration in the file that you want to access them from.

Basically, what you’ll do in your main program is to parse the input stream via a call to yyparse(), and then when you want to do your compilation and optimization, you will access these data structures as needed. Look in parser.y to see exactly what each of the structures mean and the sort of data that they hold.

You should also look over the parser to see exactly what our version of SQL will look like. To try out a simple SQL statement, just compile the parser that I’ve supplied, and then run the resulting executable. Type in:

SELECT SUM DISTINCT (a.b + b), d.g

FROM a AS b

WHERE (‘foo’ &gt; this.that OR 2 = 3) AND (12 &gt; 5)

GROUP BY a.f, c.d, g.f

&lt;control-D&gt;

And the program will parse this statement and fill up the data structures!

What You Need To Do

Since the parser is already written, you probably won’t have to do much in terms of messing with parser.y (though undoubtedly there are things that I’ve done that you won’t like, and will want to change). But the core of this assignment is to implement the recursive routine for enumerating all possible query plans, and selecting the best one in terms of the plan that creates the smallest number of intermediate tuples. You will use your stats code from the first part of A4 to guess the size of the intermediate relations that your query plan will produce. For simplicity, just go ahead and initialize your statistics object with all of the statistics that you were provided in the first part of A4 (you might just want to put these into a text file in the format used by your A4.1 statistics object, and then when your main program fires up, you read them in in order to perform the optimization).

In the end, what your recursive optimization routine will produce is a query plan, which should be represented/implemented as a tree-based, C++ data structure. There should be seven different node types that can appear in the tree, with one node type being associated with each relational operation from A3. Each node should contain the output schema for records that are being piped out of the operation, as well as any other operation-specific information that will be needed to actually invoke or call the relational operation. For example, in the case of a relational projection node, you will need to store the last three parameters to the Project operation in the node. In the case of a relational join node, you will need to store the last two parameters to the Join operation in the node. You do not actually need to store any of the pipes that will be used in the nodes, since these are implied by the structure of the tree. That is, if a join node is the child of a project node, then this implies that there is a pipe from the corresponding Join operation into the corresponding Project operation. These pipes will actually be created when you execute the query plan, which is the goal of the next (last) assignment.

In order to facilitate grading and debussing of this assignment, once your optimization routine produces its final query plan, what your main program should do is to perform an in-order traversal of the plan to print it out to the screen. Each of the nodes should be printed to the screen in something resembling the following format:

********

Join Operation Input pipe ID 2 Input pipe ID 5 Output pipe ID 6 Output Schema: Att1: int Att2: int Att3: string Join CNF:

&lt;output from CNF.Print ()&gt; ********

Specifically, when a node is printed, its relevant pipes should be identified (associate a unique pipe ID with each pointer or link in the tree), the output schema should be printed, and the specific operation should be named (join, project, pipe select, etc.). Also, any important, operation-specific information needs to be printed to the screen. On an operation-by-operation basis, this is:

In the case of a select on a pipe: the corresponding CNF

In the case of a select on a file: the corresponding CNF

In the case of a project: the attributes to keep

In the case of a join: the corresponding CNF

In the case of a sum: the corresponding function

In the case of a group-by: the corresponding OrderMaker as well as the function

Follow the example in tc6Output.txt.

That’s it!

What To Turn In:

1. Turn in your submission via Canvas. Turn in your code, output42.txt, and your report in a zip file called firstNameLastName1_firstNameLastName2_p42.zip.

 Edit the Makefile to name your executable a42.out.

 Make sure your code runs with all files in directory a4-2test without any modifications.

 The output of your program should follow the example shown in tc6Output.txt when test case 6 is given as input.

Include the following:

a) All code needed to compile test.cc

b) Create 2 GTests for any of the methods you wrote or augmented in this assignment. Turn in your GTest code.

c) In a Bash shell run the test cases script with the following command:

./runTestCases42.sh

Submit the file output42.txt generated after running the test cases script. If you wrote your code in Rust or are running on a Windows machine, change the script as needed.

2. Your report as a PDF file that includes:

a) Group member names

b) Include instructions on how to compile and run your code as well as a brief explanation of each method you wrote and how it works.

c) A screen shot of output42.txt generated after running the script.

d) Screen shots of GTest results that match results generated by your code.

e) If you had a problem with the code or found a bug that you think would be useful for future classes to know about, list the bug you found and what you did to fix it.

Grading:

Graded out of 100 points.

+20 Gtests

+50 points for correct output for each query

+30 report
