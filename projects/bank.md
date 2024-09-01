---
layout: project
type: project
image: img/bank/bank.png
title: "Banking Record Tracker"
date: 2023-10-26
published: true
labels:
  - C
  - C++
  - Pointers
  - Vim
summary: "A banking system record tracker that I developed for ICS 212."
---

<img class="img-fluid" src="../img/bank/bank1.png">

This project simulates a banking system record tracker that I developed in my ICS 212 class. When run, the program prompts the user with a welcome message, giving the rundown of how the user can interact with the system. You can add, delete, or find a specific record or you can print all the records entered in the database so far. There is also an option to quit the program and if the user exits and decides to rerun the executable, all records will be remembered from the prior run. The program tells the user that they are able to access any of these commands by entering specific keywords, however, the code also allows a command to be called if a command is only partially entered. For example, if the user wants to select the ‘find’ option but only enters ‘fi’, the command will still run and all the necessary follow up questions will execute. 

This project was coded across multiple files for the interface and database which demonstrates the skill of being able to link files together to create a cohesive end result. While this project was originally coded in C, I also redid it with the same premise and requirements in C++ to demonstrate competence in both languages.

Here are some of the functions I used in order to implement to auto-save feature of this project:
```cpp
/*****************************************************************
//
//  Function name: writefile
//      
//  DESCRIPTION:   a function that writes all of the contents of the
//                 linked list to a file
//    
//  Parameters:    start (struct record *) : starting address of the 
//                                           linked list
//                 filename (char []) : the file name being written to
//     
//  Return values:  0 : file was able to be accessed
//                 -1 : file was not able to be accessed
//   
*****************************************************************************/
int writefile(struct record * start, char filename[])
{
    int success = 0;
    FILE * outfile;
    struct record * temp;
    if (debugmode == 1)
    {
        printf("===================================================\n");
        printf("FUNCTION NAME: writefile\n");
        printf("PARAMETER NAME: filename\n");
        printf("VALUE OF filename: %s\n", filename);
        printf("===================================================\n");
        printf("\n");
    }
    outfile = fopen(filename, "w");
    if (outfile == NULL)
    {
        success = -1;
    }
    else
    {
        temp = start;
        while (temp != NULL)
        {
            fprintf(outfile, "%d\n", temp->accountno);
            fprintf(outfile, "%s\n", temp->name);
            fprintf(outfile, "%s]\n", temp->address);
            temp = temp->next;
        }
    }
    return success;
}

/*****************************************************************
//
//  Function name: readfile
//        
//  DESCRIPTION:   a function that reads from the file the records are
//                 stored into and puts into the linked list
//    
//  Parameters:    start (struct record **) : a pointer that points to
//                                            the pointer called start
//                 filename (char []) : the file name that is being read from
//      
//  Return values:  0 : file successfully opened
//                 -1 : file could not be opened
//     
*********************************************************************************/
int readfile(struct record ** start, char filename[])
{
    FILE *infile;
    int success = 0;
    int accountNo;
    int index = 0;
    char character;
    int length;
    char name[30];
    char address[50];
    char hold[100];
    if (debugmode == 1)
    {
        printf("===================================================\n");
        printf("FUNCTION NAME: readfile\n");
        printf("PARAMETER NAME: filename\n");
        printf("VALUE OF filename: %s\n", filename);
        printf("===================================================\n");
        printf("\n");
    }
    infile = fopen(filename, "r");
    if (infile == NULL)
    {
        success = -1;
    }
    else
    {
        while (fscanf(infile, "%d", &accountNo) != EOF)
        {
            fgets(hold, 100, infile);
            fgets(name, 30, infile);
            length = strlen(name);
            if (length > 0 && name[length - 1] == '\n')
            {
                name[length - 1] = '\0';
            }
            for (index = 0; index < 50; index++)
            {
                character = fgetc(infile);
                address[index] = character;
                if (character == ']')
                {
                    address[index] = '\0';
                    index = 50;
                }
            }
            index = 0;
            addRecord(start, accountNo, name, address);
        }
        fclose(infile);
    }
    return success;
}
```

