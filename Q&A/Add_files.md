---
title: Add pages to Nanhu Documentation
parent: Q&A
nav_order: 1
---

1. Choose the folder in which the new page belongs.
2. Create a Markdown file (`.md`) in that folder. Use the next available `nav_order` number to position it after the existing pages. For example, if the highest value is `5`, use `6`.
3. Add YAML front matter at the top of the file:

   ```yaml
   ---
   title: Your page title
   parent: Folder page title
   nav_order: 6
   ---
   ```

   The `parent` value must exactly match the `title` in the folder's `README.md`.

4. Write the page content below the front matter using Markdown. See the [Markdown Guide](https://www.markdownguide.org/basic-syntax/) for syntax examples.
5. Preview the page and check its links before submitting your change.
