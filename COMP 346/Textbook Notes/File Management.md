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
- 
## 13.4 Security 
