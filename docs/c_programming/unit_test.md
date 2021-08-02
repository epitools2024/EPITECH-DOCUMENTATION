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
./
The asserts below allows to test a function while returning a sentence if the ```condition``` is not verified.

```C
Test(suite_name, test_name) {
    int i = 2;
    cr_assert(i * 2 == 4, "The result was %d. Expected %d", i * 2, 4);
}
```
In this example if the condition ```i * 2 == j``` is not verified the message is displayed.

```bash
cr_assert(condition)
cr_assert_not(condition)
```

If you want to compare arrays, please refer to ```cr_assert_str_eq()``` or ```cr_assert_arr_eq()```.

***Redirections***

To use the following assertions, you must include ```<criterion/redirect.h>``` along with ```<criterion/criterion.h>```.

```bash
cr_assert_stdout_eq_str(Value)
```

These asserts allow to compare the content of stdout with Value

```bash
 cr_assert_stderr_eq_str(Value)
```

These asserts allow to compare the content of stderr with value.

Here is a sample usage of this assert.

```C
#include <criterion/criterion.h>
#include <criterion/redirect.h>

void redirect_all_stdout(void)
{
        cr_redirect_stdout();
        cr_redirect_stderr();
}

int error(void)
{
        write(2, "error", 5);
        return(0);
}

Test(errors, exit_code, .init=redirect_all_stdout)
{
        error();
        cr_assert_stderr_eq_str("error", "");
}
```
NB: You must include criterion.h and redirect.h in this order, otherwise your tests won’t work.

**Test options**

***.init***

This parameter takes a function pointer as an argument. Criterion will execute the function just before running the test. The function pointer should be of type  ```void(*)(void)```.

```C
void my_func(void)
{
        my_putstr("My test\n");
}

Test(suite_name, test_name, .init = my_func)
{
        //tests
}
```

***.fini***

This parameter takes a function pointer to a function that will be executed after the tests is finished.

It takes the same pointer type as the ```.init``` parameter, and also has the same usage.

***.exit_code***

If you want to test your error handling, you can use the .exit_code parameter so the test will be marked as passed if the given exit code is found.

```C
int error(void)
{
        write(2, "error", 5);
        exit(0);
}

Test(errors, exit_code, .exit_code = 84)
{
        error();
        cr_assert_stderr_eq("error", "");
}
```

***.signal***

If a test receives a signal, it will by default be marked as a failure. However, you can expect a test to pass if a special kind of signal is received.

***.disabled***

If it's true, the test will be skipped.

***.description***

This parameter must be used in order to give extra definition of the test’s purpose, which can be quite helpful if your suite_name and test_name aren’t as explicit as you would like.

***.timeout***

This parameter takes a double, representing a duration. If your test takes longer than this duration to run, the test will be marked as failed.

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