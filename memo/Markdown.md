# Markdown

Markdown is a text-to-HTML conversion tool for web writers. Markdown allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML).

Documentation: [Markdown Docs](https://daringfireball.net/projects/markdown/)
RFC: [RFC 7763](https://www.rfc-editor.org/rfc/rfc7763)

GitHub Documentation: [Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
GitHub Documentation: [Writing Markdown on GitHub](https://docs.github.com/en/get-started/writing-on-github)


---
## Cheat-Sheet

### Headings
```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

Here is a heading: `# Heading`, **don't do this:** `#Heading` 

### Emphasis
```markdown
Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~
```

### Line Breaks
```markdown
First line with two spaces after.  
And the next line.
```

### Lists

#### Ordered Lists
```markdown
1. First item
2. Second item
3. Third item
```

#### Unordered Lists
```markdown
- First item
- Second item
- Third item
```   

#### Definition Lists
```markdown
This is a definition list
: definition 1
: definition 2
```

### Icons
Complete list of github markdown emoji markup: [lista](https://gist.github.com/rxaviers/7360908)

### Links
```markdown
Link with text: [link-text](https://www.google.com)
```

### Images
```markdown
Image with alt text: ![alt-text](https://camo.githubusercontent.com/4d89cd791580bfb19080f8b0844ba7e1235aa4becc3f43dfd708a769e257d8de/68747470733a2f2f636e642d70726f642d312e73332e75732d776573742d3030342e6261636b626c617a6562322e636f6d2f6e65772d62616e6e6572342d7363616c65642d666f722d6769746875622e6a7067)

Image without alt text: ![](https://camo.githubusercontent.com/4d89cd791580bfb19080f8b0844ba7e1235aa4becc3f43dfd708a769e257d8de/68747470733a2f2f636e642d70726f642d312e73332e75732d776573742d3030342e6261636b626c617a6562322e636f6d2f6e65772d62616e6e6572342d7363616c65642d666f722d6769746875622e6a7067)
```

### Code Blocks

#### Inline Code Block
```markdown
Inline `code` has `back-ticks around` it.
```

#### Blocks of Code
<pre>
```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```
 
```python
s = "Python syntax highlighting"
print s
```
 
```
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```
</pre>

### Tables

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the raw Markdown line up prettily.

```markdown
| Heading 1 | Heading 2 | Heading 3 |
|---|---|---|
| col1 | col2 | col3 |
| col1 | col2 | col3 |
```

### Task list

To create a task list start line with square brackets with an empty space.
Ex: [<>] and add text for task.
To check the task replace the space between the bracket with "x".  

```markdown
[x] Write the post
[ ] Update the website
[ ] Contact the user
```

## Reference

Link: [markdown guide](https://www.markdownguide.org/cheat-sheet)
Link: [online markdown editor](https://dillinger.io/)
Link: [ascii diagrams](https://asciiflow.com/#/) or [this one](https://textik.com/#c3c7fe723e321e4b)
Link: [ASCII art](https://safeimagekit.com/text-to-ascii)

### How to put ASCII art into Markdown
Using [page asciiflow.com](asciiflow.com/#) you can download your project.
If you export drawing you should choose:
ASCII standard:
- ASCII basic
- ASCII extended
Types of signs at the beginning of line or project. For MD files choose:
- backticks multiline
- four spaces
### Examples

backticks:
```
    Obsidian                                                                     
                                                                                 
 ┌───┐    ┌───┐                                                                  
 │   ├────┤   │                                                                  
 └─┬─┘    └─┬─┘         _____  ___    _                           _         _    
   │        │          (  _  )(  _`\ (_)                         ( )       (_ )  
┌──▼────────▼───┐      | ( ) || (_(_)| |     ___ ___     _      _| |   __   | |  
│               │      | | | |`\__ \ | |   /' _ ` _ `\ /'_`\  /'_` | /'__`\ | |  
│   Example 1   │      | (_) |( )_) || |   | ( ) ( ) |( (_) )( (_| |(  ___/ | |  
└───────────────┘      (_____)`\____)(_)   (_) (_) (_)`\___/'`\__,_)`\____)(___) 
                                                                                 
                                                                                 
```

fourspaces:
        Obsidian                                                                     
                                                                                     
     ┌───┐    ┌───┐                                                                  
     │   ├────┤   │                                                                  
     └─┬─┘    └─┬─┘         _____  ___    _                           _         _    
       │        │          (  _  )(  _`\ (_)                         ( )       (_ )  
    ┌──▼────────▼───┐      | ( ) || (_(_)| |     ___ ___     _      _| |   __   | |  
    │               │      | | | |`\__ \ | |   /' _ ` _ `\ /'_`\  /'_` | /'__`\ | |  
    │   Example 1   │      | (_) |( )_) || |   | ( ) ( ) |( (_) )( (_| |(  ___/ | |  
    └───────────────┘      (_____)`\____)(_)   (_) (_) (_)`\___/'`\__,_)`\____)(___) 
                                                                                     
                                                                                     