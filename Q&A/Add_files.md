---
sort: 1
title: Add pages to Nanhu Documentation
---

1. Choose the folder in which the new page belongs.
2. Create a Markdown file (`.md`) in that folder. Use the next available `sort` number to position it after the existing pages. For example, if the highest value is `5`, use `6`.
3. Add YAML front matter at the top of the file:

   ```yaml
   ---
   sort: 6
   title: Your page title
   ---
   ```

4. Write the page content below the front matter using Markdown. See the [Markdown Guide](https://www.markdownguide.org/basic-syntax/) for syntax examples.
5. Preview the page and check its links before submitting your change.
