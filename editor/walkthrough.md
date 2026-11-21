## Check a proposed dependency upgrade numerically

Returns [allowed upgrade, candidate versus installed, major/minor/patch index changed, within range]. Equal versions are allowed. This release handles numeric cores and explicit bounds. Invalid arguments and nonfinite results return an empty vector.

1. Open an empty file named `bowerbird-demo.blyx`.
2. Type `blyx-bowerbird-demo` and select **Bowerbird — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
1
1
1
1
```

[Work through the example in the browser](https://www.blyx-lang.space/play?example=package-bowerbird)
