# CBT369
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 369 IS FROM PLANNING RESEARCH CORPORATION AND CONTAINS    *   FILE 369
//*           SEVERAL OF THEIR PROGRAMS.  THIS FILE IS IN IEBUPDTE  *   FILE 369
//*           SYSIN FORMAT.  FOR ADDITIONAL INFORMATION SEE THE     *   FILE 369
//*           MEMBER CALLED $$DOC AND $$NWKDOC                      *   FILE 369
//*                                                                 *   FILE 369
//*       ---------------------------------------------------       *   FILE 369
//*           DALE VICK:  UPDATED DSPACE COMMAND (JAN 1999)         *   FILE 369
//*            (THE REST OF THIS FILE IS FROM DICK SZIEDE)          *   FILE 369
//*                                                                 *   FILE 369
//*                 DALE VICK                                       *   FILE 369
//*                 USA GROUP, INC.                                 *   FILE 369
//*                 11100 USA PARKWAY                               *   FILE 369
//*                 MC: B131                                        *   FILE 369
//*                 FISHERS, IN 46038-9203                          *   FILE 369
//*                 WORK PHONE: (317) 578-6786                      *   FILE 369
//*                 E-MAIL:           DVICK@USAGROUP.COM            *   FILE 369
//*       ---------------------------------------------------       *   FILE 369
//*                                                                 *   FILE 369
//*    AC#VIOX  TITLE 'AC#VIOX -- ACF2 VIOLATION EXIT'              *   FILE 369
//*             ALLOWS A USER WITH "ACCOUNT" AUTHORITY TO           *   FILE 369
//*             CREATE AN ALIAS IN THE MASTER CATALOG, EVEN         *   FILE 369
//*             THOUGH HE DOESN'T HAVE "WRITE" PERMISSION.          *   FILE 369
//*             THE ROUTINE CHECKS THE ACF2 VIOLATION TO            *   FILE 369
//*             DETERMINE WHETHER IT IS FROM VSAM CATALOG           *   FILE 369
//*             MANAGEMENT.  IF SO, IT THEN CHECKS TO SEE           *   FILE 369
//*             WHETHER THE REQUEST IS TO DEFINE OR DELETE          *   FILE 369
//*             AN ALIAS.  IF YES, IT CHECKS TO SEE IF THE          *   FILE 369
//*             USER HAS ACCOUNT AUTHORITY.  IF ALL                 *   FILE 369
//*             CONDITIONS MATCH, THE ACCESS IS ALLOWED.            *   FILE 369
//*                                                                 *   FILE 369
//*    ACFFTSUB TITLE 'ACFFTSUB -- FILE TAILOR AND                  *   FILE 369
//*             AUTHORIZED JOB SUBMISSION'.  THIS ROUTINE           *   FILE 369
//*             PERFORMS THE FUNCTIONS OF ACF2'S ACFSUB             *   FILE 369
//*             PROGRAM.  THE MAIN REASON TO HAVE THIS IS TO        *   FILE 369
//*             PERMIT A USER TO SUBMIT A JOB WHICH WILL DO         *   FILE 369
//*             THINGS THE USER WOULD NORMALLY NOT BE               *   FILE 369
//*             PERMITTED TO DO.  (TYPICALLY, A DATA-CONTROL        *   FILE 369
//*             CLERK SUBMITTING THE FDR BACKUPS).  THIS            *   FILE 369
//*             ROUTINE EXTENDS ACFSUB TO ALLOW A FINAL STEP        *   FILE 369
//*             OF FILE TAILORING BY ISPF SERVICES PRIOR TO         *   FILE 369
//*             THE SUBMISSION WHILE MAINTAINING SECURITY           *   FILE 369
//*             OVER PRODUCTION AND MAINTENANCE JCL.                *   FILE 369
//*                                                                 *   FILE 369
//*             NORMALLY ACFSUB-LIKE ROUTINES WHICH ARE USED        *   FILE 369
//*             TO TRIGGER THE SUBAUTH LID ATTRIBUTE HAVE TO        *   FILE 369
//*             BE APF AUTHORIZED.  HOWEVER, THERE IS A             *   FILE 369
//*             RESTRICTION IN FORCE WITH ISPF/PDF V2R2M0           *   FILE 369
//*             AND TSO/E WHICH PROHIBITS ANY APF AUTHORIZED        *   FILE 369
//*             PROGRAM OR COMMAND PROCESSOR FROM USING ANY         *   FILE 369
//*             ISPF SERVICES.  THE SUBAUTHX EXIT, ALSO IN          *   FILE 369
//*             THIS FILE, IS NECESSARY TO GET AROUND THIS          *   FILE 369
//*             RESTRICTION.                                        *   FILE 369
//*                                                                 *   FILE 369
//*             THE USER SHOULD HAVE READ AUTHORITY FOR THE         *   FILE 369
//*             FILE TAILORING SKELETON LIBRARY.  WRITE             *   FILE 369
//*             ACCESS TO THESE LIBRARIES SHOULD BE                 *   FILE 369
//*             CONTROLLED.  ONLY PROPER JOBSTREAMS CAN BE          *   FILE 369
//*             SUBMITTED.  THE USER'S LEVEL OF MODIFICATION        *   FILE 369
//*             OF THE JOBSTREAMS IS LIMITED TO SETTING             *   FILE 369
//*             DIALOG VARIABLES FOR THE FILE TAILORING.            *   FILE 369
//*                                                                 *   FILE 369
//*    ADAEX2 - 'ADABAS USER EXIT 2.'                               *   FILE 369
//*             THIS IS THE ADABAS SWITCH LOG EXIT.  WE GET         *   FILE 369
//*             CONTROL FROM ADABAS WHEN A PROTECTION LOG OR        *   FILE 369
//*             COMMAND LOG SWITCH TAKES PLACE.  ADAEX2             *   FILE 369
//*             DUMPS THE LOGS AS REQUIRED, AND TELLS ADABAS        *   FILE 369
//*             TO GET ON WITH PROCESSING.  **NOTE** OUR            *   FILE 369
//*             ADABAS LOG-DUMP UTILITY JCL CALLS THE               *   FILE 369
//*             "REPLYTO" PROGRAM ALSO IN THIS FILE, TO GIVE        *   FILE 369
//*             ADABAS THE GO-AHEAD.                                *   FILE 369
//*                                                                 *   FILE 369
//*    ASMTOZAP - THE ORIGINAL HOWARD GILBERT VERSION.              *   FILE 369
//*             ACCEPT NO SUBSTITUTES!  THERE ARE OTHER             *   FILE 369
//*             ASMTOZAP PROGRAMS AROUND THAT WILL PRODUCE          *   FILE 369
//*             BAD ZAPS FROM THE CODE IN THIS FILE.                *   FILE 369
//*                                                                 *   FILE 369
//*             THIS IS A UTILITY WHICH CONVERTS AN                 *   FILE 369
//*             ASSEMBLER LISTING DATASET INTO A FORMATTED          *   FILE 369
//*             IMASPZAP INPUT DECK OR SMP PTF.  IT IS USEFUL       *   FILE 369
//*             IN PREPARING, MAINTAINING, AND DOCUMENTING          *   FILE 369
//*             THOSE INSTALLATION MODIFICATIONS WHICH              *   FILE 369
//*             CANNOT BE INSTALLED EXCEPT BY MODIFING IBM          *   FILE 369
//*             CODE.  ONE CAN MAKE FREE USE OF MACROS,             *   FILE 369
//*             LITERALS, AND OTHER CONVENIENCE FEATURES IN         *   FILE 369
//*             PREPARING THE DECK.  CONTROL CARDS IN SPECIAL       *   FILE 369
//*             ASSEMBLER COMMENT FORM PROVIDE FLEXIBILITY          *   FILE 369
//*             IN MODIFICATION DESIGN AND CONTROL OVER             *   FILE 369
//*             OUTPUT.                                             *   FILE 369
//*                                                                 *   FILE 369
//*    AUTOIPL  TITLE    'A U T O M A T I C   I P L'                *   FILE 369
//*             THIS PROGRAM ISSUES OPERATOR COMMANDS READ          *   FILE 369
//*             FROM AN INPUT FILE.  IT ALLOWS CONDITIONAL          *   FILE 369
//*             COMMAND EXECUTION, TIMED COMMAND SUBMISSION,        *   FILE 369
//*             AND PROGRAM INVOCATION.  THESE FUNCTIONS            *   FILE 369
//*             PERMIT THE PROGRAM TO BE USED FOR A FULLY           *   FILE 369
//*             AUTOMATED IPL PROCEDURE FOR THE SYSTEM.             *   FILE 369
//*                                                                 *   FILE 369
//*    BITENCOD TITLE ENCODE OR DECODE BITS INTO BYTES              *   FILE 369
//*             PROVIDES BIT TESTING AND BIT SETTING FOR            *   FILE 369
//*             HIGH-LEVEL LANGUAGES                                *   FILE 369
//*                                                                 *   FILE 369
//*             BITENCOD: THIS SUBROUTINE TAKES A SINGLE            *   FILE 369
//*                       CHARACTER ARGUMENT OF ONE BYTE,           *   FILE 369
//*                       AND RETURNS EIGHT CHARACTERS OF           *   FILE 369
//*                       ONES OR ZEROS DEPENDING ON THE            *   FILE 369
//*                       BITS SET IN THE ARGUMENT.                 *   FILE 369
//*                                                                 *   FILE 369
//*             BITDECOD: THIS SUBROUTINE TAKESS EIGHT              *   FILE 369
//*                       CHARACTERS OF DATA AND RETURNS A          *   FILE 369
//*                       SINGLE BYTE, THE BITS OF WHICH ARE        *   FILE 369
//*                       THE RIGHTMOST BITS OF EACH                *   FILE 369
//*                       ARGUMENT BYTE.  THUS IS THE               *   FILE 369
//*                       OPPOSITE OF BITENCODE.                    *   FILE 369
//*                                                                 *   FILE 369
//*    CALENDAR - PRINT A CUSTOM CALENDAR FOR ANY YEAR:             *   FILE 369
//*               BIRTHDAYS, HOLIDAYS, AND EVENTS TO YOUR           *   FILE 369
//*               ORDER.                                            *   FILE 369
//*                                                                 *   FILE 369
//*    CLIB   --- CONCATENATE DATASET FIRST TO DDNAME.              *   FILE 369
//*             PURPOSE:  PROVIDE TSO USER QUICK ACCESS TO          *   FILE 369
//*                      PRIVATE CLISTS.                            *   FILE 369
//*             METHOD:  USE SVC 99 TO DETERMINE THE DSNAMES        *   FILE 369
//*                      OF ALL DATASETS CONCATENATED TO A          *   FILE 369
//*                      PARTICULAR DDNAME.  REALLOCATE THE         *   FILE 369
//*                      ARGUMENT DSNAME IN FRONT OF ALL THE        *   FILE 369
//*                      OTHERS.                                    *   FILE 369
//*                                                                 *   FILE 369
//*    COMMAND  TITLE 'COMMAND - ISSUE SVC34 FOR PROBLEM            *   FILE 369
//*             PROGRAM'.  ALLOW COMMANDS TO BE ISSUED BY           *   FILE 369
//*             PROGRAM CONTROL EITHER THROUGH THE PARM             *   FILE 369
//*             FIELD OR BY A CALL FROM ANOTHER PROGRAM.            *   FILE 369
//*             NOT FULLY OPERATIONAL, BUT REQUIRED BY SPY.         *   FILE 369
//*                                                                 *   FILE 369
//*    DSNPOST  TITLE 'DSNPOST - ACF2 DSN POST-PROCESSING           *   FILE 369
//*              EXIT.' THIS IS AN ACF2 DSN POST-PROCESSING         *   FILE 369
//*              EXIT.  WE USE THIS EXIT TO OVERRIDE A              *   FILE 369
//*              PARTICULAR VIOLATION.  WE ATTEMPTED TO LIMIT       *   FILE 369
//*              ACCESS TO THE JES2 SPOOL AND CHECKPOINT            *   FILE 369
//*              DATASETS FROM SDSF VIA ACF2'S PROGRAM PATHING      *   FILE 369
//*              FACILITY, BUT THE LIMITATIONS OF THIS              *   FILE 369
//*              FACILITY ESPECIALLY WITHIN ISPF DIALOGS            *   FILE 369
//*              BECAME EVIDENT (YOU HAVE TO ACCURATELY             *   FILE 369
//*              DESCRIBE THE TASK AND RB CHAINS FOR EVERY          *   FILE 369
//*              DIALOG THAT WILL BE USED).  THUS WE ATTEMPT TO     *   FILE 369
//*              OVERRIDE VIOLATIONS AGAINST THE JES2 DATASETS      *   FILE 369
//*              THAT ARE REALLY NORMAL SDSF ACCESSES.  WE          *   FILE 369
//*              CHECK FOR OPEN FOR INPUT ACCESSES TO FILES         *   FILE 369
//*              HASPCKPT OR HASPAC00, AND THEN CHECK FOR THE       *   FILE 369
//*              PRESENCE OF AN AUTHORIZED LIBRARY VERSION OF       *   FILE 369
//*              ISFJINIT.                                          *   FILE 369
//*                                                                 *   FILE 369
//*    DSPACE   -- LIST DISK FREESPACE AND EXTENTS.                 *   FILE 369
//*              THIS IS THE GOOD OL' SHARE DSPACE COMMAND          *   FILE 369
//*              WITH CLEARER FIELD LABELS, AND USING               *   FILE 369
//*              PUTLINE INSTEAD OF TPUT SO IT CAN BE RUN           *   FILE 369
//*              FROM A CLIST.  THIS COMMAND IS USED BY             *   FILE 369
//*              PARKE'S FULL-SCREEN "FDSPACE" PANELS.              *   FILE 369
//*                                                                 *   FILE 369
//*    DOPROG  -- DOPROG/DOCP  (TSO) COMMAND PROCESSOR              *   FILE 369
//*              DOPROG AND DOCP IN THE SAME MODULE.   USE          *   FILE 369
//*              TO INVOKE A COMMAND PROCESSOR.  HAS A              *   FILE 369
//*              "TASKLIB" CAPABILITY.  THIS ISN'T JOE              *   FILE 369
//*              SCHINDLER'S "DOCP," WHICH IS A STAND-ALONE         *   FILE 369
//*              CP, RATHER, AN ALIAS OF DOPROG.  JOE USED          *   FILE 369
//*              TPUT-TGET TO PROMPT FOR THE COMMAND LINE,          *   FILE 369
//*              WHICH I DIDN'T LIKE.  THIS VERSION WILL            *   FILE 369
//*              TAKE A CP COMMAND LINE IN QUOTES, OR WILL          *   FILE 369
//*              PROMPT WITH PUTGET IF IT DOESN'T FIND ONE.         *   FILE 369
//*              THUS IT CAN BE USED IN A CLIST.                    *   FILE 369
//*                                                                 *   FILE 369
//*    DSIEX04 - NCCF'S OWN LOGGING FACILITY IS PRETTY              *   FILE 369
//*              USELESS.  THIS EXIT PROVIDES AN                    *   FILE 369
//*              ALTERNATIVE.  WE GET A LOOKSEE AT ALL NCCF         *   FILE 369
//*              TERMINAL INPUTS AND OUTPUTS BEFORE NCCF            *   FILE 369
//*              DOES ITS OWN LOGGING.  WE DECIDE WHAT'S            *   FILE 369
//*              IMPORTANT AND WRITE IT FOR POSTERITY.              *   FILE 369
//*              YOU'LL PROBABLY WANT TO SUPPRESS MSGID             *   FILE 369
//*              NCCF/ IN YOUR MVS/XA MPF LIST.  NOTE THAT          *   FILE 369
//*              DSILOG TASK MUST BE ACTIVE FOR THIS EXIT TO        *   FILE 369
//*              BE INVOKED.                                        *   FILE 369
//*                                                                 *   FILE 369
//*    DSNWAIT  TITLE 'DSNWAIT - WTO EXIT TO INFORM TSO USER        *   FILE 369
//*             OF DSN WAIT.'                                       *   FILE 369
//*                                                                 *   FILE 369
//*             NAME - DSNWAIT - WTO EXIT TO INFORM A TSO USER      *   FILE 369
//*             THAT JOB IS WAITING FOR A DATASET.                  *   FILE 369
//*                                                                 *   FILE 369
//*             DESCRIPTION -                                       *   FILE 369
//*             WE GET CONTROL UPON ISSUANCE OF THE IEF099I         *   FILE 369
//*             WTO.  WE ISSUE AN OPERATOR SEND COMMAND TO          *   FILE 369
//*             INFORM THE TSO USER THAT HIS BATCH JOB IS           *   FILE 369
//*             WAITING FOR SOME DATASETS.  THE INTENT HERE         *   FILE 369
//*             IS TO ALERT THE PERSON WHO CAN DO SOMETHING         *   FILE 369
//*             ABOUT THE SITUATION, SUCH AS FREE THE               *   FILE 369
//*             DATASETS.  WE FIRST MAKE SURE THAT MSG              *   FILE 369
//*             IEF099I WAS ISSUED, THAT ACF2 IS ALIVE AND          *   FILE 369
//*             WELL, THAT WE'RE A JOB, AND THAT THE RESULTS        *   FILE 369
//*             OF OUR GQSCAN REQUEST FOR SYSDSN CONFLICTS IS       *   FILE 369
//*             COOL.  THEN WE ISSUE A SEND COMMAND FOR THE         *   FILE 369
//*             FIRST THREE CONFLICTS THAT MEET THE FOLLOWING       *   FILE 369
//*             CONDITIONS:                                         *   FILE 369
//*                                                                 *   FILE 369
//*              1). 1 TASK HOLDS THE RESOURCE.                     *   FILE 369
//*              2). 1 TASK WAITS FOR THE RESOURCE.                 *   FILE 369
//*              3). WE ARE THE TASK THE WAITS FOR THE              *   FILE 369
//*                  RESOURCE.                                      *   FILE 369
//*              4). IT IS A TSO USER THAT HOLDS THE                *   FILE 369
//*                  RESOURCE.                                      *   FILE 369
//*              5). THE ACF2 LIDS FOR THE HOLDER AND WAITER        *   FILE 369
//*                  ARE THE SAME.                                  *   FILE 369
//*                                                                 *   FILE 369
//*            WHILE IT IS ACKNOWLEDGED THAT THESE CRITERIA         *   FILE 369
//*            WILL ELIMINATE SOME OTHERWISE VALID CANDIDATES       *   FILE 369
//*            FROM CONSIDERATION, IT IS HOPED THAT THIS EXIT       *   FILE 369
//*            WILL OTHERWISE PROVE USEFUL IN MOST                  *   FILE 369
//*            SITUATIONS.                                          *   FILE 369
//*                                                                 *   FILE 369
//*          NOTE - WE MUST BE IN AN APF-AUTHORIZED LINKLIST        *   FILE 369
//*            LIBRARY.  THE ACF2 SECURITY SYSTEM IS                *   FILE 369
//*            REQUIRED BY THIS EXIT.                               *   FILE 369
//*                                                                 *   FILE 369
//*          TO USE -                                               *   FILE 369
//*            SPECIFY IN AN MPFLSTXX MEMBER OF PARMLIB:            *   FILE 369
//*            IEF099I,SUP(NO),USEREXIT(DSNWAIT)                    *   FILE 369
//*                                                                 *   FILE 369
//*    ENQWAIT  TITLE 'ENQWAIT - STIMER UNTIL SOMEONE ELSE          *   FILE 369
//*              GETS AN ENQ.'                                      *   FILE 369
//*                                                                 *   FILE 369
//*              THIS PROGRAM WORKS IN CONJUNCTION WITH THE         *   FILE 369
//*              AUTOIPL PROGRAM.  WE STIMER UNTIL A TARGET         *   FILE 369
//*              JOB ACQUIRES A TARGET RESOURCE VIA AN ENQ          *   FILE 369
//*              REQUEST.  THUS WE CAN ENSURE THAT AUTOIPL          *   FILE 369
//*              WILL NOT PROCEED UNTIL A PREVIOUS PROCESS          *   FILE 369
//*              IS READY FOR PROCESSING.                           *   FILE 369
//*                                                                 *   FILE 369
//*              FOR EXAMPLE, CONSIDER THE FOLLOWING AUTOIPL        *   FILE 369
//*                INPUT:                                           *   FILE 369
//*                                                                 *   FILE 369
//*                S TPJOB,M=TCAM                                   *   FILE 369
//*                                                                 *   FILE 369
//*                "ENQWAIT "JOB=TCAM,MAJOR=AUTOTCAM                *   FILE 369
//*                                                                 *   FILE 369
//*                S MESS,M=                                        *   FILE 369
//*                                                                 *   FILE 369
//*              THE "S MESS,M=" COMMAND WILL NOT PROCEED           *   FILE 369
//*              UNTIL TCAM ACQUIRES THE RESOURCE WHOSE             *   FILE 369
//*              MAJOR NAME IS AUTOTCAM.  WE STIMER EVERY 10        *   FILE 369
//*              SECONDS FOR 5 MINUTES TO CHECK ON STATUS.          *   FILE 369
//*              IF ANYTHING IS FOUND THAT IS UNGOOD, WE            *   FILE 369
//*              ABEND WITH A S0C3.                                 *   FILE 369
//*                                                                 *   FILE 369
//*            TO USE -                                             *   FILE 369
//*                                                                 *   FILE 369
//*         EXEC PGM=ENQWAIT,PARM='JOB=JJJJJJJJ,MAJOR=MMMMMMMM,     *   FILE 369
//*                               MINOR=RRRRRRRR,NAME=NNNNNNNN      *   FILE 369
//*       WHERE JJJJJJJJ = TARGET JOBNAME (1-8 CHARS),              *   FILE 369
//*             MMMMMMMM = TARGET MAJOR NAME (1-8 CHARS),           *   FILE 369
//*             RRRRRRRR = TARGET MINOR NAME (1-44 CHARS),          *   FILE 369
//*             NNNNNNNN = DESCRIPTIVE NAME FOR MSG (1-8 CHARS).    *   FILE 369
//*           * = REQUIRED                                          *   FILE 369
//*                                                                 *   FILE 369
//*    FSAS    - A FULL SCREEN SAS FACILITY THAT USES THE           *   FILE 369
//*              ISPF EDITOR.  NEEDS PANELS, CLISTS,                *   FILE 369
//*              MESSAGES AND CODE FOUND IN THIS PDS, THAT          *   FILE 369
//*              START FSAS....   ALSO NEEDS THE CLIST              *   FILE 369
//*              SELMEMBR, AND THE PANEL SELMEMP1.                  *   FILE 369
//*                                                                 *   FILE 369
//*    HEX   TITLE ' BASE 16 ARITHMETIC ' FOR THOSE WHO             *   FILE 369
//*              HAVEN'T BLOWN THE $15 FOR A CASIO CM-100,          *   FILE 369
//*              HERE'S A LITTLE HELP.  THE IMPETUS FOR             *   FILE 369
//*              WRITING THIS PROGRAM COMES FROM THOSE              *   FILE 369
//*              FRUSTRATING HOURS SPENT FUMBLING WITH A            *   FILE 369
//*              DUMP ONLY TO DISCOVER THAT MY INABILITY TO         *   FILE 369
//*              FIND A SOLUTION STEMS FROM AN ARITHMETIC           *   FILE 369
//*              ERROR IN THE INITIAL STEPS.                        *   FILE 369
//*                                                                 *   FILE 369
//*    IGC0022F TITLE 'IGC0022F,SVC 226, WRITE USER SMF             *   FILE 369
//*              RECORD' WRITE USER SMF RECORD FROM NON             *   FILE 369
//*              APF-AUTHORIZED PROGRAM.  TYPICALLY, THE            *   FILE 369
//*              RECORD CONTAINS ACCOUNTING DATA FROM SUCH          *   FILE 369
//*              PACKAGES AS TELAGRAF, THAT REQUIRE THEIR           *   FILE 369
//*              OWN ACCOUNTING DATA.  THE CALLER MUST              *   FILE 369
//*              PROVIDE A POINTER TO THE SMF RECORD IN             *   FILE 369
//*              REGISTER ONE.  SVC226 WILL VALIDATE THE            *   FILE 369
//*              ARGUMENTS, FILL IN THE STANDARD SMF HEADER         *   FILE 369
//*              AND DISPATCH THE RECORD WITH A SMFWTM              *   FILE 369
//*              MACRO.                                             *   FILE 369
//*                                                                 *   FILE 369
//*    IEFACTRT TITLE 'SMF JOB/STEP TERMINATION EXIT ROUTINE'       *   FILE 369
//*                SMF EXIT ROUTINE PUTS JOB SUMMARY                *   FILE 369
//*              MESSAGES ON THE JOB LOG WITH STEP                  *   FILE 369
//*              TERMINATION STATUS.  THIS IS THE SP IPO            *   FILE 369
//*              EXIT, DIDDLED TO WORK UNDER XA.                    *   FILE 369
//*                                                                 *   FILE 369
//*    IEFUSI   'MEMLIMIT - IEFUSI EXIT TO SET REGION AND           *   FILE 369
//*              GETMAIN PARAMETERS AVOID 40D ABENDS WHEN           *   FILE 369
//*              USING A REGION GREATER THAN 32 MEG.  SET           *   FILE 369
//*              LIMITS FOR REGION AND GETMAINS.  THE IEFUSI        *   FILE 369
//*              LIMIT FLAG IS SET ON IN THE VSM PARAMETER          *   FILE 369
//*              LIST.  THIS ENABLES VSM LOGIC TO SET REGION        *   FILE 369
//*              AND GETMAIN LIMITS.  NO SPECIFIC VALUES ARE        *   FILE 369
//*              SET.  THIS EXIT ADDRESSES A PROBLEM WHICH          *   FILE 369
//*              CAUSES ADDRESS SPACES TO FAIL WHEN A V-FORM        *   FILE 369
//*              GETMAIN IS ISSUED WHICH GETS THE ENTIRE            *   FILE 369
//*              PRIVATE AREA BELOW THE 16M LINE.  ITS              *   FILE 369
//*              PURPOSE IS TO RESERVE FOR SYSTEM USE (E.G.,        *   FILE 369
//*              ABTERM) A REASONABLE AMOUNT OF STORAGE.            *   FILE 369
//*                                                                 *   FILE 369
//*    IKJEFF10 TITLE 'IKJEFF10 - TSO/E SUBMIT EXIT                 *   FILE 369
//*             ROUTINE.'  WE USE THIS EXIT TO INSERT A             *   FILE 369
//*             COMMENT CARD AFTER EACH JOB CARD THAT NAMES         *   FILE 369
//*             THE JCL SOURCE DATASET.  THUS:                      *   FILE 369
//*                                                                 *   FILE 369
//*               //* SUBMITTED FROM ISPF EDIT OF                   *   FILE 369
//*               USERID.TEST.CNTL(IEFBR14)                         *   FILE 369
//*                                                                 *   FILE 369
//*             THIS ALLOWS THE DEBUGGER TO RELATE A JCL            *   FILE 369
//*             LISTING BACK TO THE LIBRARY FROM WHICH THE          *   FILE 369
//*             JOB WAS SUBMITTED.                                  *   FILE 369
//*                                                                 *   FILE 369
//*    IKJEFF53 TITLE ' FIB INSTALLATION EXIT' VALIDITY             *   FILE 369
//*             CHECKS JOBNAME ON A CANCEL, OUTPUT OR STATUS        *   FILE 369
//*             FIB (FOREGROUND INITIATED BACKGROUND)               *   FILE 369
//*             COMMAND.  USES AN ACF2 GENERALIZED RESOURCE         *   FILE 369
//*             RULE TEST, SO THE ACCESS RULES CAN BE               *   FILE 369
//*             CHANGED WITH ACF2 COMMANDS INSTEAD OF               *   FILE 369
//*             REASSEMBLY AND RELOAD OF IKJEFF53.                  *   FILE 369
//*                                                                 *   FILE 369
//*    ISPFPRTO TITLE 'PRINTOFF SUBCOMMAND OF BROWSE & EDIT         *   FILE 369
//*             ' THIS CLIST, PLUS AN ENTRY IN THE ISPTLIB          *   FILE 369
//*             MEMBER, "ISPCMDS," WILL PRINT THE DATASET           *   FILE 369
//*             BEING BROWSED OR EDITED.  THUS: COMMAND ==>         *   FILE 369
//*             PRINTO INSTEAD OF:  COMMAND ==> TSO PRINTO          *   FILE 369
//*             ENDLESS.GODDAM.DATASET.NAME NEEDS ISRBROBF          *   FILE 369
//*             AND ISREDDE REPLACEMENT PANELS IN THIS PDS.         *   FILE 369
//*                                                                 *   FILE 369
//*    ISFUSER  SDSF - ACF2 INTERFACE                               *   FILE 369
//*             WITH THIS INTERFACE, SDSF AND OUTPUT OBEY           *   FILE 369
//*             THE SAME RULES -- WHO CAN DO WHAT, AND WITH         *   FILE 369
//*             WHICH, AND TO WHOM?  IKJEFF53 AND ISFUSER           *   FILE 369
//*             BOTH CHECK THE SAME ACF2 GRO RULES.                 *   FILE 369
//*                                                                 *   FILE 369
//*    ISRPID TITLE 'ISRPID - FETCH THE CURRENT ISPF PANELID.'      *   FILE 369
//*             THIS ROUTINE RUNS UNDER THE ISPF DIALOG             *   FILE 369
//*             MANAGER AND RETURNS THE NAME OF THE CURRENT         *   FILE 369
//*             PANEL IN DIALOG VARIABLE PANELID.  IT WAS           *   FILE 369
//*             DESIGNED FOR USE BY THE PRINTO SUBCOMMAND OF        *   FILE 369
//*             EDIT AND BROWSE, ALSO IN THIS FILE.                 *   FILE 369
//*                                                                 *   FILE 369
//*    ISRUOL   A FULL SCREEN 3.8 REPLACEMENT THAT ALLOWS           *   FILE 369
//*             MANIPULATION OF JOBS/SYSOUT WITHOUT THE HASSLE      *   FILE 369
//*             OF AWKWARD "JOB(JOBNUM)" SPECIFICATIONS.            *   FILE 369
//*             REQUIRES TSO/E.                                     *   FILE 369
//*                                                                 *   FILE 369
//*    ISRUDLP  ISPF 3.4 MOD                                        *   FILE 369
//*             DEFAULTS TO SEARCH UNDER YOUR USERID.  THUS         *   FILE 369
//*             "=3.4;;" WILL DISPLAY WHAT YOU GET WITH,            *   FILE 369
//*             "=3.4 **ENTER** **TAB** MYUSERID **ENTER**".        *   FILE 369
//*             THIS PANEL ALSO HAS MODS TO SUPPORT BEING           *   FILE 369
//*             CALLED AS A LINE COMMAND FROM FDSPACE.              *   FILE 369
//*                                                                 *   FILE 369
//*    ISTAUCAG TITLE 'VTAM SESSION ACCOUNTING EXIT ROUTINE.'       *   FILE 369
//*             DESCRIPTION - THIS EXIT IS DOCUMENTED IN THE        *   FILE 369
//*             ACF/VTAM CUSTOMIZATION MANUAL (SC27-0613).  WHAT    *   FILE 369
//*             WE DO IN THIS EXIT IS BANG OUT AN SMF RECORD        *   FILE 369
//*             (TYPE 240) THAT CONTAINS ALL RELEVANT               *   FILE 369
//*             INFORMATION PASSED TO US.  THIS INCLUDES            *   FILE 369
//*             PRIMARY AND SECONDARY LU NAMES.  RECORD IS          *   FILE 369
//*             IN RELOCATE FORMAT (SECTIONS WITH A HEADER          *   FILE 369
//*             CONTAIN OFFSET, LENGTH, AND NUMBER).  PLEASE        *   FILE 369
//*             NOTE THAT THE RECORD IS IN A FORMAT COMPATIBLE      *   FILE 369
//*             WITH THE VECTORS THAT WILL BE OUTPUT BY THE         *   FILE 369
//*             VTAM SESSION MANAGEMENT EXIT ROUTINE WE WILL        *   FILE 369
//*             USE WHEN VTAM 2.2 IS IMPLEMENTED.                   *   FILE 369
//*                                                                 *   FILE 369
//*    JESXIT9 - TITLE 'JES2 EXIT9 - OUTPUT EXCEEDED EXIT.'         *   FILE 369
//*        DESCRIPTION -                                            *   FILE 369
//*             THIS IS THE OUTPUT EXCEEDED JES EXIT.  OUR          *   FILE 369
//*             INSTALLATION DOES NOT BY DEFAULT CANCEL JOBS        *   FILE 369
//*             THAT EXCEED OUTPUT.  THIS EXIT PROMPTS THE          *   FILE 369
//*             OPERATOR ABOUT EVERY 100,000 LINES EXCEEDED TO      *   FILE 369
//*             CANCEL THE JOB OR ALLOW THE JOB TO CONTINUE.        *   FILE 369
//*             THUS WE CAN PREVENT RUNAWAY JOBS FROM FILLING       *   FILE 369
//*             UP SPOOL SPACE.                                     *   FILE 369
//*                                                                 *   FILE 369
//*    LM00501  FORCE JES2 TO RELOAD 6-LPI FCB AFTER 8-LPI          *   FILE 369
//*             DATASET PRINTS.  JES2 WILL ONLY RELOAD THE          *   FILE 369
//*             3211 FCB WITH A STANDARD FCB, IF THE CURRENT        *   FILE 369
//*             LOAD IS MARKED NON-STANDARD.  THIS MEANS, A         *   FILE 369
//*             JOB THAT DOESN'T SPECIFY A FCB WILL PRINT AT        *   FILE 369
//*             THE DENSITY OF THE PRECEDING DATASET,               *   FILE 369
//*             WHATEVER IT MAY BE.  THE SOLUTION IS TO             *   FILE 369
//*             LEAVE ONLY THE 6-LPI FCB MARKED STANDARD.           *   FILE 369
//*                                                                 *   FILE 369
//*    LM01602  TITLE 'LM01602 -- I/O COUNTS IN DEALLOCATION        *   FILE 369
//*             MESSAGES'                                           *   FILE 369
//*                                                                 *   FILE 369
//*                IEF285I SYS1.DATASET        KEPT *----2,301      *   FILE 369
//*                                                                 *   FILE 369
//*             I/O COUNT IN MSGS IEF283I, IEF285I, IEF287I         *   FILE 369
//*             UPDATED FOR XA.  IEFAB4B0 AT JBB2110,               *   FILE 369
//*             IEFAB4A2 AT JBB2125 ADDED LOOP TO SUM UP            *   FILE 369
//*             COUNTS WHEN MULTIPLE UNITS ARE ALLOCATED.           *   FILE 369
//*             ENHANCED TO SHOW COUNTS FOR VIO DATASETS.           *   FILE 369
//*                                                                 *   FILE 369
//*             NOTE: THIS ZAP DEPENDS ON THE HOWARD GILBERT        *   FILE 369
//*                  ASMTOZAP, ALSO IN THIS FILE.  ACCEPT NO        *   FILE 369
//*                  SUBSTITUTES.                                   *   FILE 369
//*                                                                 *   FILE 369
//*    LM02701  TITLE 'ZAP TO IGG01946 FOR TCAM OPENQ SMF           *   FILE 369
//*             RECORD.'                                            *   FILE 369
//*                                                                 *   FILE 369
//*    LM02801  TITLE 'ZAP TO IGG02046 FOR TCAM CLOSEQ SMF          *   FILE 369
//*             RECORD.'  DESCRIPTION - THESE TWO ZAPS WRITE        *   FILE 369
//*             AN SMF240 RECORD FOR EACH OPEN OR CLOSE OF A        *   FILE 369
//*             TCAM APPLICATION Q.                                 *   FILE 369
//*                                                                 *   FILE 369
//*             NOTE: THIS ZAP DEPENDS ON THE HOWARD GILBERT        *   FILE 369
//*                  ASMTOZAP, ALSO IN THIS FILE.  ACCEPT NO        *   FILE 369
//*                  SUBSTITUTES.                                   *   FILE 369
//*                                                                 *   FILE 369
//*    NONDESC  TITLE 'NONDESC - WTO EXIT TO MAKE ACTION            *   FILE 369
//*             MESSAGES ROLLABLE DESCRIPTION - IF EITHER           *   FILE 369
//*             DESC=1 OR DESC=2 FLAGS ARE ON, WE TURN THEM         *   FILE 369
//*             OFF, MAKING THE MESSAGE ROLLABLE.  THIS EXIT        *   FILE 369
//*             WAS ORIGINALLY DESIGNED TO MAKE SELECTED            *   FILE 369
//*             GARBAGE MESSAGES FROM PROPRIETARY SOFTWARE,         *   FILE 369
//*             ROLLABLE.  THIS EXIT IS WELL DOCUMENTED IN          *   FILE 369
//*             THE USER EXITS SPL, GC28-1147.                      *   FILE 369
//*                                                                 *   FILE 369
//*    PRCJFCB  TITLE 'PRCJFCB -- READ JOB-FILE CONTROL             *   FILE 369
//*             BLOCK'  PURPOSE:  THIS SUBROUTINE MOVES THE         *   FILE 369
//*             JOB-FILE CONTROL BLOCK FOR A CALLER INTO AN         *   FILE 369
//*             AREA ACCESSIBLE FROM HIGH-LEVEL LANGUAGE.           *   FILE 369
//*                                                                 *   FILE 369
//*    PRC38DSN TITLE  'STORE THE DSN FOR A DDNAME IN A             *   FILE 369
//*             DIALOG VARIABLE.'  THIS ROUTINE RUNS UNDER          *   FILE 369
//*             CONTROL OF THE ISPF DIALOG MANAGER.  GIVEN          *   FILE 369
//*             AN ALLOCATED DDNAME VIA THE PARM FIELD, WE          *   FILE 369
//*             RETURN THE DSN AND VOLSER IN DIALOG                 *   FILE 369
//*             VARIABLES OUTDSN AND OUTVOL.  DESIGNED FOR          *   FILE 369
//*             USE IN THE PRC 3.8 REPLACEMENT CLISTS SO WE         *   FILE 369
//*             CAN USE VIO FOR OUR TEMPORARY FILES.                *   FILE 369
//*                                                                 *   FILE 369
//*               ISPEXEC SELECT PGM(PRC38DSN) PARM(DDNAME)         *   FILE 369
//*               ISPEXEC VGET (OUTDSN OUTVOL)                      *   FILE 369
//*                                                                 *   FILE 369
//*    PRINTSEP TITLE  'APS JES2 EXITS: CUSTOM PRINTER BANNER       *   FILE 369
//*             SEPARATOR PAGE' CUSTOM PRINT SEPARATOR EXIT         *   FILE 369
//*             ROUTINES.  PUTS ACF2 UID OF JOB OWNER IN            *   FILE 369
//*             BANNER, AS WELL AS JOB NAME.                        *   FILE 369
//*                                                                 *   FILE 369
//*             1.  ENTRY SEPEX1 IS TO BE INVOKED AT                *   FILE 369
//*                 STANDARD JES2 EXIT 1.                           *   FILE 369
//*             2.  ENTRY SEPEX222 IS TO BE INVOKED AT              *   FILE 369
//*                 ACF2-GENERATED JES2 EXIT 222 BEFORE THE         *   FILE 369
//*                 STANDARD ACF2X2J2 FUNCTION.                     *   FILE 369
//*             3.  THE ACF2 LOGON ID IS PASSED IN 8 BYTES          *   FILE 369
//*                 OF JCTUSER.  CURRENTLY WE'RE USING THE 8        *   FILE 369
//*                 BYTES FOLLOWING WHATEVER FIELD ACF2 IS          *   FILE 369
//*                 USING.                                          *   FILE 369
//*             4.  THE LOGOS ARE IN LOWER CASE.  TAKE CARE         *   FILE 369
//*                 WITH THE EDITOR IF YOU MAKE CHANGES.            *   FILE 369
//*                                                                 *   FILE 369
//*    QALLOC - ALLOCATE A TCAM QUEUE.                              *   FILE 369
//*      DESCRIPTION - WE DRIVE THE DYNAM PGM TO ALLOCATE A         *   FILE 369
//*             TCAM Q FROM TSO.  PLEASE NOTE THAT THE ALLOCATE     *   FILE 369
//*             COMMAND DOES NOT SUPPORT THIS.  CALL                *   FILE 369
//*             'MY.LOAD.LIB(QALLOC)' 'DD=SYSUT1 QNAME=MYQNAME      *   FILE 369
//*             OPTCD=C ;'  PLEASE NOTE THAT THE PARM FIELD IS      *   FILE 369
//*             PASSED UNEDITED TO THE DYNAM PGM.  DON'T FORGET     *   FILE 369
//*             THE ';' TO TERMINATE IT!                            *   FILE 369
//*                                                                 *   FILE 369
//*             THE DYNAM PROGRAM FROM THE UNIVERSITY OF MANITOBA   *   FILE 369
//*             IS ON SEVERAL CBT FILES.  I BELIEVE OURS CAME FROM  *   FILE 369
//*             CBT FILE 360.  (FILE 089 IS DEVOTED TO DYNAM.  SG)  *   FILE 369
//*                                                                 *   FILE 369
//*    QFLUSH - FLUSH A TCAM QUEUE.                                 *   FILE 369
//*      DESCRIPTION - THIS UTILITY FLUSHES RECORDS FROM A          *   FILE 369
//*             TCAM INPUT QUEUE THAT IS ALLOCATED TO THE SYSUT1    *   FILE 369
//*             FILE.  IT WRITES THESE RECORDS TO THE SYSUT2 FILE   *   FILE 369
//*             IF IT'S FOUND ALLOCATED.  THIS PGM CAN BE RUN       *   FILE 369
//*             FROM THE OPERATOR CONSOLE WHEN A QUEUE IS FOUND     *   FILE 369
//*             TO BE CLOGGED UP WITH MESSAGES.                     *   FILE 369
//*      TO USE -                                                   *   FILE 369
//*                                                                 *   FILE 369
//*        //QFLUSH PROC Q=BADQNAME,TCAM=TCAM,OUTDSN=NULLFILE       *   FILE 369
//*        //S1     EXEC PGM=QFLUSH                                 *   FILE 369
//*        //SYSUT1 DD   QNAME=&Q..&TCAM                            *   FILE 369
//*        //SYSUT2 DD   DSN=&OUTDSN,DISP=(,CATLG,DELETE),          *   FILE 369
//*        // SPACE=(TRK,(10,5),RLSE),DCB=(RECFM=VB,LRECL=4024,     *   FILE 369
//*        // BLKSIZE=23200),UNITS=SYSTS                            *   FILE 369
//*                                                                 *   FILE 369
//*       THE OPERATOR CAN ENTER: "S QFLUSH,Q=MYQUEUE"  (CVT)       *   FILE 369
//*                                                                 *   FILE 369
//*                       FLUSH,Q=MYQUEUE,TCAM=MYTCAM"  (ASCB)      *   FILE 369
//*                                                                 *   FILE 369
//*    RECEIVED TITLE 'RECEIVE NOTIFY EXIT'                         *   FILE 369
//*             FUNCTION     PROVIDE NOTIFICATION OF                *   FILE 369
//*                          RECEIVED MESSAGE.                      *   FILE 369
//*                                                                 *   FILE 369
//*    REPLYTO - 'RESPOND TO AN OUTSTANDING WTOR.'  THIS            *   FILE 369
//*             PROGRAM WILL ISSUE A CANNED REPLY TO A SELECTED     *   FILE 369
//*             WTOR MESSAGE.  WE USE IT TO SYNCH PROCESSING        *   FILE 369
//*             BETWEEN ADABAS AND THE ADABAS LOG UTILITY.  IT      *   FILE 369
//*             ACCEPTS AS INPUT THE WTOR MESSAGE TEXT, THE         *   FILE 369
//*             CANNED REPLY MESSAGE TEXT, AND OPTIONALLY THE       *   FILE 369
//*             JOBNAME OF THE WTOR ISSUER, ALONG WITH OTHER        *   FILE 369
//*             MISC. OPTIONS, AS DESCRIBED BELOW.                  *   FILE 369
//*                                                                 *   FILE 369
//*       (FIXED BY ALAN FIELD AND ED BILLOWITZ TO HANDLE           *   FILE 369
//*        4-CHARACTER REPLY IDS.   SG-10/98)                       *   FILE 369
//*                                                                 *   FILE 369
//*        FOR EXAMPLE, THE FOLLOWING JOB STEP:                     *   FILE 369
//*                                                                 *   FILE 369
//*          //S1 EXEC PGM=REPLYTO,                                 *   FILE 369
//*          // PARM='J=ADA8|M=ADA040A|R=OK'                        *   FILE 369
//*                                                                 *   FILE 369
//*             WILL REPLY "OK" TO A WTOR MESSAGE BEGINNING         *   FILE 369
//*             "ADA040A" THAT IS ISSUED BY JOB ADA8.               *   FILE 369
//*                                                                 *   FILE 369
//*        EXEC PGM=REPLYTO,PARM='MSG=MMMMMMMM...|                  *   FILE 369
//*                               REPLY=RRRRRRRR...|                *   FILE 369
//*                               ABEND=YES/NO|                     *   FILE 369
//*                               COLUMN=99|                        *   FILE 369
//*                               JOB=JJJJJJJJ|                     *   FILE 369
//*                               TIME=999|                         *   FILE 369
//*                               WAIT=YES/NO'                      *   FILE 369
//*                                                                 *   FILE 369
//*    SD       PUNCH DIRECTORY OF PDS INTO SEQUENTIAL              *   FILE 369
//*             DATASET NON-MODAL COMMAND TO FORMAT THE             *   FILE 369
//*             DIRECTORY INTO A DATASET FOR SUBSEQUENT             *   FILE 369
//*             EDITING, OR TO THE SCREEN.                          *   FILE 369
//*                                                                 *   FILE 369
//*    SID      TITLE 'SID - THIS PGM RETURNS SID INDICATOR         *   FILE 369
//*             IN R15' THE INTENT OF THIS PROGRAM IS TO            *   FILE 369
//*             ALLOW JOBS TO EXECUTE DIFFERENT STEPS BASED         *   FILE 369
//*             ON THE SYSTEM ON WHICH THEY ARE RUN.                *   FILE 369
//*                                                                 *   FILE 369
//*    SITEID   TITLE 'SITEID - SET RETURN CODE BASED ON JES2       *   FILE 369
//*             SPOOL NODE NAME' THE INTENT OF THIS PROGRAM IS      *   FILE 369
//*             TO ALLOW JOBS TO EXECUTE DIFFERENT STEPS BASED      *   FILE 369
//*             ON THE SITE AT WHICH THEY ARE RUN.                  *   FILE 369
//*                                                                 *   FILE 369
//*    SMF240   PURPOSE:  MAP USER SMF RECORD 240                   *   FILE 369
//*                                                                 *   FILE 369
//*    SPY      TITLE 'S P Y --  MVS CONSOLE SPY PROGRAM  --        *   FILE 369
//*             VERSION 3.1' THIS PROGRAM DISPLAYS THE              *   FILE 369
//*             CONTENTS OF ALL ACTIVE GRAPHIC OPERATOR'S           *   FILE 369
//*             CONSOLES ON A TSO CRT.  THE OPERATOR'S SCREEN       *   FILE 369
//*             CAN BE EITHER A 327X OR A 370-168 INTEGRATED        *   FILE 369
//*             CONSOLE WITH 35 LINES.  THE TSO USER CAN USE        *   FILE 369
//*             ANY 327X TERMINAL.  HEAVILY MODIFIED FOR XA         *   FILE 369
//*             AT PRC.                                             *   FILE 369
//*                                                                 *   FILE 369
//*    SRCDOC   ADD DOCUMENTATION TO LMF-MANAGED MEMBERS            *   FILE 369
//*             CREATES AN EYE-CATCHER OF ISPF STATS AND            *   FILE 369
//*             PROMOTION TIME IN THE OBJECT CODE OF A              *   FILE 369
//*             PROMOTED MODULE;                                    *   FILE 369
//*                                                                 *   FILE 369
//*             SRCLEVEL DC    C'IGC0022F V01.M05 85/09/26          *   FILE 369
//*                              17:57 PSYRRS  '                    *   FILE 369
//*                                                                 *   FILE 369
//*             THE SHARED POOL IS ACCESSED TO GET THE              *   FILE 369
//*             MEMBER NAME AND LOW LEVEL QUALIFIER                 *   FILE 369
//*             (LANGUAGE TYPE).  THE LM DIALOG SERVICES ARE        *   FILE 369
//*             THEN USED TO ACCESS VERSION, MODIFICATION           *   FILE 369
//*             LEVEL, DATE, TIME, AND TSO LOGON FROM THE           *   FILE 369
//*             PDS DIRECTORY.  THE INPUT MEMBER IS OPENED          *   FILE 369
//*             FOR UPDATE AND READ.  WHEN THE EXISTING             *   FILE 369
//*             TRIGGER RECORD OR SEQUENCE IS FOUND, THE            *   FILE 369
//*             RECORD IS UPDATED AND REWRITTEN.  NOTE: THIS        *   FILE 369
//*             ROUTINE IS INVOKED FROM THE PROMOTION EXIT          *   FILE 369
//*             DEFINED TO LMF IN THE PROMOTION HIERARCHY,          *   FILE 369
//*             (PANEL 8.5).  THE CLIST, "LMFAPSEX," ALSO IN        *   FILE 369
//*             THIS FILE, IS THE EXIT WE USE.  THIS CLIST          *   FILE 369
//*             WILL NOT WORK FOR YOU WITHOUT MODIFICATION.         *   FILE 369
//*             FOR INSTANCE, YOU WON'T NEED THE "IMP"              *   FILE 369
//*             PRE-PROCESSOR CALL, AND YOUR SYSLIB                 *   FILE 369
//*             CONCATENATION IS GONNA' BE DIFFERENT.               *   FILE 369
//*                                                                 *   FILE 369
//*    SUBAUTHX TITLE 'SUBAUTHX - CHECK FOR AUTHORIZED JOB          *   FILE 369
//*           SUBMISSION PROGRAM'                                   *   FILE 369
//*                                                                 *   FILE 369
//*             FUNCTION   CHECK FOR AUTHORIZED JOB                 *   FILE 369
//*                        SUBMISSION PROGRAM PROVIDES ACF2         *   FILE 369
//*                        "JOBCOPY" FUNCTION FROM WITHIN           *   FILE 369
//*                        ISPF                                     *   FILE 369
//*                                                                 *   FILE 369
//*             OPERATION  IF THE SUBMITTING PROGRAM IS             *   FILE 369
//*                        REENTRANT AND COMES                      *   FILE 369
//*                                                                 *   FILE 369
//*                        FROM AN APF-AUTHORIZED LIBRARY,          *   FILE 369
//*                        THE BIT IN THE ACF DCT EXTENSION         *   FILE 369
//*                        IS SET TO ALLOW THE 'SUBAUTH'            *   FILE 369
//*                        RESTRICTION TO BE MET.                   *   FILE 369
//*                                                                 *   FILE 369
//*             NOTES      THIS EXIT EXTENDS THE FUNCTIONS          *   FILE 369
//*                        PROVIDED BY ACF2 EXIT ACF2XIRD           *   FILE 369
//*                        (INTERNAL READER OPEN) PACKAGED IN       *   FILE 369
//*                        LOAD MODULE ACF2X1J2.  THE EXIT          *   FILE 369
//*                        POINT IS INSERTED IN HASPSSSM AS         *   FILE 369
//*                        PART OF ACF2 INSTALLATION (RELEASE       *   FILE 369
//*                        4.0).  THE ORIGINAL EXIT IS              *   FILE 369
//*                        DESIGNED TO CAPTURE THE SUBMITTING       *   FILE 369
//*                        ENVIRONMENT WHEN INTRDR IS OPENED.       *   FILE 369
//*                        THE PROGRAM NAME AND ITS APF             *   FILE 369
//*                        AUTHORIZATION ARE AMONG THE DATA         *   FILE 369
//*                        PRESERVED.  THESE DATA ARE THEN          *   FILE 369
//*                        USED DURING ACF2 ENTRY VALIDATION,       *   FILE 369
//*                        USUALLY FOR A LID WITH THE RESTRICT      *   FILE 369
//*                        ATTRIBUTE.  THE PROGRAM NAME IS          *   FILE 369
//*                        MATCHED WITH THE PROGRAM SPECIFIED       *   FILE 369
//*                        IN THE LID, AND APF AUTHORIZATION        *   FILE 369
//*                        IS REQUIRED IF THE LID ALSO HAS          *   FILE 369
//*                        SUBAUTH SPECIFIED.                       *   FILE 369
//*                                                                 *   FILE 369
//*    TCAMFIX DESCRIPTION - THIS ROUTINE CLEANS UP THE             *   FILE 369
//*            CVTAQAVB FIELD SO TCAM WILL INITIALIZE.  THE         *   FILE 369
//*            CVT-BASED TCAM IS SUPPOSED TO DO THIS WHEN IT        *   FILE 369
//*            TERMINATES, BUT IT ISN'T ALWAYS SO OBLIGING.         *   FILE 369
//*            IF THE OPERATOR RESPONDS "Y" TO OUR MESSAGE          *   FILE 369
//*            IEDPRC1D, THEN WE ZERO THIS FIELD.  NOTE - WE        *   FILE 369
//*            MUST RUN APF-AUTHORIZED.                             *   FILE 369
//*                                                                 *   FILE 369
//*    TLBLMAIN TITLE 'TLBLMAIN -- MAIN MODULE FOR TAPE             *   FILE 369
//*                                LABEL WRITER'                    *   FILE 369
//*                                                                 *   FILE 369
//*             FUNCTION     PROCESS REQUESTS TO PRINT              *   FILE 369
//*                          EXTERNAL TAPE LABELS PRINT TAPE        *   FILE 369
//*                          LABELS AT TAPE MOUNT TIME              *   FILE 369
//*                          WITHOUT A TAPE MANAGEMENT              *   FILE 369
//*                          SYSTEM.                                *   FILE 369
//*                                                                 *   FILE 369
//*             OUTPUT       LABEL PRINTED ON 328X-TYPE             *   FILE 369
//*                          PRINTER VIA VTAM                       *   FILE 369
//*                                                                 *   FILE 369
//*    WAIT   TITLE 'WAIT - WAIT A LITTLE BIT.' THIS MODULE         *   FILE 369
//*           WILL WAIT THE REQUESTED NUMBER OF SECONDS.            *   FILE 369
//*           PARM='NNNN', WHERE 0 < NNNN <= 9999, THE NUMBER       *   FILE 369
//*           OF SECONDS TO WAIT.  DEFAULT IS 10 SECONDS.           *   FILE 369
//*                                                                 *   FILE 369
//*    WTO      TITLE 'WTO    - OPERATIONS COMMUNICATION'           *   FILE 369
//*             THIS PROGRAM PROVIDES PROGRAMMER TO OPERATOR        *   FILE 369
//*             COMMUNICATION.  THIS IS THE IPO "WTO"               *   FILE 369
//*             DIDDLED TO ALLOW GREATER THAN 72 BYTE               *   FILE 369
//*             MESSAGES.                                           *   FILE 369
//*                                                                 *   FILE 369
//*    WTONR    TITLE 'WTONR - WRITE NON-ROLLABLE OPERATOR          *   FILE 369
//*                    MESSAGES.'                                   *   FILE 369
//*             DESCRIPTION - WE READ SYSIN INPUT AND WTO           *   FILE 369
//*               CARD IMAGES TO THE OPERATOR CONSOLE THAT          *   FILE 369
//*               ARE NON-ROLLABLE.  ORIGINALLY USED BY THE         *   FILE 369
//*               MESSENGER JOBS FOR AN OPERATOR RESTART.           *   FILE 369
//*                                                                 *   FILE 369
//*             NOTE - WE MUST BE APF-AUTHORIZED TO WRITE           *   FILE 369
//*                    NON-ROLLABLE MESSAGE                         *   FILE 369
//*                                                                 *   FILE 369
//*             TO USE -                                            *   FILE 369
//*              //S1 EXEC PGM=WTONR                                *   FILE 369
//*              //STEPLIB DD DSN=AN.APF.LIBRARY,DISP=SHR           *   FILE 369
//*              //SYSIN   DD *                                     *   FILE 369
//*              * THIS IS A COMMENT                                *   FILE 369
//*              ---> UP TO THREE LINES OF TEXT <---                *   FILE 369
//*              ---> AFTER THREE LINES IGNORED <---                *   FILE 369
//*              ---> COLS 1-72 ARE PROCESSED   <---                *   FILE 369
//*              /*                                                 *   FILE 369
//*                                                                 *   FILE 369
```
