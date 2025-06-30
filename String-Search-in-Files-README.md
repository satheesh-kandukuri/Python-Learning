**String Search in Files**

A Python script to recursively search for text strings in files within a directory, with support for both regular text files and gzip-compressed files.
Features

🔍 Recursive Search: Searches through all subdirectories

📁 File Type Filtering: Filter by file extensions (e.g., .txt, .log, .py)

🔤 Case Sensitivity: Toggle case-sensitive or case-insensitive search

📦 Gzip Support: Automatically handles .gz compressed files

📊 Detailed Results: Shows file path, line number, and matching content

💾 Export Results: Save search results to a text file

🛡️ Error Handling: Gracefully handles permission errors and encoding issues

**Requirements**

Python 3.6+

Standard library modules: **os, sys, pathlib, gzip**

 
**Installation**

```bash
git clone https://github.com/yourusername/string-search-files.git
cd string-search-files
```

**Run the script:**

```bash
python string_search.py
```

**Example**
```bash
$ python file_search.py
Enter directory path to search: ./my_project
Enter string to search for: TODO
Case sensitive search? (y/n): n
File extensions to search (e.g., .txt,.py,.log) or press Enter for all: .py
Save results to file? (y/n): y
```

**Output:**

```bash
Searching for 'TODO' in directory: my_project
------------------------------------------------------------
Found in: my_project/script.py
  Line 10: # TODO: Add error handling

Found in: my_project/utils.py
  Line 25: # todo: Optimize this function
------------------------------------------------------------
Search completed!
Files searched: 15
Total matches found: 2
Files with matches: 2
Results saved to: search_results_TODO.txt
```

**Error Handling**





* Skips files with permission errors, decoding errors, or invalid gzip files


* Validates directory existence


* Handles empty search strings


* Ignores non-file entries during directory traversal

**Output File**

If saving results is enabled, a file named **search_results_<search_term>.txt **is created with the search results, including:


* Search term

* Directory searched

* File paths, line numbers, and matching lines

**Returns**

List of dictionaries containing:

* file: Full file path
* line_number: Line number where match was found
* line_content: Content of the matching line

**Supported File Types**

* Text files: .txt, .log, .csv, .py, .js, etc.
* Compressed files: .gz files are automatically decompressed and searched
* All file types: When no extension filter is specified
