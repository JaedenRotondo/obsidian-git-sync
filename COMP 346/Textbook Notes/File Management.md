## 13.1 File Concept 
--- 
> Files are the method that users and applications use to store and retrieve data. 
#### File Attributes
- Name: symbolic file name is kept in human-readable form 
- Identifie: A unique tag kept in non-readable form for the system
- Type: For systems which support a particular file
- Location: A pointer to a device and location of the file
- Size: Current file size and possibly max file size
- Protection: Access rifhts of the file (read, write, execute)
- Timestamp and user info
- Note that some file systems support extended attributes *click "view proper ties" on a file*
#### File operations
- Creating a fil
- Opening a fil
- Writing to a fil
- Reading a fil
- Repositioning (seek) a fil (doesn't require actual I/O)
- Deleting a fil
- Truncation a fil 
#### File Types
- Systems use an extension (like .exe) for file type indication
- There are many common file types, ones which might be present on the exam include: 
- ![[Pasted image 20230419140901.png]]
#### File Structure
- An operating system requires an execuatbale file to have a specific structure so that it can determine where in memory to load the fule and what the location of the first instruction is
	- This poses a problem for multi-file operating systems... All of this information about how to read files need to be stored in the OS
##### Internal File Structure
- A file may be considered as a sequence of blocks
	- All disk I/O is performed in units of one block (physical record) which are the same size
- The waste incurred to keep everything in units of blocks (instead of bytes) is **internal fragmentation**. All file systems suffer from internal fragmentation; the larger the block size, the greater the internal fragmentation. 
---
## 13.2 Access Methods
#### Sequential Access
- The simplest method of file access is sequentially. E.g. ReadNextLine()
#### Direct Access
- Here, a file is made up of fixed-length logical records (virtual addresses) that allow programs to read and write to records rapidly in no particular order
	- Example: Disk model of a file. A disk is serperated as anumbered sequence of blocks and can be skipped over
- Acces is determined by relative block number, meaning that the file block number starts at zero 
	- *This is beneficial for security purposes, the Memory Manager acts as a security because it can see if a process is trying to access data outside its logical data allocation* 
#### Other Access Methods
- Indexing is another form of file access
	- This allows for fast searching mechanisms and is good for very large data
	- ![[Pasted image 20230419142532.png]]
---
## 13.3 Directory Structure 
- Directory structures can be viewed as symbol tables that translates file names into their control blocks
- Directories must allow for the following actions:
	- Create a fil
	- Insert entries
	- Delete entries 
	- Search for a named entry
	- List all entries in a directory 
	- Rename a file 
	- Traverse the directory 
#### Single-Level Directory 
- This is the simplest form of file directory 
	- All files are contained in the same directory
	- ![[Screenshot 2023-04-19 at 3.47.42 PM.png]]
	- There are a significant number of limitations of the single level directory system: 
		- If there is more than one user, file names will become very difficult to manage
		- unique name rules can be violated even with a single user 
		- keeping track of hundreds of files in the same directory is a daunting task 
#### Two Level Directory 
- In the two level directory, the master file directory is includes the directories of each user
- Can be seen as a tree with a height of 2
- ![[Screenshot 2023-04-19 at 3.50.28 PM.png]]
- There is an enhancement of security with the two layers, for example, a user is confined to their own directory (UFD) when deleting files. 
- Although the two level directory solves the name-collision problem there still are *disadvantages*:
	- This structure isolates one user from another 
		- This means they cannot cooperate in tasks or need to access other users files
		- If we give access to other user directories, it creates the problem of a user deleting other use files 
		- If *access is permitted* then a "path name" is required when you need to access a file in a different directory like `/userb/test.txt`
- If we use these user directories, where do we store system level files? 
	- One solution is to copy all the system files into every user directory - but this wastes a lot of space
	- Solution: A special user directory is created which stores all the system files. Whenever a file name is loaded, the operating system first checks the UFD. If the file isnt found then it is automatically searched for in the special user directory. 
- The sequence of directories searched when looking for a file is called the *search path* andis used by UNIX and Windows. 
#### Tree- Structured Directories 
- This is the natural generalization of two-level directory structure 
- ![[Screenshot 2023-04-19 at 4.08.25 PM.png]]
- absolute path and relative paths
- This system allows for different users to access other user files, which is better than the 2-level model which suffered from user isolation
- With the tree structure, whether or not you allow deleting directories is can cause big problems. For example, deleting root could wipe your entire system. 
	- This is why sometimes you can only delete a directory if its empty
## 13.4 Protection 
- There are different types of access in terms of file protection 
- Types of file access 
![[Screenshot 2023-04-20 at 8.55.24 AM.png]]
##### Access Control
- Access control list
	1. Owner: The creator of the file
	2. Group: The set of users who share the file and need similar access
	3. Other: All other users 
##### Password protected files
- Can be effected based on the strengh of passwords 
- Requires the user to memorize too many passwords 