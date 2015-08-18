# API cs.io

### cs.io.close(path)

* **Description**: Close editor pane of currently opened file. 

* **Parameter**:
    * *String* path - file path

* **Return**: *cs.io*

### cs.io.fileExists(path)

* **Description**: Check if path point to existing file. 

* **Parameter**:
    * *String* path - file path

* **Return**: *bool*

### cs.io.include(path)

* **Description**: Include script file. 

* **Parameter**:
    * *String* path - file path

* **Return**: *cs.io*

### cs.io.open(path)

* **Description**: Opens a file in the according editor. 

* **Parameter**:
    * *String* path - file path

* **Return**: *cs.io*

### cs.io.read(path)

* **Description**: Read file into js string. 

* **Parameter**:
    * *String* path - file path

* **Return**: *string*

### cs.io.readCsv(path)

* **Description**: Read csv file into js array. 

* **Parameter**:
    * *String* path - file path

* **Return**: *array*

### cs.io.write(path, content)

* **Description**: Read file into js string. 

* **Parameter**:
    * *String* path - file path
    * *String* content - file content

* **Return**: *cs.io*