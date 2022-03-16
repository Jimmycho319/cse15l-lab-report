To find the differences between the two files, I used vimdiff as was recommended by my TA. This allowed me to find not only the difference between the two files but also the whole text so that I could see which test was giving me different results

The different output inducing files that I chose were `523.md` and `530.md`.

For `523.md`, our implementation printed `[]` while the given implementation printed `[baz]`
For `530.md`, our implementation printed `[]` while the given implementation printed `[moon.jpg]`

Inside `523.md` was the text: 
`[foo <bar att="](baz)">`
The correct output when ran in github was:
`[]` since there were no links present.

The implementation that the professor worked on was incorrect in this case. The symptom that we ran into was that the program recognized `baz` as a link in this case when it should not have. I ran some tests on the github with md file and found that this bug occurred because it did not recognize `="` as a format for a link name. I think we could fix this by making sure that nothing gets printed when there is an equals followed by an unfinished `="`. There seems to be some functionality within `md` that allows for the writer to set a link name equal to something. I personally couldn't find what this actually does and I think that this is a very niche case so I think that it is best fixed by adding another if statement that checks if there is an incomplete `="` within the link name portion that will not consider it a finished link if this is not resolved

This is an image of the non working code:
![](https://user-images.githubusercontent.com/97693001/158697896-524d9959-7f74-46f1-9903-60db83e1bbae.png)

To account for this special case, we can add another if statement after the first if statement inside of the while loop to check to see if there is an equals sign between the index of the open and close brackets and then write a continue for if it does contain a `=`.

Inside `530.md` was the text: 
```
[!moon](moon.jpg)][ref]

[ref]: /uri
```

The correct parse of the links should be `[moon.jpg, ref]`. Therefore, neither of the implementations were correct. The symptom was that the second link was not counted as a link when it should have been. Looking at the professor's implementation, I think the only logical explanation for the bug was that there is a completely new way of writing a link on Markdown that was not previously specified by putting the link and link name in the format: `[<some text>]: <some link>`. This does not even have any parenthesis yet it still it is considered a link. I did some personal tests and came to the conclusion that it was the colon that made whatever come after it a link. To fix this bug, I would implement another if statement that considered the case where if there was something of the format: `[<some text>]: <some link>`, the "some link" portion would come out as a link until the next endline.
This is an image of the non working code:
![](https://user-images.githubusercontent.com/97693001/158697345-6323b28f-4c47-44cd-beab-b2f252939ca0.png)

If we were to add another if statement right before the first if statement inside of the while loop that checked before proceeding if there was a open and close bracket and then a colon `:` right after that it would consider the next line of text as a link. 
