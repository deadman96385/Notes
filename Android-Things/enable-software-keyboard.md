You will need to install a keyboard that does not rely on Google Play Services so something like [OpenKeyboard](https://github.com/openboard-team/openboard) will work

Then you will need to get the package name and class with this command:

```adb shell ime list -s```

You will get an output like this:

```org.dslul.openboard.inputmethod.latin/.LatinIME```

Then you will enable it to be used

```adb shell ime enable org.dslul.openboard.inputmethod.latin/.LatinIME```


## Reference Docs for the ime command:

usage: 
```
ime list [-a] [-s]
       
ime enable ID
       
ime disable ID
       
ime set ID
```

The list command prints all enabled input methods.

Use the -a option to see all details about each installed input methods.

Use the -s option to see only a single summary line for each installed input method.

The enable command allows the given input method ID to be used.

The disable command disallows the given input method ID from use.

The set command switches the current input method to whichever ID you specified.
