---
layout: page
title: "Q32309: Using _harderr to Capture Critical Error Interrupt 24h"
permalink: /kb/032/Q32309/
---

## Q32309: Using _harderr to Capture Critical Error Interrupt 24h

{% raw %}

	Article: Q32309
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 22-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C Run-Time (CRT), included with:
	   - Microsoft C for MS-DOS, versions 5.1, 6.0, 6.0a, 6.0ax 
	   - Microsoft C for OS/2, versions 5.1, 6.0, 6.0a 
	   - Microsoft C/C++ for MS-DOS, version 7.0 
	   - Microsoft Visual C++, versions 1.0, 1.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The text below demonstrates using the critical-error-handler function _harderr()
	that was introduced with the Microsoft C version 5.0 run- time library.
	
	This function change the MS-DOS critical-error-handler interrupt, Interrupt 24h,
	to point to a user-defined error-handler function. This function accepts three
	parameters that contain information about the hardware error that triggered the
	call to the error-handler function.
	
	The sample code includes a number of functions that shift and mask these
	parameters and returns a value that corresponds to one of the manifest constant
	values defined in the library header file.
	
	MORE INFORMATION
	================
	
	The end of the HARDERR.C file provides information about declaring the
	user-defined error-handler function. The HARDTEST.C file demonstrates calling
	the user-defined error-handler function.
	
	HARDERR.H
	---------
	
	  // This header file defines the manifest constants and function
	  // prototypes for HARDERR.C.
	
	  // Boolean constants
	
	  #define TRUE -1
	  #define FALSE 0
	  typedef signed boolean;
	
	  // Manifest constants for get_codeloc()
	
	  #define DOS       0x0
	  #define FAT       0x1
	  #define DIRECTORY 0x2
	  #define DATA      0x3
	
	  // Manifest constants for get_errcode()
	
	  #define WRITE_PROTECT_ERR  0x0
	  #define UNKNOWN_UNIT       0x1
	  #define DRIVE_NOT_READY    0x2
	  #define UNKNOWN_CMD        0x3
	  #define CRC_ERR            0x4
	  #define BAD_DRV_REQUEST    0x5
	  #define SEEK_ERR           0x6
	  #define UNKNOWN_MEDIA      0x7
	  #define SECTOR_NOT_FOUND   0x8
	  #define OUT_OF_PAPER       0x9
	  #define WRITE_FAULT        0xA
	  #define READ_FAULT         0xB
	  #define GENERAL_FAILURE    0xC
	
	  // Manifest constants for get_curr_dev()
	
	  #define CURRENT_INPUT_DEVICE    0x1
	  #define CURRENT_OUTPUT_DEVICE   0x2
	  #define CURRENT_NULL_DEVICE     0x4
	  #define CURRENT_CLOCK_DEVICE    0x8
	  #define BAD_MEM_IMAGE           0xF
	
	  // Type definitions
	
	  #define HEADER struct _device_header
	  extern HEADER
	  {
	     long     far *devptr;
	     unsigned far *attrib;
	     unsigned far *stratptr;
	     unsigned far *intrptr;
	     char     far *devname;
	  };
	
	  // Function prototypes
	
	  unsigned getdrv(void);
	  unsigned get_errcode(void);
	  unsigned get_deverr(void);
	  unsigned get_codeloc(void);
	  unsigned far* get_devhdr(HEADER *header);
	  char get_curr_dev(void);
	  void* get_devname(void);
	  boolean is_harderr(void);
	  void hardreset(void);
	  boolean is_diskerr(void);
	  boolean is_char_dev(void);
	  boolean is_read_err(void);
	  boolean is_write_err(void);
	  void handler(unsigned deverr, unsigned errcode, unsigned far *devhdr);
	
	HARDERR.C
	---------
	
	  // This file implements a number of functions to work with the
	  // _harderr() function in the Microsoft C run-time library. When a
	  // hardware error occurs, the _harderr() function calls an error-
	  // handler function defined in this file. The error handler sets flags
	  // to indicate the cause of the hardware error in a global structure
	  // _hflags.
	  // 
	  // Bits in each flag byte indicate the causes of the error. The
	  // functions shift and mask the bits to obtain the causes of the
	  // error.
	  // 
	  // Please read the comments in the code below carefully; they contain
	  // several warnings.
	  // 
	  // Compile options needed: -AL -c -Od -W3 -Zi
	  // Link options needed: None
	
	  // Preprocessor information
	  #include <dos.h>
	  #include <malloc.h>
	  #define TRUE -1
	  #define FALSE 0
	
	  // Type definition
	  typedef signed boolean;
	
	  // Do not modify the members of the HEADER structure! For more
	  // information, please refer to an IBM or Microsoft programmer's
	  // reference manual.
	  #define HEADER struct _device_header
	  typedef HEADER
	  {
	     long     far *devptr;
	     unsigned far *attrib;
	     unsigned far *stratptr;
	     unsigned far *intrptr;
	     char     far *devname;
	  };
	
	  // Global data
	  static struct
	  {
	     unsigned deverr;
	     unsigned errcode;
	     unsigned far *devhdr;  // READ ONLY pointer to a HEADER structure
	  } near _hflags;
	
	  static boolean near _err = FALSE; // Error flag. FALSE = no hardware
	                                    // error
	
	  // Function definitions
	  // Use these functions to retrieve information after a hardware error
	  // occurs. When no hardware error has occurred, these functions
	  // return random values.
	
	  // getdrv() returns drive letter if error occurred on a drive.
	  unsigned getdrv(void)
	  {
	     return (_hflags.deverr & 0x00ff) + 0x41;
	  }
	
	  // get_errcode() returns the hardware error type. The function
	  // returns one of the manifest constants defined in HARDERR.H.
	  unsigned get_errcode(void)
	  {
	     return _hflags.errcode;
	  }
	
	  // get_deverr returns information about device errors; for example,
	  // a disk error
	  unsigned get_deverr(void)
	  {
	     return _hflags.deverr;
	  }
	
	  // get_codeloc() returns the code location where the hardware error
	  // occurred. The function returns one of the code locations defined in
	  // HARDERR.H.
	  unsigned get_codeloc(void)
	  {
	     return (_hflags.deverr & 0x0600) >> 9;
	  }
	
	  // get_devhdr() accepts the address of a HEADER structure and returns
	  // a pointer to the device header. If the HEADER structure the pointer
	  // parameter specifies defines the WORD fields of the device header,
	  // these fields are defined in the HEADER structure specified by the
	  // return value. Otherwise, these fields are not defined.
	  unsigned far* get_devhdr(HEADER *header)
	  {
	     if (!_err)
	        return 0;
	     header = (HEADER *)_hflags.devhdr;
	     return _hflags.devhdr;
	  }
	
	  // get_curr_dev() returns the low nibble of the attribute word at
	  // offset 04 of the device header. The function returns one of the
	  // manifest constants defined in HARDERR.H. This information indicates
	  // serious hardware failures.
	  char get_curr_dev(void)
	  {
	     return (char)(_hflags.devhdr[2] & 0x000f);
	  }
	
	  // get_devname() returns the name of the device on which the error
	  // occurred. For example, if a printer is out of paper, this function
	  // returns the value "PRN".
	  void* get_devname(void)
	  {
	     char *ptr, i = 0;
	     ptr = (char *)malloc(8);
	     while (i < 8)
	     {
	        ptr[i] = ((char *) &(_hflags.devhdr[5]))[i];
	        i++;
	     }
	     ptr[8] = '\0';
	     return &ptr[0];
	  }
	
	  // The following functions determine if a hardware error has occurred
	  // and, if so, where it occurred. You must call these functions in the
	  // proper order. Failing to call them in the correct order can cause
	  // unpredictable results.
	
	  // is_harderr() is the most important function of the library. It
	  // determines that a hardware error has occurred. If this function
	  // does not return TRUE, the values returned by all the other
	  // functions defined in this library are undefined.
	  boolean is_harderr(void)
	  {
	     return _err;
	  }
	
	  // After calling is_harderr(), you must call hardreset().
	  void hardreset(void)
	  {
	     _err = FALSE;
	  }
	
	  // is_diskerr() returns TRUE if a device error occurred on a disk
	  // drive; for example, if the drive door is open. This function
	  // returns undefined results for drives that do not exist and for
	  // virtual drives, such as RAM drives.
	  boolean is_diskerr(void)
	  {
	     return (_hflags.deverr & 0x8000) == 0 ? TRUE : FALSE;
	  }
	
	  // If a hardware error occurred, and it is not a disk error, call
	  // is_char_dev() to determine if the error involved a character device
	  // (PRN, KBD, TRM, and so on) of if it is a block error. If this
	  // function returns FALSE, the error may be a bad memory image of the
	  // File Allocation Table (FAT).
	  boolean is_char_dev(void)
	  {
	     return (_hflags.devhdr[2] & 0x8000) == 0 ? FALSE : TRUE;
	  }
	
	  // is_read_err() returns TRUE when the error was a read error.
	  boolean is_read_err(void)
	  {
	     return (_hflags.deverr & 0x0100) != 0 ? FALSE : TRUE;
	  }
	
	  // is_write_err() returns TRUE when the error was a write error.
	  boolean is_write_err(void)
	  {
	     return (is_read_err() == TRUE ? FALSE : TRUE);
	  }
	
	  // handler() is the main function in this file. You cannot call any of
	  // the functions defined above until after you call the _harderr()
	  // function with the address of this handler.
	  void handler(unsigned deverr, unsigned errcode, unsigned far *devhdr)
	  {
	     _hflags.deverr  = deverr;
	     _hflags.errcode = errcode;
	     _hflags.devhdr  = devhdr;
	     _err = TRUE;
	     _hardretn(1);
	  }
	
	HARDTEST.C
	----------
	
	  // This code example demonstrates using HARDERR.LIB.
	  // 
	  // This program determines if the floppy drive door is open when the
	  // program attempts to write to disk or it determines if the printer
	  // is on or is out of paper. The program checks only the disk or the
	  // printer each time it runs.
	  // 
	  // To use this program, perform one of the following:
	  //  - Open the door to your floppy disk drive and run the program.
	  //    -or-
	  //  - Turn off your printer and run the program.
	  //    -or-
	  //  - Remove the paper from your printer and run the program.
	  // 
	  // Compiler options needed: -AL -Od -W3 -Zi
	
	  #include <stdio.h>
	  #include <stdlib.h>
	  #include <fcntl.h>
	  #include <sys\types.h>
	  #include <sys\stat.h>
	  #include <io.h>
	  #include <dos.h>
	  #include <graph.h>
	  #include <conio.h>
	  #include "harderr.h"
	
	  #define _PATHLENGTH_ 64
	  #define _BUFFLENGTH_ 20
	  #define INT24 0x24
	
	  void (far *fptr)();   // Pointer to error-handler routine
	                        // defined in HARDERR.C.
	  void (interrupt far *OldHandler)(); // Pointer to the original
	                                      // error-handler routine.
	
	  void main(void);
	  void print_errmsg(unsigned errcode);
	  void print_codeloc(unsigned codeloc);
	  void p_deverr(char error);
	
	  char path[_PATHLENGTH_], buffer[_BUFFLENGTH_] = "Hello, World\n";
	
	  void main(void)
	  {
	     int fh, ch;
	     unsigned far *headptr;
	     HEADER header;
	
	     OldHandler = _dos_getvect(INT24); // Save original handler.
	     fptr = handler;
	     _harderr(fptr);  // Set harderr to handler()
	
	     printf("Do you wish to reset the harderr handler? [y/n] ");
	     ch = getche();
	
	     if (toupper(ch) == 'Y')   // Reset to original handler.
	        _dos_setvect(INT24, OldHandler);
	
	     _clearscreen(_GCLEARSCREEN);
	     printf("\nPlease enter path: ");
	     fscanf(stdin, "%s", path);
	
	     fh = open(path, O_CREAT | O_TEXT | O_RDWR, S_IWRITE);
	     printf("\nOpening %s....\n", path);
	
	     if (!is_harderr())    // Was open successful?
	     {
	        puts("No hardware error detected.");
	
	        fh = fileno(stdprn);
	        printf("\nPrinting %s....\n", path);
	        write(fh, buffer, _BUFFLENGTH_);    // Write to the printer
	     }
	
	     if (is_harderr())   // Print hardware error diagnostics
	     {
	        puts("Hardware error!");
	        if (is_diskerr())
	        {
	           printf("Drive         = %c:\n", getdrv());
	           printf("Error code    = ");
	           print_errmsg(get_errcode());
	           printf("Code location = ");
	           print_codeloc(get_codeloc());
	        }
	        else
	        {
	           headptr = get_devhdr(&header);
	           // Implemented for illustration and for viewing in CodeView.
	
	           if (is_char_dev())
	              puts("Character device error!");
	           else
	              puts("Block device error!");
	           printf("Error code = ");
	           print_errmsg(get_errcode());
	           printf("Code location = ");
	           print_codeloc(get_codeloc());
	           printf("Device name = %s\n", get_devname());
	           printf("Device: ");
	           p_deverr(get_curr_dev());
	        }
	        if (is_write_err())
	           puts("Write error!");
	        else
	           puts("Read error!");
	        hardreset();
	     }
	     else
	        puts("No hardware error detected.");
	     close(fh);
	     exit(0);
	  }
	
	  void print_errmsg(unsigned errcode)
	  {
	     switch (errcode)
	        {
	     case WRITE_PROTECT_ERR:
	        puts("WRITE PROTECT ERROR!");
	        break;
	     case UNKNOWN_UNIT:
	        puts("UNKNOWN UNIT!");
	        break;
	     case DRIVE_NOT_READY:
	        puts("DRIVE NOT READY!");
	        break;
	     case UNKNOWN_CMD:
	        puts("UNKNOWN COMMAND!");
	        break;
	     case CRC_ERR:
	        puts("CYCLIC REDUNDANCY CHECK!");
	        break;
	     case BAD_DRV_REQUEST:
	        puts("BAD DRIVE REQUEST!");
	        break;
	     case SEEK_ERR:
	        puts("SEEK ERROR!");
	        break;
	     case UNKNOWN_MEDIA:
	        puts("UNKNOWN MEDIA!");
	        break;
	     case SECTOR_NOT_FOUND:
	        puts("SECTOR NOT FOUND!");
	        break;
	     case OUT_OF_PAPER:
	        puts("OUT OF PAPER!");
	        break;
	     case WRITE_FAULT:
	        puts("WRITE FAULT!");
	        break;
	     case READ_FAULT:
	        puts("READ FAULT!");
	        break;
	     case GENERAL_FAILURE:
	        puts("GENERAL FAILURE!");
	        break;
	     default:
	        puts("NO ERROR!");
	        break;
	        }
	  }
	
	  void print_codeloc(unsigned codeloc)
	  {
	     switch (codeloc)
	        {
	     case DOS:
	        puts("MS-DOS");
	        break;
	     case FAT:
	        puts("FAT");
	        break;
	     case DIRECTORY:
	        puts("DIRECTORY");
	        break;
	     case DATA:
	        puts("DATA");
	        break;
	     default:
	        puts("ERROR PRINTING CODE LOCATION.");
	        break;
	        }
	  }
	
	  // Call p_deverr only if an error occurred on a device other than a
	  // disk drive and if the error occurred on a default device. This
	  // program uses only the default selection of the switch statement.
	  void p_deverr(char error)
	  {
	     switch ( error )
	        {
	     case CURRENT_INPUT_DEVICE:
	        puts("Current input device.");
	        break;
	     case CURRENT_OUTPUT_DEVICE:
	        puts("Current output device.");
	        break;
	     case CURRENT_NULL_DEVICE:
	        puts("Current null device.");
	        break;
	     case CURRENT_CLOCK_DEVICE:
	        puts("Current clock device.");
	        break;
	     default:
	        puts("No error on default device.");
	        break;
	        }
	  }
	
	Additional query words: kbinf 1.00 1.50 5.10 6.00 6.00a 6.00ax 7.00
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbVCsearch kbAudDeveloper kbCRT
	Version           : winnt:
	
	=============================================================================
	

{% endraw %}
