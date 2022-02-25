[Link to my MarkdownParse](https://github.com/Jimmycho319/markdown-parse)

[Link to the MarkdownParse we reviewed](https://github.com/atruong39/markdown-parse)


The expected output for the first snippet is should include the links:
`['google.com, google.com, ucsd.edu]`

The expected output for the second snippet is:
`[a.com, a.com(()), example.com]`

The expected output for the third snippet is: 
`[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]`

These were found by clicking all of the working links in the preview section of VScode

We used these expected outputs for our code and this is what our tester looked like for JUnit:

![](https://user-images.githubusercontent.com/97693001/155673934-1a88aca4-a064-4ac5-9744-8b91eadd0de7.png)


For the tests of the 3 snippets on our file, none of them passed:
![](https://user-images.githubusercontent.com/97693001/155673990-a0a834b4-8461-4677-a55b-55a3c6d50fe9.png)


For the tests of the 3 snippets on their file, none of them passed:
![](https://user-images.githubusercontent.com/97693001/155674061-12a489a4-6d22-4a56-82ec-1adb57b104cb.png)


1. I think the first code will be an easy fix to account for all of the back ticks. This is something that is special with md parse and backticks so we just need to account for them by adding a couple of if statements for the backticks. I can also notice that the backticks are ignored when they are in the brackets so I think we can do away with just a couple if statements to account for the backticks.

2. I think that this second one with nested brackets will be a little more nontrivial than the first and will take more than just 10 lines of code to account for them. I think this way since we need to keep track of all of the open bracket and the open parenthesis and be able to compare them to see where the links actually are. This would be even more difficult with more consecutive open brackets.

3. Even though technically this is the longest snippet out of all of them I think this could be fixed in less than 10 lines of code. I think that if we add a part that resets the open bracket to the start of the next instance of an open bracket, we can account for the links as the preview is doing in `mdparse`.
