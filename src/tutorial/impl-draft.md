# First implementation of _grrs_

After the last chapter on command line arguments,
we have our input data,
and we can start to write our actual tool.
Our `main` function only contains this line right now:

```rust,ignore
{{#include impl-draft.rs:13:13}}
```

We can drop the `println` statement that we put there temporarily
to demonstrate that our program works as expected.

Let’s start by opening the file we got.

```rust,ignore
{{#include impl-draft.rs:14:14}}
```

<aside>

**Note:**
See that [`.expect`] method here?
This is a shortcut function that will make the program exit immediately
when the value (in this case, the input file)
could not be read.
It's not very pretty,
and in the next chapter on [Nicer error reporting],
we will look at how to improve this.

[`.expect`]: https://doc.rust-lang.org/1.39.0/std/result/enum.Result.html#method.expect
[Nicer error reporting]:./errors.html

</aside>

Now, let’s iterate over the lines
and print each one that contains our pattern:

```rust,ignore
{{#include impl-draft.rs:16:20}}
```

## Wrapping up

Your code should now look like:

```rust,ignore
{{#include impl-draft.rs}}
```

Give it a try: `cargo run -- main src/main.rs` should work now!

<aside class="exercise">

**Exercise for the reader:**
This is not the best implementation as
it will read the whole file into memory, no matter how large the file may be.
Find a way to optimize it!
(One idea might be to use a [`BufReader`]
instead of `read_to_string()`.)

[`BufReader`]: https://doc.rust-lang.org/1.39.0/std/io/struct.BufReader.html

</aside>
