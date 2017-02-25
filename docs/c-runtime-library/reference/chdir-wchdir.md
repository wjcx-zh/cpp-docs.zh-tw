---
title: "_chdir、_wchdir | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wchdir"
  - "_chdir"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "tchdir"
  - "_chdir"
  - "_wchdir"
  - "_tchdir"
  - "wchdir"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tchdir 函式"
  - "_chdir 函式"
  - "_wchdir 函式"
  - "tchdir 函式"
  - "wchdir 函式"
  - "chdir 函式"
  - "變更目錄 [c + +]"
ms.assetid: 85e9393b-62ac-45d5-ab2a-fa2217f6152e
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _chdir、_wchdir
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

變更目前工作目錄。  
  
## 語法  
  
```  
int _chdir(   
   const char *dirname   
);  
int _wchdir(   
   const wchar_t *dirname   
);  
```  
  
#### 參數  
 `dirname`  
 新工作目錄的路徑。  
  
## 傳回值  
 如果成功，這些函式會傳回值 0。 –1 的傳回值表示失敗。 如果找不到指定的路徑，`errno`  會設定為 `ENOENT`。 如果 `dirname` 為 NULL，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，`errno`  會設定為 `EINVAL` ，且此函式會傳回 \-1。  
  
## 備註  
 `_chdir`  函式會將目前工作目錄變更為 `dirname` 指定的目錄。`dirname` 參數必須參考現有的目錄。 這個函式可以變更任何磁碟機上的目前工作目錄。 如果在 `dirname` 中指定了新的磁碟機代號，預設磁碟機代號也會變更。 例如，如果 A 是預設磁碟機代號，而 \\BIN 是目前工作目錄，下列呼叫會變更磁碟機 C 的目前工作目錄，並將 C 建立為新的預設磁碟機：  
  
```  
_chdir("c:\\temp");  
```  
  
 當您在路徑中使用選擇性反斜線字元 \(`\`\) 時，您必須在 C 字串常值中放置兩個反斜線 \(`\\`\) 來表示單一反斜線 \(`\`\)。  
  
 `_wchdir`  是寬字元版的 `_chdir`；`_wchdir`  的 `dirname` 引數是寬字元字串。`. _wchdir`  和 `_chdir`  的行為相同。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tchdir`|`_chdir`|`_chdir`|`_wchdir`|  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_chdir`|\<direct.h\>|\<errno.h\>|  
|`_wchdir`|\<direct.h\> 或 \<wchar.h\>|\<errno.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_chdir.c  
// arguments: C:\WINDOWS  
  
/* This program uses the _chdir function to verify  
   that a given directory exists. */  
  
#include <direct.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( int argc, char *argv[] )  
{  
  
   if(_chdir( argv[1] ) )  
   {  
      switch (errno)  
      {  
      case ENOENT:  
         printf( "Unable to locate the directory: %s\n", argv[1] );  
         break;  
      case EINVAL:  
         printf( "Invalid buffer.\n");  
         break;  
      default:  
         printf( "Unknown error.\n");  
      }  
   }  
   else  
      system( "dir *.exe");  
}  
```  
  
```Output  
Volume in drive C has no label. (磁碟機 C 內的磁碟區沒有標籤。) Volume Serial Number is 2018-08A1 Directory of c:\windows 08/29/2002  04:00 AM         1,004,032 explorer.exe 12/17/2002  04:43 PM            10,752 hh.exe 03/03/2003  09:24 AM            33,792 ieuninst.exe 10/29/1998  04:45 PM           306,688 IsUninst.exe 08/29/2002  04:00 AM            66,048 NOTEPAD.EXE 03/03/2003  09:24 AM            33,792 Q330994.exe 08/29/2002  04:00 AM           134,144 regedit.exe 02/28/2003  06:26 PM            46,352 setdebug.exe 08/29/2002  04:00 AM            15,360 TASKMAN.EXE 08/29/2002  04:00 AM            49,680 twunk_16.exe 08/29/2002  04:00 AM            25,600 twunk_32.exe 08/29/2002  04:00 AM           256,192 winhelp.exe 08/29/2002  04:00 AM           266,752 winhlp32.exe 13 File(s)      2,249,184 bytes 0 Dir(s)  67,326,029,824 bytes free  
```  
  
## .NET Framework 對等用法  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## 請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir、\_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)