# sb_32-01-19_ExpressCalculatorExercise

## Assignment Details

Creation of an Express.js application to perform 3 statistical operation -- mean, median, and mode -- with an arbitrary set of numbers. Each statistic operation has to have its own route and numbers are passed in as comma separated numbers. Sample calls to each operation using 1, 3, 5, 7, 9, 11:
`mean?nums=1, 3, 5, 7, 9, 11`
`median?nums=1, 3, 5, 7, 9, 11`
`mode?nums=1, 3, 5, 7, 9, 11`

The application needs to handle invalid numbers, no numbers, invalid operation (that is, not `mean`, `median`, or `mode`).

When numbers are valid, the application should respond with the following json:
```
response: {
  operation: "statOperation",
  value: result
}
```
where `"statOperation"` is either `"mean"`, `"median"`, or `"mode"` and `result` is the result of the statistic operation. `result` is always a number for `mean` and `median` operation and possibly a string for `mode` when multiple numbers appear the same amount of times.

Unit tests are required for `"mean"`, `"median"`, and `"mode"` functions.


**Enhancements**

- Not sure if it counts as an 'enhancement' but code was functionalized as much as possible.


**Difficulties**

Testing. An improved version of app.js did have mean, mode, and median operations in their own functions. Iterations of code eventually resulted in one route call with operation as a parameter because the routes for all 3 operations were nearly identical code-wise and the differences were easily handled with variables.

After unsuccessful testing attempts with app.js, I started adding `module.exports = {}` to the bottom of app.js so the non-express, non app.x functions could easily get required for the test scripts . . . when I realized nope, this is backwards -- the non-express, non app.x functions simply should not be in app.js. Move them into another file and require the file. 

Oh, and then there are the annoyances of sort, and trying to figure out a decent way to test a string for a number. parseInt seemed to work, until in testing when I used '1o' as a test value. Testing also revealed that sort was a character based sort because the median value was incorrect when the numbers included numbers less than and greater than 10. So yeay testing!
