# ⭐️ Introduction
This library is a Python-based toolkit for recording data to files (including SQLite).
It's easy to use, has concise code, and is a reliable, worry-free, and practical tool.
It also supports multi-threaded writing to files.
**QQ Group for discussion:** 897838127
**Contact email:** g1879@qq.com
**User manual:** 📒[Click to open](http://g1879.gitee.io/datarecorderdocs/)

# ✨️ Philosophy
Simple, reliable, and worry-free.

# 📕 Background
When collecting data, it's often necessary to save data to files. Frequently opening and closing files can affect efficiency, while waiting until the end of collection to write can risk losing data due to exceptions.
Therefore, these tools were written to cache data up to a certain amount before writing at once, reducing the number of file operations, and automatically saving as much as possible in case of program crashes or exits.
They are very convenient to use. Whenever and wherever, regardless of the format, you just need to use the `add_data()` method to store the data. The syntax is extremely concise, allowing programmers to focus more on business logic.
They are also quite reliable. The author has once continuously recorded over 3 million pieces of data in one go, and also had 50 threads simultaneously writing tens of thousands of pieces of data to a single file, still handling it with ease.
The tools have also been optimized for spreadsheet files (xlsx, csv), encapsulating practical functions that can easily implement resume-from-breakpoint crawling, batch data transfer, writing data at specified coordinates, and more using spreadsheet files.

# 🍀 Features
- Can cache data up to a certain amount before writing at once, reducing the number of file read/write operations and lowering overhead.
- Supports multi-threaded simultaneous data writing.
- When writing, if the file is open, it will automatically wait for the file to close before writing, avoiding data loss.
- Provides good support for resume-from-breakpoint crawling.
- Convenient batch data transfer.
- Can automatically create headers based on dictionary data.
- Automatically creates files and paths, reducing code volume.

# 🌠 Overview
Here's a brief introduction to the uses of various tools. For detailed usage, please refer to the Usage Methods section.

## ⚡ Recorder `Recorder`
The `Recorder`'s functionality is simple, intuitive, efficient, and practical. It does one action: continuously receiving data and adding it to the file in order. It can receive single-line data or two-dimensional data to write multiple lines at once.
It supports four file formats: csv, xlsx, json, and txt.
```python
from DataRecorder import Recorder
data = ((1, 2, 3, 4), 
        (5, 6, 7, 8))
r = Recorder('data.csv')
r.add_data(data)  # Record multiple lines of data at once
r.add_data('abc')  # Record single line of data
```

### ⚡ Table Filler`Filler`
`Filler` is used to fill data into spreadsheet files and can specify the coordinates to fill. Its use is very flexible; you can specify coordinates as the upper-left corner and fill in a patch of two-dimensional data. It also encapsulates the function of recording data processing progress (such as resume-from-breakpoint crawling). In addition, it can set links for cells. It only supports csv and xlsx file formats.
```python
from DataRecorder import Filler
f = Filler('results.csv')
f.add_data((1, 2, 3, 4), 'a2')  # Write a row of data starting from cell A2
f.add_data(((1, 2), (3, 4)), 'd4')  # Write a patch of 2D data with D4 as the upper-left corner
```

### ⚡ Binary Data Recorder`ByteRecorder`
`ByteRecorder` is the simplest to use. It's similar to `Recorder`, recording multiple data and then writing to the file in order. The difference is that it only accepts binary data, can only input one piece of data per `add_data()`, and has no concept of rows. It can be used in conjunction with the author's other tool [FlowViewer](https://gitee.com/g1879/FlowViewer) to obtain files loaded by the browser or to record downloaded files. You can specify the position of each data written in the file to support multi-threaded file downloads. Supports any file format.
```python
from DataRecorder import ByteRecorder
b = ByteRecorder('data.file')
b.add_data(b'xxxxxxxxxxx')  # Write binary data to the file
```

## ⚡ Database Recorder`DBRecorder`
Supports SQLite, with usage consistent with `Recorder`. Supports automatic creation of databases, data tables, and data columns.
```python
from DataRecorder import DBRecorder
d = DBRecorder('data.db')
d.add_data({'name': 'Zhang San', 'age': 25}, table='user')  # Insert data into user table
d.record()
```

# 🛠 Usage Methods
[📒Click to jump to the user manual](http://g1879.gitee.io/datarecorderdocs/)
# ☕ Buy Me a Coffee
If this project has been helpful to you, why not buy the author a cup of coffee ：）
![](https://gitee.com/g1879/DrissionPage-demos/raw/master/pics/code.jpg)
