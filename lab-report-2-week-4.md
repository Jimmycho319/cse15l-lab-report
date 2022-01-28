Lab 2 Week 4

First Code Change:

Image of the first code change diff from Github

![](https://user-images.githubusercontent.com/97693001/151485440-5cf871ee-8b1e-4c48-b3fe-9ea9b241c037.png)

[Link to the first test file](https://github.com/Jimmycho319/markdown-parse/blob/main/test2.md)

Image of the first symptom of the failing-inducing input

![](https://user-images.githubusercontent.com/97693001/151485599-8fa0c1cd-8b13-40cd-9869-7a59865b08a4.png)

The bug in original MarkdownParse is caused by a removal of the close parenthesis after the first link. The symptom of this bug was that it printed everything until the next instance of the close parenthesis which was at the end of the second link which also included the open and close brackets of the second link which was not supposed to be printed. I fixed this by resetting the value of the close parenthesis to be the index of the next open bracket if it returned a value of -1



Second Code Change:

Image of the second code change diff from Github

![](https://user-images.githubusercontent.com/97693001/151487494-29a0e9a1-2e61-47f7-8dca-0b0bb25b5278.png)

[Link to the second test file](https://github.com/Jimmycho319/markdown-parse/blob/main/test3.md)

Image of the second symptom of the failing-inducing input

![](https://user-images.githubusercontent.com/97693001/151489590-93d3b574-7fea-4d01-8747-cdf8fbbd65dc.png)

The bug in the unedited MarkdownParse is caused by the removal of the close parenthesis after the second link. The symptom of this failure inducing input is that I get an index error. I get this index error from running the MarkdownParse because, the index of the close parenthesis is returned as a -1 when trying to find the second close parenthesis because it cannot find a close parenthesis so when we are giving the indexes of the substring to add to the arraylist, we get an index error. We fixed this by setting the end of the substring to default to the end length of the file if the value of closeParen == -1.


Third Code Change:

Image of the third code change diff from Github

![](https://user-images.githubusercontent.com/97693001/151489463-10b3fa97-9899-4795-a320-7c69c1f009e3.png)

[Link to the third test file](https://github.com/Jimmycho319/markdown-parse/blob/main/test4.md)

Image of the third symptom of the failing-inducing input

![](https://user-images.githubusercontent.com/97693001/151489645-bec932f3-7d13-4ca9-9eb9-6e57ad7d944a.png)

The bug in the unedited MarkdownParse is caused by the removal of the second close bracket after the first link. The symptom of this failure inducing input is that I get an OutOfMemoryError since this is causing an infinite loop. The relationship between the failure inducing input and the bug is that the program will never reach the end of the file since the value of the index of "(" will always be the same since it will keep finding the same "(" since the starting index of the indexOf is set to -1 since it is not able to find the second "(" which will cause the program to copy the same substring again and again. Since this causes an infinite loop, we get the OutOfMemoryError. I fixed this by adding an if statement which will set the start of the indexOf for the open parenthesis to the index of the "!" instead of the index of the "]" if it returned a value of -1.
