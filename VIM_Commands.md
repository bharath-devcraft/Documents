### **Vim editor commands**

```markdown
# Vim Editor Commands

## Basic Vim Commands

### Entering Vim
- **Open a file in Vim**:
  ```bash
  vim <file_name>
  ```
- **Open Vim in read-only mode**:
  ```bash
  vim -R <file_name>
  ```
- **Exit Vim**:
  - Save and exit:  
    ```bash
    :wq
    ```
  - Exit without saving:  
    ```bash
    :q!
    ```
  - Save the file without exiting:  
    ```bash
    :w
    ```
  - Exit Vim if no changes were made:  
    ```bash
    :q
    ```

## Navigating in Vim

### Move the Cursor
- **Move cursor up**:  
  ```bash
  k
  ```
- **Move cursor down**:  
  ```bash
  j
  ```
- **Move cursor left**:  
  ```bash
  h
  ```
- **Move cursor right**:  
  ```bash
  l
  ```
- **Move to the beginning of the current line**:  
  ```bash
  0
  ```
- **Move to the end of the current line**:  
  ```bash
  $
  ```
- **Move to the beginning of the file**:  
  ```bash
  gg
  ```
- **Move to the last line of the file**:  
  ```bash
  G
  ```

### Scrolling
- **Scroll one line up**:  
  ```bash
  Ctrl + u
  ```
- **Scroll one line down**:  
  ```bash
  Ctrl + d
  ```
- **Scroll one page up**:  
  ```bash
  Ctrl + b
  ```
- **Scroll one page down**:  
  ```bash
  Ctrl + f
  ```

### Searching
- **Search forward for a term**:  
  ```bash
  /<search_term>
  ```
- **Search backward for a term**:  
  ```bash
  ?<search_term>
  ```
- **Repeat the search forward**:  
  ```bash
  n
  ```
- **Repeat the search backward**:  
  ```bash
  N
  ```

## Editing Text in Vim

### Inserting Text
- **Enter insert mode at the cursor position**:  
  ```bash
  i
  ```
- **Enter insert mode before the current character**:  
  ```bash
  I
  ```
- **Enter insert mode at the end of the current line**:  
  ```bash
  a
  ```
- **Enter insert mode after the current character**:  
  ```bash
  A
  ```
- **Enter insert mode at the beginning of the next line**:  
  ```bash
  o
  ```

### Deleting Text
- **Delete the current character**:  
  ```bash
  x
  ```
- **Delete the previous character**:  
  ```bash
  X
  ```
- **Delete the current word**:  
  ```bash
  dw
  ```
- **Delete from the cursor to the end of the line**:  
  ```bash
  D
  ```
- **Delete the current line**:  
  ```bash
  dd
  ```

### Copying and Pasting Text
- **Copy (yank) the current line**:  
  ```bash
  yy
  ```
- **Copy the current word**:  
  ```bash
  yw
  ```
- **Copy from the cursor to the end of the line**:  
  ```bash
  y$
  ```
- **Paste the copied content**:  
  ```bash
  p
  ```

### Undo and Redo
- **Undo the last change**:  
  ```bash
  u
  ```
- **Redo the last undone change**:  
  ```bash
  Ctrl + r
  ```

## Advanced Navigation and Commands

### Moving by Words
- **Move to the next word**:  
  ```bash
  w
  ```
- **Move to the previous word**:  
  ```bash
  b
  ```
- **Move to the beginning of the current word**:  
  ```bash
  0
  ```
- **Move to the end of the current word**:  
  ```bash
  e
  ```

### Moving by Paragraphs
- **Move to the beginning of the next paragraph**:  
  ```bash
  }
  ```
- **Move to the beginning of the previous paragraph**:  
  ```bash
  {
  ```

### Indentation
- **Indent the current line**:  
  ```bash
  >>
  ```
- **Un-indent the current line**:  
  ```bash
  <<
  ```

### File Management
- **Save the file**:  
  ```bash
  :w
  ```
- **Save the file with a different name**:  
  ```bash
  :w <new_file_name>
  ```
- **Close the current file**:  
  ```bash
  :q
  ```

## Working with Multiple Files

### Open a new file in the same session
- **Open a new file**:  
  ```bash
  :e <file_name>
  ```

### Switch between open files
- **Switch to the next open file**:  
  ```bash
  :n
  ```
- **Switch to the previous open file**:  
  ```bash
  :N
  ```

### Split Screen
- **Split the window horizontally**:  
  ```bash
  :split
  ```
- **Split the window vertically**:  
  ```bash
  :vsplit
  ```
- **Switch between windows**:  
  ```bash
  Ctrl + w, w
  ```

### Navigate Between Windows
- **Switch to the top window**:  
  ```bash
  Ctrl + w, k
  ```
- **Switch to the bottom window**:  
  ```bash
  Ctrl + w, j
  ```

## Working with Regular Expressions
- **Search using a regular expression**:  
  ```bash
  /<regex>
  ```

## Exiting Vim
- **Save and exit (force)**:  
  ```bash
  :wq!
  ```

## Search and Replace in Vim
- **Search and replace** a term in the file:
  ```bash
  :s/name/change_name/g
  ```
  - `g` means replace globally (in the entire file).
---
