<!-- saved from url=(0048) https://kacos2000.github.io/Win10-Research/Bam/ --> 
<!-- https://guides.github.com/features/mastering-markdown/ --> 

   
### -> UPDATE (09/2019) ###
  - In Win10 **v1809** & **v1903**, BAM stopped updating  "\bam\UserSettings" (old entries may still be found there) and now updates "bam\ *State* \UserSettings". These powershell scripts get the data from the new location:<br>
  
    [bam.ps1](https://github.com/kacos2000/Win10-Research/blob/master/Bam/bam.ps1) *(parses both locations)* <br>
    [bamoffline1.ps1](https://github.com/kacos2000/Win10-Research/blob/master/Bam/bamoffline1.ps1) *(parses both locations)* <br>
    [bam1809.ps1](https://github.com/kacos2000/Win10-Research/blob/master/Bam/bam1809.ps1) <br>
    [bamoffline1809.ps1](https://github.com/kacos2000/Win10-Research/blob/master/Bam/bamoffline1809.ps1)<br> 

## Windows 10 *(1703+)* Background Activity Moderator ##

- [**BAMparser.ps1** - PowerShell script](https://github.com/kacos2000/Win10-Research/blob/master/Bam/BAMParser.ps1) by [Matthew Green](https://github.com/mgreen27) *(original is [here](https://github.com/mgreen27/Powershell-IR/blob/master/Content/Other/Get-BAMParser.ps1))* for live parsing of the BAM service key:

  ![BAMparser.ps1 results](https://raw.githubusercontent.com/kacos2000/Win10-Research/master/Bam/utc_results.JPG)
    

- [**bam.ps1** - Modification of the above script](https://github.com/kacos2000/Win10-Research/blob/master/Bam/bam.ps1) to get the results in a pop-up Window with Filestamps in both UTC and user's locatime

  ![bam.ps1 results](https://raw.githubusercontent.com/kacos2000/Win10-Research/master/Bam/results.JPG)

  User can select all lines (Ctrl+A) or specific lines (Ctrl+click) and copy/paste (Ctrl+C and Ctrl+V) the data to a text file or MS Excel  spreadsheet. The Selected lines are also displayed in the console after the user presses the OK button.

  ![bam.ps1 console](https://raw.githubusercontent.com/kacos2000/Win10-Research/master/Bam/console.JPG)
  
- [**bam1.ps1** - 2nd Modification of the above script](https://github.com/kacos2000/Win10-Research/blob/master/Bam/bam1.ps1) - This one is like bam.ps1 but includes separate filename & path and 3 different dates: UTC, localtime and calculated user time (utc +- the Active Time Bias. Information on the Timezone, Daylight savings and Active time bias are in the header:
    
  ![bam1.ps1 output](https://raw.githubusercontent.com/kacos2000/Win10-Research/master/Bam/o_o.JPG)

-  [**bamoffline.ps1** - Offline parser](https://github.com/kacos2000/Win10-Research/blob/master/Bam/bamoffline.ps1) reads an **offline** system hive *(SYSTEM)* and displays the BAM key entries in a pop-up Window with Filestamps in UTC and the *SYSTEM* hive's timezone (calculated from the *ActiveTimeBias*). It can also read *SYSTEM* hives directly from FTK image mounted logical drives. **Note:** *must be run in a PowerShell console with Administrator privileges.* The script asks the user to select a *SYSTEM* hive file:

    ![Select SYSTEM hive](https://raw.githubusercontent.com/kacos2000/Win10-Research/master/Bam/select.JPG)

    Calculates the SHA256 hash of the *SYSTEM* hive file and opens it (Read Only). The results are shown in a popup window with Filestamp in user localtime. User can select all lines (Ctrl+A) or specific lines (Ctrl+click) and copy/paste (Ctrl+C and Ctrl+V) the data to a text file or MS Excel spreadsheet. The Selected lines are also displayed in the console after the user presses the OK button.
  
   ![Offline results](https://raw.githubusercontent.com/kacos2000/Win10-Research/master/Bam/o_results.JPG)
  
   After the result window is closed *(user presses the OK button)*, a new SHA256 hash of the *SYSTEM* hive file is calculated and checked against the original:
  
   ![Offline console](https://raw.githubusercontent.com/kacos2000/Win10-Research/master/Bam/o_console.JPG)
   
  - [**bamoffline1.ps1** - Offline parser](https://github.com/kacos2000/Win10-Research/blob/master/Bam/bamoffline1.ps1) is similar to the above except that it includes separate filename & path and 3 different dates: Examiner local time, UTC, and calculated user time (utc +- the Active Time Bias. Information on the Timezone, Daylight savings and Active time bias are in the header:
  
    ![Offline results](https://raw.githubusercontent.com/kacos2000/Win10-Research/master/Bam/0_01.JPG)
  
    console example:
   
    ![console example](https://raw.githubusercontent.com/kacos2000/Win10-Research/master/Bam/0_02.JPG)
    

  

- [**Documentation**](https://github.com/kacos2000/Win10-Research/blob/master/Bam/BAM%20-%20Background%20Activity%20Moderator.pdf) of the Background Activity Moderator service key (**[pdf](https://github.com/kacos2000/Win10-Research/blob/master/Bam/BAM%20-%20Background%20Activity%20Moderator.pdf)**)
  
    *Other References*:
    
     1.  *[Background Activity Moderator Driver](http://batcmd.com/windows/10/services/bam/)* 
     2.  *[About BAM key (execution trace #1) -in Japanese](https://padawan-4n6.hatenablog.com/entry/2018/02/22/131110)*
     3.  *[About BAM key (execution trace #2) -in Japanese](https://padawan-4n6.hatenablog.com/entry/2018/03/07/191419)*
     4.  *[BAM Key and Process Execution, Updated Plugins](http://windowsir.blogspot.com.au/2018/03/new-and-updated-plugins-other-items.html)*
     5. *[Bam - Alternative to Prefetch](https://www.linkedin.com/pulse/alternative-prefetch-bam-costas-katsavounidis/)*
     6. *[BAM Internals](https://dfir.ru/2020/04/08/bam-internals/)*

Status
 - **[x]** Live Parser 
 - **[x]** Offline SYSTEM hive parser
