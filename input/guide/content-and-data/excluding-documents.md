Order: 11
Badge: Web
---
Documents can be easily excluded from generation, either by removing them entirely or by suppressing their output (but still processing them in the appropriate pipeline).

To hide a document entirely, set the `Excluded` metadata value to `true`. By default, any file with a `Published` metadata value greater than the current date will be automatically excluded.

To prevent a document from outputting but still include it in pipelines and the generation, set the metadata value of `ShouldOutput` to `false`. This is helpful when you want the document to be available to other documents without itself being an output. For example if you use a set of Markdown files to define content that's only intended to be included within other outputs.

You can also exclude entire paths with the global `ExcludedPaths` setting. For example, this will entirely exclude the `exclude_me` folder and no files from that folder will be processed or copied to output:

```csharp
await Bootstrapper
    .Factory
    .CreateWeb(args)
    .AddSetting(
        WebKeys.ExcludedPaths,
        new List<NormalizedPath>
        {
            new NormalizedPath("exclude_me")
        })
    .RunAsync();
```