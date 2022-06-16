---
title: Toying with Binary files in C
description: Learn how to manage Binary files in C.
category: Dev
tags:
- Binary
- C
---

I noticed a lot of devs these days relay heavily on text or JSON files to store data/settings instead of using binary files. This maybe due to thinking that dealing with binary files are hard or requires deep knowledge in low level languages, which is false. Binary files are very similar to arrays of structures, except the structures are in a disk file rather than in an array in memory. Because the structures in a binary file are on disk, you can create very large collections of them (limited only by your available disk space). They are also permanent and always available. The only disadvantage is the slowness that comes from disk access time.<!--more-->

Disk access time is how long it takes to obtain the first data character after initiating a request. It includes the time to move the read/write head to the track (seek time) and time to rotate the platter to the sector (latency). Disk access time is always given as an average, because seek time and latency vary depending on the current position of the head and platter.

Binary files also usually have faster read and write times than text files, because a binary image of the record is stored directly from memory to disk (or vice versa). In a text file, everything has to be converted back and forth to text and this takes time. Here's three features that distinguish them from text files:

1. Non-readable file; Which acts like a protection from unwanted editing.
2. You can jump instantly to any structure in the file. Which provides random access as in an array.
3. You can change the contents of a structure anywhere in the file at any given time.

C supports the file-of-structures concept very cleanly. Once you open the file you can read a structure, write a structure, or seek to any structure in the file. This file concept supports the concept of a **file pointer**. When the file is opened, the pointer points to record 0 (the first record in the file). Any **read operation** reads the currently pointed-to structure and moves the pointer down one structure. Any **write operation** writes to the currently pointed-to structure and moves the pointer down one structure. **Seek** moves the pointer to the requested record.

Keep in mind that C thinks of everything in the disk file as blocks of bytes read from disk into memory or read from memory onto disk. C uses a file pointer, but it can point to any byte location in the file. You therefore have to keep track of things.

For example; Let's create a simple Binary file with the name **records.bin**:

```c
#include <stdio.h>

//Random record description - could be anything.
struct rec { int x, y, z; };

//Writes 10 arbitrary records to file "records.bin"
int main()
{
    FILE *f; //Init binary file
    struct rec r; //Init record structure

    //Create the file of 10 records
    f = fopen("records.bin", "w"); //"w" is for "write"

	//Throw error and exit with -1 if file wasn't created
    if (!f) {
        printf("Couldn't create file \"records.bin\"");
        return -1;
    }

	//Write records
    for (int i = 1; i <= 10; i++) {
        r.x = i;
        fwrite(&r, sizeof(struct rec), 1, f);
    }
	
    fclose(f); //Important
}
```

Now lets try to read those records from the file:

```c
#include <stdio.h>

struct rec { int x, y, z; };

int main()
{
    FILE *f;
    struct rec r;
    
    f = fopen("records.bin", "r"); //"r" is for "read"

    if (!f) {
        printf("Couldn't read file \"records.bin\"");
        return -1;
    }

    for (int i = 1; i <= 10; i++) {
        fread(&r, sizeof(struct rec), 1, f);
        printf("%d\n", r.x);
    }

    fclose(f);
}
```

Using `fseek` to read the records in reverse order:

```c
#include <stdio.h>

struct rec { int x, y, z; };

int main()
{
    FILE *f;
    struct rec r;
    
    f = fopen("records.bin", "r");

    if (!f) {
        printf("Couldn't read file \"records.bin\"");
        return -1;
    }

    for (int i = 9; i >= 0; i--) {
        //Seek
        fseek(f, sizeof(struct rec) * i, SEEK_SET);
        //Read
        fread(&r, sizeof(struct rec), 1, f);
        //Print
        printf("%d\n", r.x);
    }

    fclose(f);
}
```

Using `fseek` to read every other record:

```c
#include <stdio.h>

struct rec { int x, y, z; };

int main()
{
    FILE *f;
    struct rec r;
    
    f = fopen("records.bin", "r");
    
    if (!f) {
        printf("Couldn't read file \"records.bin\"");
        return -1;
    }
    
    fseek(f, 0, SEEK_SET);
    for (int i = 0; i < 5; i++) {
        fread(&r, sizeof(struct rec), 1, f);
        printf("%d\n", r.x);
        fseek(f, sizeof(struct rec), SEEK_CUR);
    }

    fclose(f);
}
```

Using `fseek` to read 4th record, change it, and write it back:

```c
#include <stdio.h>

struct rec { int x, y, z; };

int main()
{
    FILE *f;
    struct rec r;
    
    f = fopen("records.bin", "r+"); //Notice the "r+" which means "read/write".
    
    if (!f) {
        printf("Couldn't read file \"records.bin\"");
        return -1;
    }
    
    fseek(f, sizeof(struct rec) * 3, SEEK_SET);
    fread(&r, sizeof(struct rec), 1, f);
    printf("4th record value before: %d\n", r.x);
    r.x = 666;
    fseek(f, sizeof(struct rec) * 3, SEEK_SET);
    fwrite(&r, sizeof(struct rec), 1, f);
    printf("4th record value now: %d\n", r.x);

    /*
    * You can also use the second code/program that we wrote
    * previously to read the 4th record value
    * and see that it was changed to "666" 
    */

    fclose(f);
}
```

In these concepts, a structure description **rec** has been used, but you can use any structure description you want. You can see that **fopen** and **fclose** work exactly as they did for text files.

The new functions here are **fread**, **fwrite** and **fseek**. The fread function takes four parameters:

1. A memory address
2. The number of bytes to read per block
3. The number of blocks to read
4. The file variable

Thus, the line `fread(&r, sizeof(struct rec), 1, f);` says to read 12 bytes (the size of **rec**) from the file **f** (from the current location of the file pointer) into memory address **&r**. One block of 12 bytes is requested. It would be just as easy to read 100 blocks from disk into an array in memory by changing 1 to 100.

The **fwrite** function works the same way, but moves the block of bytes from memory to the file. The **fseek** function moves the file pointer to a byte in the file. Generally, you move the pointer in **sizeof(struct rec)** increments to keep the pointer at record boundaries. You can use three options when seeking:

* SEEK_SET
* SEEK_CUR
* SEEK_END

`SEEK_SET` moves the pointer x bytes down from the beginning of the file (from byte 0 in the file). `SEEK_CUR` moves the pointer x bytes down from the current pointer position. `SEEK_END` moves the pointer from the end of the file (so you must use negative offsets with this option).

Several different options appear in the codes above. In particular, note the section where the file is opened with **r+** mode. This opens the file for reading and writing, which allows records to be changed. The code seeks to a record, reads it, and changes a field; it then seeks back because the read displaced the pointer, and writes the change back.
