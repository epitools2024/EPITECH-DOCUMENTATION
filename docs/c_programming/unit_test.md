Unit tests are tests that allow you to check the correctness and efficiency of your functions.

To start with we need the librairy criterion.

Criterion is a unit-testing tool that will allow you to test your code efficiently. Criterion lets you create a set of tests that will be executed on your code.

**Install Criterion**

```bash
$ sudo dnf install criterion
```
If you want your tests to work, you must compile your code with Criterion’s library using the -lcriterion flag.

To see the coverage you need to install ```gcovr```
```bash
$ sudo dnf install gcovr
```

**Basic of Unit testing**

***Assert***

Asserts are Criterion’s way of defining tests to run and all asserts are located in the header ```<criterion/criterion.h>```.

***Basic asserts***

The asserts below allows to test a function while returning a sentence if the ```condition``` is not verified.

```bash
Test(suite_name, test_name) {
    int i = 2;
    cr_assert(i * 2 == 4, "The result was %d. Expected %d", i * 2, 4);
}
```
In this example if the condition ```i * 2 == j``` is not verified the message is displayed.

Very important at EPITECH

**Makefile rule for Unit Test**

```bash
$ gcc -o binary_name file.c tests/test_project.c -- coverage -lcriterion
```

```bash
$ gcovr --exclude tests
```

```bash
$ gcovr --exclude tests --branches
```

NB: The command to execute the test units must be
```bash
$ make tests_run
```

[Criterion doc epitech](https://epitech-2022-technical-documentation.readthedocs.io/en/latest/criterion.html)