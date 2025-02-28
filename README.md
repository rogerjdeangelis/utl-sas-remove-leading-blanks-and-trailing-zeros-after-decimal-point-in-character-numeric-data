# utl-sas-remove-leading-blanks-and-trailing-zeros-after-decimal-point-in-character-numeric-data
sas remove leading blanks and trailing zeros after decimal point in character numeric data
    %let pgm=utl-sas-remove-leading-blanks-and-trailing-zeros-after-decimal-point-in-character-numeric-data;

    %stop_submission;

    sas remove leading blanks and trailing zeros after decimal point in character numeric data

      Two aolutions

          1 sas loadinfile or loadinfileb
          2 sas prxchange
            ksharpe
            https://communities.sas.com/t5/user/viewprofilepage/user-id/18408

    github
    https://tinyurl.com/yynmz3cz
    https://github.com/rogerjdeangelis/utl-sas-remove-leading-blanks-and-trailing-zeros-after-decimal-point-in-character-numeric-data

    sas communities
    https://tinyurl.com/nhbvehbm
    https://communities.sas.com/t5/SAS-Programming/Removing-Trailing-zeros-after-decimal-point-in-character-data/m-p/956391#M373473

    loadinfile macro (two macros can be used loadinfob and loadinfo)
    https://tinyurl.com/y9nfugth
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories


    /**************************************************************************************************************************/
    /*                               |                                       |                                                */
    /*     INPUT                     |          PROCESS                      |          OUTPUT                                */
    /*     =====                     |          =======                      |          ======                                */
    /*                               |                                       |                                                */
    /*                               | 1 SAS LOADINFILE OR LOADINFILEB       |                                                */
    /*                               | ===============================       |                                                */
    /*                               |                                       |   CHRNUM         NUMCHR                        */
    /*   CHRNUM                      |   INPUT USING FORMAT 10. REMOVES      |                                                */
    /*                               |   LEADING BLANKS AND TRAILING         |    60.0000            60                       */
    /*    60.0000                    |   ZEROS                               |    45.500           45.5                       */
    /*    45.500                     |                                       |   100                100                       */
    /*   100                         |   data want;                          |    33.30            33.3                       */
    /*    33.30                      |    length numchr $16.;                |    25.010          25.01                       */
    /*    25.010                     |    set have;                          |    43.001010    43.00101                       */
    /*    43.001010                  |    %loadinfile(chrnum);               |                                                */
    /*                               |    input num 10. @;                   |   Variable    Type    Len                      */
    /*   data have;                  |    numchr=num;                        |                                                */
    /*    input chrnum $char16.;     |    input @1 @@;                       |   NUMCHR      Char     16                      */
    /*   cards4;                     |    drop num;                          |   CHRNUM      Char     16                      */
    /*    60.0000                    |   run;quit;                           |                                                */
    /*    45.500                     |                                       |                                                */
    /*   100                         |                                       |                                                */
    /*    33.30                      |----------------------------------------------------------------------------------------*/
    /*    25.010                     |                                       |                                                */
    /*    43.001010                  |  2 SAS PRXCHANGE                      |                                                */
    /*   ;;;;                        |                                       |   WANT                                         */
    /*   run;quit;                   |                                       |                                                */
    /*                               |  KEEPS LEADING SPACES                 |    CHRNUM       NUMCHR                         */
    /*                               |                                       |                                                */
    /*                               |  data want;                           |    60.0000       60                            */
    /*                               |    set have;                          |    45.500        45.5                          */
    /*                               |    if findc(chrnum,'.') then          |   100           100                            */
    /*                               |       numchr=prxchange('s/\.\s*$//'   |    33.30         33.3                          */
    /*                               |     ,1                                |    25.010        25.01                         */
    /*                               |     ,prxchange('s/0+\s*$//'           |    43.001010     43.00101                      */
    /*                               |     ,1,chrnum));                      |                                                */
    /*                               |    else numchr=chrnum;                |   Variable    Type    Len                      */
    /*                               |  run;quit;                            |                                                */
    /*                               |                                       |   CHRNUM      Char     16                      */
    /*                               |                                       |   NUMCHR      Char    200                      */
    /*                               |                                       |                                                */
    /**************************************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
