- Compile your project with:

```bash
$ gcc file.c
```

- You can compile multiple file with:

```bash
$ gcc file1.c file2.c
```

This method with create a default name for your binary `a.out`

- If you want a specific name, you can use:

```bash
$ gcc file.c -o your_binary_name
```

- Include a headers file directory

```bash
$ gcc file.c -I ./include
```

- Include a library directory

```bash
$ gcc file.c -L ./lib/my -l libmy
```

You can use some flags to prevent warning in your code

`Wall` `Werror` `Wextra`

Type `man gcc` to find more info about it