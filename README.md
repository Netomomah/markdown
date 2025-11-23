<!-- Headings-->
# Heading 1
## Heading 2
### Heading 3
#### Heaading 4
##### Heading 5
###### Heading 6

<!-- Italics -->
\*This text\* is italic

_This text_ is italic

__This text__ is italic

**This text**

<!-- StrikeThrough-->
~~This text~~ is strikethrough

<!-- Horizontal Rule -->

_ _ _
____

<!-- Blockquote -->
> This is a quote

<!-- Links -->
[Trasvery Media](http://www.traversymedia.com "Traversy Media")

<!--UL -->
* Item 1
* Item 2
* Item 3
     * Nested Item 1
     * Nested Item 2

<!-- OL -->
1. Item 1
1. Item 1
2. Item 2

 <!-- Inline COde Block -->
 '<p>This is paragraph</p>'

 <!--Images-->
  ![Markdown Logo]
  (https://markdown-here.com/img/icon256.png)

  <!--Github Markdown-->
  <!-- Code Blocks-->
  ...bash
  >...  npm Install
  
  >...  npm start 

  >...javascript
   function add(num 1,num 2) {
    return nun1 + nun2;
   }
...
<!--Tables-->
   |NAME     |Email      |
   |---------|------------|
   |John Doe |John@gmail.com|
   | Jane Doe|Jane@gmail.com|
   

   <!-- Task Lists -->
   * [x] Task 1
   * [x] Task 2
   * [ ] Task 3
# Automatically Organize Your Desktop with a Python Script

Tired of a messy Desktop? This guide will walk you through creating a simple Python script that automatically sorts your files into folders like `Images`, `Documents`, and `Archives`.

## Before You Start

*   **Python 3** installed on your computer. [How to check and install it.](#)
*   Basic comfort with using the Terminal (Mac) or Command Prompt (Windows).

## The Script

Copy and paste the following code into a new file named `organize_desktop.py`.

```python
import os
from pathlib import Path

# Define the paths
desktop_path = Path.home() / 'Desktop'
file_types = {
    'Images': ['.jpg', '.jpeg', '.png', '.gif', '.svg'],
    'Documents': ['.pdf', '.docx', '.txt', '.xlsx'],
    'Archives': ['.zip', '.rar', '.7z']
}

# Create the folders if they don't exist
for folder_name in file_types.keys():
    (desktop_path / folder_name).mkdir(exist_ok=True)

# Move files to the corresponding folders
for file_path in desktop_path.iterdir():
    if file_path.is_file():
        for folder_name, extensions in file_types.items():
            if file_path.suffix.lower() in extensions:
                new_path = desktop_path / folder_name / file_path.name
                file_path.rename(new_path)
                print(f"Moved {file_path.name} to {folder_name}/")
                break

print("Desktop organization complete!")
