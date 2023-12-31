# REXXTRY

    +--------------------------------------------------------------------+
    |                                                                    |
    |                  SAA-portable REXXTRY procedure                    |
    |                                                                    |
    +--------------------------------------------------------------------+


The purpose of this procedure is to provide an implementation of the
rexxtry concept that can be used on all IBM SAA systems that have a
REXX interpreter.  Further, it provides a simple example of the method
used to handle system-specific operations within a non-system-specific
framework.

The REXXTRY package is now available on the VMTOOLS repository.

This version is structured, SAA-portable, provides indented output,
and has consistent messages.  All of its subroutines can be called by
the user.

The tell subroutine highlights the features:

   three modes of operation...

      interactive           enter:  rexxtry alone
      one-line and exit     enter:  rexxtry and any strings
      tell                  enter:  rexxtry ?

   filespec independence    Rexxtry can be renamed.  It uses
                              parse source to get its name.

   'prev'  variable         Contains the previous line that was
                              entered by the user.

   recursion                Can be run recursively with CALL.
                              In CMS, EXEC also works.

   'save'  variable         Save user input with save=filespec.
                              Stop saving with save=''.  (null)
                              Rexxtry does a lineout to the file
                                of your choice before that line
                                is interpreted.

   'show'  subroutine       'call show' will display the current
                              values of the user variables that are
                              provided by rexxtry, including the
                              filled-in 'version' and 'source'
                              variables.

   'sub'   test subroutine  Can be CALLed or invoked as 'sub().
                              So can all the other subroutines, but
                                'sub' announces itself and does a
                                return 1234 for testing the RESULT
                                special variable.

   'trace' variable         Enter trace=i, trace=o etc. to control
                              tracing of user instructions.  Rexxtry
                              itself is not traced unless the user
                              CALLs or SIGNALs its subroutines.

   '=' operator             Enter '=' to repeat previous statement.

   '?' operator             Enter '?' to invoke system-provided online
                              help for REXX, if any is available.

   'more'  variable         For CMS only, after a syntax error, the
                              user can enter 'more' to see information
                              from REXX IOSLIB about this error code.

   prompting                For CMS only, after a syntax error, if the
                              PROMPT module is available, rexxtry will
                              put the user's input on the command line,
                              ready to be corrected and tried again.


Steve Stafford     March 23, 1991

IBM SAA REXX Development, Endicott, New York
