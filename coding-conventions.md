1. We use [Allman style](https://en.wikipedia.org/wiki/Indentation_style#Allman_style) braces, where each brace begins on a new line, indented to the same level as the control statement. Statements within the braces are indented to the next level. (Never use single-line form)
2. We use four spaces of indentation (no tabs).
3. We use `_camelCase` for internal and private fields and use readonly. Prefix internal and private instance fields with _, static fields with s_ and thread static fields with t\_. When used on static fields, readonly should come after static (e.g. static readonly not readonly static). Public fields should be used sparingly and should use PascalCasing with no prefix used.
4. We avoid this. unless absolutely necessary. (WHY: [Code Inspection: Add/remove 'this.' qualifier](https://www.jetbrains.com/help/resharper/ArrangeThisQualifier.html))
5. We alwaysspecify the visibility, even if it's the default (e.g. private string \_foo not string \_foo). Visibility should be the first modifier (e.g. public abstract not abstract public).
6. Namespace imports shoud be specified at the top of the file, outside of namespace declarations.
7. Avoid more than one empty line at any time.
8. Avoid spurious free spaces, For example avoid if (someVar ==0)..., where the dots mark the spurious free spaces.
9. We only use var when the type is explicitly named on the right-hand side, typically due to either new or and explicit cast, e.g. var stream = new FileStream(...) not var stream = OpenStandardInput().
10. We use language keywords instead of BCL types (e.g. int, string, float instead of Int32, String, Single, etc) for both types references as well as method calls (e.g. int.Parse instead of Int32.Parse).
11. We use PascalCasing to name all our contant fields.
12. We use PascalCasing for all method names, including local functions.
13. We use nameof(...) instead of "..." whenever possible and relevant.
14. Fields should be specified at the top within type declarations.
15. Test case naming convention: [Action]_[Should...]_[When...] (e.g. OrgSetup_ShouldReturn412_WhenUserIdHeaderIsMissing).
16. Use // Arrange, // Act, // Assert heading comments in tests.
17. Preferred the naming convention for API data contract: suffix the type name with Request or Response (e.g. CreateOrgRequest), avoid using Dot as a suffix.
18. Avoid using comments when the code can explain itself. When comment is necessary, make sure it is clear to other people (even after a long time), and insert one space between the comment delimiter (//) and the comment text (e.g. // comment) \

- Always try to explain yourself in code.
- Don't be redundant.
- Dont add obvious noise.
- Dont use closing brace comments.
- Dont' comment out code. Just remove.
- Use as explanation of intent.
- Use as clarification of code.
- Use as warning of consequences.

19. Add vertical openness between concepts (use single blank line to separate sectins of code).
20. Avoid switch statement whenever you can, unless it's a [switch expression](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression).
21. Use "Return Early patter" in functions/methods where possible. [Return Early Pattern](https://medium.com/swlh/return-early-pattern-3d18a41bba8)
22. Use Ternary Operator e.g. "bool ? dotX: doY logic". For basic one line IF statements.

References:

- Coding style from dotnet core runtime [runtime/coding-style.md at main . dotnet/runtime](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)
- Clean Code: A Handbook of Agile Software Craftsmanship (by Robert C. Martin) [Summary of 'Clean code' by Robert C. Martin](https://gist.github.com/wojteklu/73c6914cc446146b8b533c0988cf8d29)
