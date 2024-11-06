Project No. 1 : Similarity checking from Books.

Object        : To write a C++ program to identify 10 similar pairs of text books int txt format.

References    : Class notes , Professor lectures.
              : https://cplusplus.com/ , https://stackoverflow.com/ , www.geeksforgeeks.org/

Requirement   : Libraries ==

              : Standard C++ libraries      = <cstring>, <string>, <iostream>, <fstream> <iomanip>
              : Standard template libraries = <vector>, <map>, <algorithm>
              : boost                       = <filesystem>

              : Data-Set                    = Book-Txt

Theory        :  A simple (but crude) way to measures similarity is given as following:
                
                Step 1 : Identify top 100 frequent (normalize) occurring words in a text file. Consider only
                 numeric character and alphabet character (by converting both small and capital
                 alphabets to capital form) of the text file. Normalize the word count of a file by
                 dividing total number of words in the file.

                Step 2 : "remove commonly occurring six specific words" “a”, “and”, “an” , “of” “in” and
                   “the” from the file at the time of counting frequent word, total number of word
                   and the normalize frequency.

                Step 3 : "Similarity index" of two files can be calculated as sum of normalize value of all the
                  frequent words occurred in both the files.

                Step 4 : "Create a 64x64 size similarity matrix", exclude the self similarity.

               
                "Report top ten similar pairs of text books using the similarity matrix". 

               
Procedure    :  

          (i): writing a class ParentFile with filenumber, fileName, filePath, words, counts, totalWords and normalizeWords
                    variables , their data types are int, string, vector<string>, vector<int>, float, vector<float> respectively.
             
         (ii): writing three temporary variables word_i, unsorted_map, sorted_word_and_count.
             
        (iii): writing class constructor and destructor.
             
         (iv): writing 5 common functions for all text Book Files
             
           a): For Receiving : Required information(File : number , name and path) and Assigning.
               void fileDetails_input(int i, vector<string> Names, vector<string> Paths);
             :

           b): For step 1 : Reading File : Alphabet or Numeric characters and storing as capital letters Word in vector word_i.
             : void requireWords();

           c): For Step 2 : Removing Commonly occurring words.
             : void RemovingCommon();

           d): For Storing , words ,counts and calculated normal frequency and Top occurring words wise sorting.
             :void storingInClass();
             
           e): For Manually clearing data calling when class object is not in use.
             :void clear()

           v): Step 4 : in main function writing two loops outer loop initialize as i, and inner loop initialize as j
             : this creating Similarity Matrix(square matrix 64x64) with a condition (i<j) this excludes 
             : self similarity.

          vi): Step 3 : in this loop creating two files one in outer loop(i) file_i and one inside loop(j) file_j
             : and in condition calling function
             : SimilarityIndex()
             : this function compares Top 100 frequent word of both passed files and calculating sum of 
             : their normalize frequency and stores in similarity_matrix variable.

         vii): Deleting created class ParentFile Objects(File_i and File_j) accordingly.

             
Advantages   :
           i): class    :  having class for same objects reduces code writing.
          ii): comments :  Comments make code understandable
         iii): pointer  :  SimilatityIndex function will run for 2080 time in 64*64 matrix(exluding self similarity)
                           this function is having pointer of  3 vectors (words , count and normal frequency)
                           insted of real copy vectors. 
             
Disadvantages:
           i): time complixicity : O(n)
             : in this code map is used to track words reoccurence(counting)
             : every file is having minimum 40,000 words , and similarityMarix
             : calling files_i and file_j 2080 times 
             : This map has to process 40000 * 2000 = 8,00,00,000 words
             : this makes execution time around 5 minutes to 8 minutes.

Uses         :
           i): This file is used to identyfy similar par of books
          ii): This code can be use by any individual to find similar pair of books
              
Result       : Top 10 similar pair of books , from given set of 64 text books in txt format
             : has been identified and reported.



Top Ten Similar Pair Of Text Books Are :

1  Book no. 7   Gerard's Herbal Vol. 3.txt              and Book no. 10  Gerards Herbal Vol.4.txt                Similarity value is : 0.295295
2  Book no. 9   Gerards Herbal Vol. 2.txt               and Book no. 10  Gerards Herbal Vol.4.txt                Similarity value is : 0.295048
3  Book no. 7   Gerard's Herbal Vol. 3.txt              and Book no. 9   Gerards Herbal Vol. 2.txt               Similarity value is : 0.284192
4  Book no. 7   Gerard's Herbal Vol. 3.txt              and Book no. 8   Gerards Herbal Vol. 1.txt               Similarity value is : 0.25933
5  Book no. 8   Gerards Herbal Vol. 1.txt               and Book no. 9   Gerards Herbal Vol. 2.txt               Similarity value is : 0.249405
6  Book no. 8   Gerards Herbal Vol. 1.txt               and Book no. 10  Gerards Herbal Vol.4.txt                Similarity value is : 0.244104
7  Book no. 5   Foxes Book of Martyrs Part 5.txt        and Book no. 6   Foxes Book of Martyrs Part 6.txt        Similarity value is : 0.219208
8  Book no. 4   Foxes Book of Martyrs Part 4.txt        and Book no. 6   Foxes Book of Martyrs Part 6.txt        Similarity value is : 0.190478
9  Book no. 2   Foxes Book of Martyrs Part 2.txt        and Book no. 3   Foxes Book of Martyrs Part 3.txt        Similarity value is : 0.188408
10 Book no. 4   Foxes Book of Martyrs Part 4.txt        and Book no. 5   Foxes Book of Martyrs Part 5.txt        Similarity value is : 0.187483    






References : Links

vector erase() and clear() in C++
https://www.geeksforgeeks.org/vector-erase-and-clear-in-cpp/

map sort by value
https://www.geeksforgeeks.org/sorting-a-map-by-value-in-c-stl/

How to delete an instance of a class
https://cplusplus.com/forum/beginner/107822/

How to Sort Data Triplet in a Vector in C++(similarity matrix)
https://stackoverflow.com/questions/65717961/how-to-sort-a-vector-with-given-column-only-on-a-triplet-value

How to Store Data Triplet in a Vector in C++(similarity matrix)
https://www.geeksforgeeks.org/store-data-triplet-vector-c
          