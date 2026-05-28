---
title: research-output
description: use this for outputting research on new and current projects
---

# Introduction
When you have completed your research, use this skill to construct your output in to a knowledge graph that consists of organised markdown files

## Decision tree on new or existing project
1. Check memory for any context about the research project
2. List files in `workspace/agent/research/`
3. If `<project>-INDEX.md` exists → treat as existing project, proceed to **Articles**
4. If no matching index file exists → treat as new project, proceed to **New project**
5. If still ambiguous → ask the user before proceeding

## For new projects
1. Confirm with user what the project name for the research should be
2. Create a new subdirectory: `workspace/agent/research/<project>/`
3. You need to create a new file in your `workspace/agent/research` directory
4. `<project>-INDEX.md` - this page is where you list every file you create for this project
5. Every file in the project must be listed as a bullet point
6. Everytime you update the file with new research you must place `NEW:` at the beginning of the bullet point
7. Everytime you update the file and have updated a file you must place `UPDATED:` at the beginning of the bullet point
8. Group files together using high level themes

```<project>-INDEX.md template
---
slug: <project>-index
type: index
description: An index of all the research done for <project>
last updated: <YYYY-MM-DD>
tags: [<tag1>, <tag2>]
---

## <Theme>
- NEW: [[research/<project>/<article>]] - <140 character max description>
- [[research/<project>/<article>]] - <140 character max description>

## <Theme>
- [[research/<project>/<article>]] - <140 character max description>
- UPDATED: [[research/<project>/<article>]] - <140 character max description>
- [[research/<project>/<article>]] - <140 character max description>

```

## Articles
Every project should have its own directory where research files go to at `workspace/agent/research/<project>/` 

- Check `<project>-INDEX.md` to see what information has already been covered in order to avoid duplication
- IF the topic is already covered in an existing file then edit it to include the new information
- IF the topic is not already covered then create a markdown file per topic that is covered by your research
- Give each file a user friendly title and in the front matter, set a kebab title as `slug:`
- Break up content using `## Header`
- Any additional metadata specific to the article should go into the article using the format: `[<metadata>: <content>]`
  - Eg [url: https://theverge.com]
- Use other markdown functions when needed such as tables and code fences - this will make the content more presentable
- Always include the sources used to gather information in the file at the bottom of the page and bullet pointed
- Try to keep files within 1,000 words and split them up into more granular files if it goes far beyond the word count

```<article>.md template
---
slug: <article-id>
type: article
description: <280 max character description of the file contents>
last updated: <YYYY-MM-DD>
related:
 - "[[<research/<project>/<article>]]"
 - "[[<research/<project>/<article>]]"
aliases: [<alias 1>, <alias 2>]
tags: [<tag 1, tag 2>]
---

# <Title>
<high level summation of the facts of the article>
<additional metadata>

## <Sub-heading 1>
<content>

## <Sub-heading 2>
<content>

---

# Sources
- <Source url>
- <Source url>

```

## Project hygiene
1. Update `<project>-INDEX.md` with the newly created markdown files for that project. Remove `NEW:` and `UPDATED:` prefixes from any index entry that was not created or modified in this session.
2. If an existing file covers the same theme or cites the same sources, link to it, either via the `related:` property in the frontmatter or inline under a thematically similar sub-heading
