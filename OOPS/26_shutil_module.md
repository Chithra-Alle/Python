# shutile Module in python
- shutile is nothing but *Shell Utility* module, it provides functions for file and directory management, inclduing copying, moving, deleting and archiving files and directories.

- ## Rules and Cosniderations
- 1. Use copy2() instead of copy() if you want to keep file metadata.
  2. Use copy2() instead of copy() if you want to keep file metadata.
  3. Use shutil.move() for renaming files (it works like os.rename()).
  4. make_archive() only works with entire directories, not individual files.
  5. Ensure you have permission before performing operations like move() or rmtree().
 
  ### Key features of shutile module
|Function|	Description	|Example|
|:-------:|:-----------:|:------:|
|shutil.copy(src, dest)|	Copies a file from src to dest.	shutil.copy("file.txt", "backup.txt")|
|shutil.copy2(src, dest)|	Similar to copy(), but also preserves metadata (timestamps, permissions).	shutil.copy2("file.txt", "backup.txt")|
|shutil.copytree(src, dest)|	Copies an entire directory tree from src to dest.	shutil.copytree("my_folder", "backup_folder")|
|shutil.move(src, dest)|	Moves a file or directory to a new location.	shutil.move("file.txt", "new_folder/")|
|shutil.rmtree(path)|	Deletes an entire directory tree. (Use with caution)	shutil.rmtree("old_folder")|
|shutil.disk_usage(path)|	Returns disk usage statistics (total, used, free space).	shutil.disk_usage("/")|
|shutil.make_archive(base_name, format, root_dir)|	Creates a compressed archive (zip, tar, etc.).	shutil.make_archive("backup", "zip", "my_folder")|
|shutil.unpack_archive(filename, extract_dir)|	Extracts an archive to a specified directory.	shutil.unpack_archive("backup.zip", "restore_folder")|


## Example Usage
```
import shutil

# Copy a file
shutil.copy("data.txt", "backup.txt")

# Move a file
shutil.move("backup.txt", "archive/backup.txt")

# Create a ZIP archive
shutil.make_archive("project_backup", "zip", "my_project")

# Delete a directory
shutil.rmtree("old_backup")  # BE CAREFUL!
```
