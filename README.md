Download Link: https://assignmentchef.com/product/solved-cs204-homework-5-iterator-and-operator-overloading
<br>
<h2>Background</h2>

<strong>Trie</strong> is an efficient information storage/querying data structure commonly used to store words in a dictionary, document etc. As the name suggests, it is like a <strong>tree</strong>, which we have covered in the lectures. In fact, we only used binary trees, the most common ones one can encounter in Computer Science. However in practice, tree nodes can have an arbitrary number of children. In a <strong>Trie</strong>, all nodes will have the same number of children but unlike binary trees it is more than two. Every <strong>TrieNode</strong> in a <strong>Trie</strong> has 26 child nodes (one child for every character in the English alphabet). As new keys (words) are inserted into the <strong>Trie</strong>, the corresponding child node is generated. A sample <strong>Trie</strong> can be seen in the following image.




<h2>Introduction</h2>

You are given a Trie class, which has a private root of the Trie (TrieNode *root). Some of the overloaded operators (e.g. functions) will be part of the class itself, while the others will be free one, thus not as a member of the Trie class. You are also asked to complete the <strong>copy constructor</strong>, <strong>move constructor</strong> and <strong>destructor</strong> for Trie.




Every Trie node has a Boolean variable named isWord stating the end of a word in the Trie. Words start from the root and end at a node which has isWord set to <strong>True. </strong>In the following example trie you can see the words in the trie and the structure of it.







In addition to operators and constructors/destructors, you will implement an iterator class for the Trie. The files containing a significant code portion for that class (TrieIterator.h and TrieIterator.cpp) are given. In this homework, you only need to complete the necessary code for Trie and TrieIterator. For almost all missing parts, you will find a comment in these files.




In addition to these, you are given a helper Stack class (Stack.h and Stack.cpp). You won’t change anything in them. You are also given a tester file TrieDemo.cpp. This code also does not need any modifications. It is a sample tester file and while grading, we will use different tester files. Note that you are not required to read input files in this homework. The output of the main function in TrieDemo.cpp is given in the homework assignment.

<h2>Operators</h2>

The operators to be implemented are listed below in detail. In this part, please keep in mind that Trie functionalities (insertion and traversal [with Iterator]) are already handled fully – of course, do not forget the parts you have to complete.

<table width="614">

 <tbody>

  <tr>

   <td width="45"><strong>&lt;&lt; </strong></td>

   <td width="569">This operator (<strong>free function</strong>) takes an ostream object as the left operand, and an instance of Trie class as the right operand. It prints the trie’s content in sorted order by sending it to an output (ostream) stream.</td>

  </tr>

  <tr>

   <td width="45"><strong>==</strong></td>

   <td width="569">This operator (<strong>member function</strong>) takes an instance of trie as parameter. The operator should return true if and only if both the current trie <strong>(*this)</strong> and the parameter trie contain the same elements/words. (Hint: for a very simple implementation, use the same helper function you use for <strong>&lt;&lt;</strong><strong>)</strong></td>

  </tr>

  <tr>

   <td width="45"><strong>!=</strong></td>

   <td width="569">This operator (<strong>member function</strong>) is the exact opposite of <strong>== </strong>(Hint: just use the previous operator)</td>

  </tr>

  <tr>

   <td width="45"><strong>= </strong></td>

   <td width="569">This operator (<strong>member function</strong>) will assign (more accurately make replica-clone of) the right hand side trie to the left one. In order to allow multiple assignments (e.g. trie1 = trie2 = trie3), you should carefully pay attention to this operator.</td>

  </tr>

  <tr>

   <td width="45"><strong>+= </strong></td>

   <td width="569">This operator (<strong>member function</strong>) takes a trie as parameter and adds its nodes to the current trie instance. Note that this operation should alter the nodes of current trie.</td>

  </tr>

  <tr>

   <td width="45"><strong>+ </strong></td>

   <td width="569">This operator (<strong>member function</strong>) takes a trie instance as a parameter and combines the content within the current one and the one on the parameter inside a new trie instance. After the operation, content of the current trie object must not have been changed. instead, another instance of a trie should be returned.</td>

  </tr>

  <tr>

   <td width="45"><strong>+= </strong></td>

   <td width="569">This operator (<strong>member function</strong>) takes a string as parameter on the right hand side and inserts it to trie. Note that this operation should alter the nodes of current trie.</td>

  </tr>

  <tr>

   <td width="45"><strong>+ </strong></td>

   <td width="569">This operator takes a trie and a string <strong>(either as a left hand side operand or a right hand side!)</strong> and returns another instance where the string is added to the trie. (Note that you need more than one version of <strong>+</strong> operator. They differ in terms of function signatures. One must be implemented as a member function; the other must be a free function.)</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<h2>Output</h2>




Output of the <strong>TrieDemo.cpp</strong> is also given in the <strong>output.txt</strong> file.

Content of tr1: compute computer process program progress uni unido universe university







Creating tr2 with: tr2(tr1) Copy constructor called Content of tr1:

compute computer process program progress uni unido universe university  Content of tr2: compute computer process program progress uni unido universe university




Creating tr3 with: tr3 = tr1 Copy constructor called

Content of tr3: compute computer process program progress uni unido universe university  Content of tr4: computing header headphone saramago zapatista




Creating tr5 with: tr5(tr1 + tr4) Move constructor called

Content of tr5: compute computer computing header headphone process program progress saramago uni unido

universe university zapatista

Deleting the tr1

Content of tr1:

Trie is empty.




Iterator for tr5 is starting:

<ul>

 <li>compute</li>

 <li>computer</li>

 <li>computing</li>

 <li>header</li>

 <li>headphone</li>

 <li>process</li>

 <li>program</li>

 <li>progress</li>

 <li>saramago</li>

 <li>uni</li>

 <li>unido</li>

 <li>universe</li>

 <li>university</li>

 <li>zapatista tr2 += tr4 Content of tr2: compute computer computing header headphone process program progress saramago uni unido universe university zapatista  Content of tr5: compute computer computing header headphone process program progress saramago uni unido universe university zapatista</li>

</ul>

tr5 and tr2 are equal.  tr4 += “gloves” Content of tr4: computing gloves header headphone saramago zapatista   tr3 = tr3 + tr4 Move constructor called

Content of tr3: compute computer computing gloves header headphone process program progress saramago uni unido universe university zapatista  Content of tr5: compute computer computing header headphone process program progress saramago uni unido universe university zapatista  tr5 and tr3 are not equal.  tr4 = tr4 + “helmet” Move constructor called

Content of tr4: computing gloves header headphone helmet saramago zapatista

tr4 = “jacket” + tr4 Move constructor called

Content of tr4:

computing gloves header headphone helmet jacket saramago zapatista




Press any key to continue . . .




<h3>Some Important Rules</h3>

In order to get a full credit, your programs must be efficient and well presented, presence of any redundant computation or bad indentation, or missing, irrelevant comments are going to decrease your grades. You also have to use understandable identifier names, informative introduction and prompts. Modularity is also important; you have to use functions wherever needed and appropriate.




When we grade your homeworks we pay attention to these issues. Moreover, in order to observe the real performance of your codes, we are going to run your programs in <em>Release</em> mode and <strong>we may test your programs with very large test cases</strong>.




<strong> </strong>

<strong>What and where to submit (PLEASE READ, IMPORTANT) </strong>

You should prepare (or at least test) your program using MS Visual Studio 2012 C++. We will use the standard C++ compiler and libraries of the abovementioned platform while testing your homework. It’d be a good idea to write your name and last name in the program (as a comment line of course).




Submissions guidelines are below. Some parts of the grading process are automatic. Students are expected to strictly follow these guidelines in order to have a smooth grading process. If you do not follow these guidelines, depending on the severity of the problem created during the grading process, 5 or more penalty points are to be deducted from the grade. Name your cpp file that contains your program as follows:




<strong><em>“SUCourseUserName_YourLastname_YourName_HWnumber.cpp” </em></strong>




Your SUCourse user name is actually your SUNet username that is used for checking sabanciuniv e-mails. Do NOT use any spaces, non-ASCII and Turkish characters in the file name. For example, if your SUCourse user name is valent, name is Valentina, and last name is Tereşkova, then the file name must be:




<h3>Valent_Tereskova_Valentina_hw1.cpp</h3>




Do not add any other character or phrase to the file name. Make sure that this file is the latest version of your homework program. Compress this cpp file using WINZIP or WINRAR programs. Please use “zip” compression. “rar” or another compression mechanism is NOT allowed. Our homework processing system works only with zip files. Therefore, make sure that the resulting compressed file has a zip extension. Check that your compressed file opens up correctly and it contains your cpp file.




You will receive no credits if your compressed zip file does not expand or it does not contain the correct file. The naming convention of the zip file is the same as the cpp file (except the extension of the file of course). The name of the zip file should be as follows:




<strong><em>SUCourseUserName_YourLastname_YourName_HWnumber.zip </em></strong>




For example zubzipler_Zipleroglu_Zubeyir_hw1.zip is a valid name, but




<h3>hw1_hoz_HasanOz.zip, HasanOzHoz.zip</h3>




are <strong>NOT</strong> valid names.

<strong> </strong>

<strong>Submit via SUCourse ONLY!</strong> You will receive no credits if you submit by other means (email, paper, etc.).




Successful submission is one of the requirements of the homework. If, for some reason, you  cannot successfully submit your homework and we cannot grade it, your grade will be 0.

<strong> </strong>

Good Luck!

CS204 Team (M. Yusa Erguven, Kamer Kaya)

<strong> </strong>