To find the differences between the two files, I used vimdiff as was recommended by my TA. This allowed me to find not only the difference between the two files but also the whole text so that I could see which test was giving me different results

The different output inducing files that I chose were `521.md` and `530.md`.

For `521.md`, our implementation printed `[]` while the given implementation printed `[baz*]`
For `530.md`, our implementation printed `[]` while the given implementation printed `[moon.jpg]`

Inside `521.md` was the text: 
`[foo *bar](baz*)`
The correct output

[foo *bar](baz*)

Inside `530.md` was the text: 
```
[!moon](moon.jpg)][ref]

[ref]: /uri
```
