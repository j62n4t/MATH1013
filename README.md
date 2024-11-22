java c
MATH1013 COMPUTATIONAL MATHEMATICS, EXERCISES 8, 2024/25
Instructions 
• The template file xxyyzz 8.py and the mergesort code mergesort.py are available on Minerva.
• When you submit your work, submit only the completed template file, which will contain your code and any answers written as comments. Your program should generate all necessary graphs when it is run.
• Your submitted work should import only the functions which are included in the template file already (namely shuffle, perf counter, and the module pyplot). Do not use any other imported functions.
• Do not change the function names.
• Your file should take at most 10 seconds to complete running.
• Before submitting your work, you are advised restart the Python kernel on your computer, and then check that your script. runs without crashing.
• Upload your submission to Assessment 8 on Minerva by 9am Tuesday 26th Novem-ber.
This workshop counts as 20% towards your final grade.8.1. Sorting experiments. Testing.  In this workshop we will compare the performance of
different sorting algorithms. We will be sorting very long lists in this workshop, so be sure to print your tests only on short lists!
First we need to generate some shuffled lists to sort. The shuffle method from the random module is used to randomise a list. For example the code
from  random  import  shuffle
mylist  =  list(range(1, n+1)) random. shuffle(mylist)
will produce a randomly shuffled list of all the integers from 1 to n inclusive.
The following code provides away to generate list of different lengths (in this case of length 2i for different i) with the time it takes to sort each:
listlengths  =  []
sorttimelist  =  []
for  i  in  range(1,  5):
listlengths. append(2**i)
mylist  =  list(range(2**i)) shuffle(mylist)
# here  define  sorttime  (how  long  it  takes  to  sort  the  list) sorttimelist. append(sorttime)
To test how long a sorting algorithm takes to sort a large list of numbers we will import and use the perf   counter() function from the time module.  This function returns the number of
seconds since some reference time. For example, the code time   start  =  time. perf   counter()
selectionsort(mylist)
time end  =  time. perf   counter()
sorttime  =  time end  -  time   start
will store the time needed for selection sort to sort mylist.  You are only timing the sorting process – so be careful not to include the time to create the unsorted list in your timing!8.2. Labelling lines. Of course, whenever we plot a graph we should label the axes.  But also
when we have multiple sets of data on a single set of axes, the reader needs to be able to tell what is what. This is easily done using matplotlib’s labels and legends:
x,  data1,  data2  =  [0,1,2],  [1,2,3],  [1.5,  2.5,  4] plt. plot(x,  data1,  label= ✬First  Set  Of  Data ✬ )
plt. plot(x,  data2,  label= ✬Second  Set  Of  Data ✬ ) plt. legend(loc= ✬upper  left ✬ )
Assessed Coursework 2, Week 8 
Part A: Sorting 
The code in section 8.3 below (also available on Minerva) implements the merge sort algorithm, you may use this in your work.
(1) Use perf count and the other ideas from 8.1 above to generate a list of data, where the ith entry i代 写MATH1013 COMPUTATIONAL MATHEMATICS, EXERCISES 8, 2024/25Python
代做程序编程语言s the time tm(i) necessary for merge-sort to sort lists of randomly chosen elements of length 2ifor i = 1, . . . , 10.
(2) Plot tm(i) against 2i on a loglog plot. Briefly explain (as a comment) what the graph says about merge-sort’s speed, using big-O notation.
(3) Write a function insertionsort(somelist) that applies the insertion sort algorithm described in lectures to sort a list. (You should use the pop and insert commands as described in the lecture notes.)
(4) Use this to find the times tI (i) for lists of the same length as in (1). Add tI (i) to your graph (on the same axes as above), and write a comment on what this says about the speed of insertion sort, in big O notation.
(5) Write a function countingsort(mylist) which implements counting sort for lists of non-negative integers, using the algorithm described in lectures.
(6) How efficient is countingsort compared to the other algorithms you have investigated? Can you provide one example each of lists of non-negative integers where counting sort would be (a) very efficient (b) very inefficient? Write your answer as a comment.
8.3. Merge sort code. One implementation of merge sort is the following.
def  interleave(list1 , list2):
✬✬✬ this    interleaves   two   already   sorted   lists ✬✬✬ newlist  =   []
while  len(list1)+len(list2)>0:
if  len(list1)==0:
newlist . extend(list2) list2  =   []
elif  len(list2)==0:
newlist . extend(list1) list1  =   []
else:
if   list1[0]
newlist . append(list1 . pop(0)) else:
newlist . append(list2 . pop(0)) return   newlist
def  mergesort(mylist):if  len(mylist)<=1: return(mylist)
else:
midpoint  =  len(mylist)//2
firstpart  =  mylist[:midpoint]   secondpart  =  mylist[midpoint:]
sortedfirst  =  mergesort(firstpart)
sortedsecond  =  mergesort(secondpart)
full_list  =  interleave(sortedfirst , sortedsecond) return(full_list)
Part B: Shuffling 
(7) Write a function triple riffle(mylist) which takes as input a list (which for convenience we will always take with length a multiple of 3) and outputs the result of a 3-way riffle shuffle as described i the lecture notes. For example: an input of range(9) should output [6,3,0,7,4,1,8,5,2].
(8) Write a function triple riffle repeat(mylist,n) which takes as input a list (again with length a multiple of 3) and outputs the result of doing a 3-way riffle shuffle n times.
(9) Write a function period(m) which takes as input a number m (which we will always take as a multiple of 3) and outputs the smallest positive integer n so that triple riffle repeat(list(range(m)),n) == list(range(m)).
(10) Discuss, with evidence, the outputs of your function period for different values of m, writing your answer as a comment.
Non-assessed Work. This section is not for submission.
• Extend your analysis of sorting algorithms to include bubblesort, selectionsort,  and Timsort (Python’s inbuilt method). Add these to your plots and compare their speeds.
• Write a function multiway   shuffle(mylist,m) which takes a list (whose length is a multiple of m), splits it into m equal piles, and then riffles them together.  What can you say about the periods of these shuffles?





         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
