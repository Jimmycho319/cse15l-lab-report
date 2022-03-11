To find the differences between the two files, I used vimdiff as was recommended by my TA. This allowed me to find not only the difference between the two files but also the whole text so that I could see which test was giving me different results

The different output inducing files that I chose were `521.md` and `530.md`.

For `521.md`, our implementation printed `[]` while the given implementation printed `[baz*]`
For `530.md`, our implementation printed `[]` while the given implementation printed `[moon.jpg]`

Inside `521.md` was the text: 
`[foo *bar](baz*)`
The correct output when ran in github was:
`[baz*]`
The implementation that we worked on was incorrect in this case. The bug that we ran into was that our code did not recognize `(baz*)` as a link and therefore gave us an empty list when getLink was run. To fix this, I think we could

Inside `530.md` was the text: 
```
[!moon](moon.jpg)][ref]

[ref]: /uri
```

The correct parse of the links should be `[moon.jpg, ref]`. Therefore, neither of the implementations were corret. The bug was that the second link was not counted as a link when it should have been. Looking at the professor's implementation, I think the only logical explanation for the bug was that there is a completely new way of writing a link on Markdown. This does not even have any parenthesis yet it still it is considered a link. I did some personal tests and came to the conclusion that it was the colon that made whatever come after it a link. To fix this bug, I would implement another if statement that considered the case where if there was something of the format: `[<some text>]: <some link>`, the "some text" portion would come out as a link.
[!moon](moon.jpg)][ref]

[ref]: /uri

*lkjdlfs* dfdf
