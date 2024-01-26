## Command Line Tools Cheat Sheet

### 1. `sed` (Stream Editor)
- **Usage**: Text substitution, filtering, and transformation.
- **Syntax**: `sed [options] 'command' file`
- **Options**:
  - `-i`: Edit files in-place.
  - `-e`: Multiple commands.
  - `-n`: Suppress automatic printing.
- **Examples**:
  - Replace 'foo' with 'bar': `sed -i 's/foo/bar/g' file.txt`
  - Delete lines 2 to 5: `sed '2,5d' file.txt`
  - Print lines matching 'start' to 'end': `sed -n '/start/,/end/p' file.txt`
  - Append text after a line: `sed '/pattern/a new line of text' file.txt`

### 2. `awk`
- **Usage**: Processing and analyzing text files.
- **Syntax**: `awk [options] 'program' file`
- **Options**:
  - `-F`: Field separator.
  - `-v var=value`: Set variable.
- **Examples**:
  - Print the second column: `awk '{print $2}' file.txt`
  - Sum and average of first column: `awk '{sum += $1} END {print "Sum:", sum, "Average:", sum/NR}' file.txt`
  - Print lines where third column > 5: `awk '$3 > 5' file.txt`
  - Use comma as separator: `awk -F, '{print $1}' file.csv`

### 3. `grep`
- **Usage**: Searching for text using patterns.
- **Syntax**: `grep [options] 'pattern' file`
- **Options**:
  - `-i`: Ignore case.
  - `-r`: Recursive search.
  - `-l`: List file names.
- **Examples**:
  - Find 'pattern' in .txt files: `grep 'pattern' *.txt`
  - Case-insensitive search: `grep -i 'pattern' file.txt`
  - List files with 'pattern': `grep -l 'pattern' *`
  - Count 'pattern' occurrences: `grep -c 'pattern' file.txt`

### 4. `jq`
- **Usage**: Parsing and transforming JSON.
- **Syntax**: `jq 'filter' [file]`
- **Examples**:
  - Extract "name" key: `jq '.[] | .name' file.json`
  - Filter objects by age > 30: `jq '.[] | select(.age > 30)' file.json`
  - Increase quantity by 1: `jq '.items[] .quantity |= . + 1' file.json`
  - Combine fields into new object: `jq '{name: .name, total: .price * .quantity}' file.json`

### 5. `yq`
- **Usage**: YAML processing.
- **Syntax**: `yq [options] 'expression' [file]`
- **Options**:
  - `-i`: Update file in-place.
  - `-o=json`: Output as JSON.
- **Examples**:
  - Extract value of key: `yq e '.key' file.yaml`
  - Update value: `yq e '.key = "newValue"' -i file.yaml`
  - Merge two YAML files: `yq ea '. as $item ireduce ({}; . * $item )' file1.yaml file2.yaml`
  - Convert YAML to JSON: `yq e -o=json file.yaml`

### General Tips
- Experiment safely: Test commands in a controlled environment.
- Chain Commands: Combine tools using pipes (`|`) for complex workflows.
- Regular Expressions: Utilize regex for advanced pattern matching.
