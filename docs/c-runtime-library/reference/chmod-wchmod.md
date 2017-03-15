---
title: "_chmod、_wchmod | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_chmod"
  - "_wchmod"
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
  - "_chmod"
  - "_wchmod"
  - "wchmod"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_chmod 函式"
  - "_wchmod 函式"
  - "chmod 函式"
  - "檔案使用權限 [C++]"
  - "檔案 [C++], 變更權限"
  - "wchmod 函式"
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _chmod、_wchmod
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

變更檔案的使用權限集合。  
  
## 語法  
  
```  
  
      int _chmod(   
   const char *filename,  
   int pmode   
);  
int _wchmod(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### 參數  
 `filename`  
 現存檔的名稱。  
  
 `pmode`  
 檔案的使用權限設定。  
  
## 傳回值  
 如果成功變更，這些函式傳回 0 使用權限設定。  傳回值為 \-1 表示失敗。  如果找不到指定的檔案， `errno` 設定為 `ENOENT`;如果參數無效， `errno` 設定為 `EINVAL`。  
  
## 備註  
 檔案的使用權限集合是由 `filename`指定的 `_chmod` 函式變更*。*使用權限設定控制對檔案的讀取和寫入。  整數運算式 `pmode` 包含定義於 SYS\\Stat.h 裏的下列資訊清單常值其一或兩者兼有的整數表達式。  
  
 `_S_IWRITE`  
 允許的寫入。  
  
 `_S_IREAD`  
 允許的讀取。  
  
 `_S_IREAD | _S_IWRITE`  
 允許讀取和寫入。  
  
 當給定兩個常值時，它們以位元連接藉由 `OR` 運算子\(         `|` \).  如果沒有寫入權限，則檔案是唯讀的。  請注意所有檔案都是可讀取的;寫入唯寫權限是不可能的。  因此， `_S_IWRITE` 和 `_S_IREAD | _S_IWRITE` 模式等價。  
  
 `_wchmod` 是 `_chmod` 的寬字元版本。 `_wchmod` 的 `filename` 引數是寬字元字串。  `_wchmod` 和 `_chmod` 其餘行為相同。  
  
 這個函式會驗證它的參數。  如果 `pmode` 不是其中一個組件資訊清單常數也不會合併替代組常數，函式會忽略參數。  如果 `filename` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，`errno` 會被設定為 `EINVAL` 且函式會傳回\-1 。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tchmod`|`_chmod`|`_chmod`|`_wchmod`|  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_chmod`|\<io.h\>|\<sys\/types.h\>, \<sys\/stat.h\>, \<errno.h\>|  
|`_wchmod`|\<io.h\> or \<wchar.h\>|\<sys\/types.h\>, \<sys\/stat.h\>, \<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_chmod.c  
// This program uses _chmod to  
// change the mode of a file to read-only.  
// It then attempts to modify the file.  
//  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
// Change the mode and report error or success   
void set_mode_and_report(char * filename, int mask)  
{  
   // Check for failure   
   if( _chmod( filename, mask ) == -1 )  
   {  
      // Determine cause of failure and report.   
      switch (errno)  
      {  
         case EINVAL:  
            fprintf( stderr, "Invalid parameter to chmod.\n");  
            break;  
         case ENOENT:  
            fprintf( stderr, "File %s not found\n", filename );  
            break;  
         default:  
            // Should never be reached   
            fprintf( stderr, "Unexpected error in chmod.\n" );  
       }  
   }  
   else  
   {  
      if (mask == _S_IREAD)  
        printf( "Mode set to read-only\n" );  
      else if (mask & _S_IWRITE)  
        printf( "Mode set to read/write\n" );  
   }  
   fflush(stderr);  
}  
  
int main( void )  
{   
  
   // Create or append to a file.   
   system( "echo /* End of file */ >> crt_chmod.c_input" );  
  
   // Set file mode to read-only:   
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );  
  
   system( "echo /* End of file */ >> crt_chmod.c_input " );  
  
   // Change back to read/write:   
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );  
  
   system( "echo /* End of file */ >> crt_chmod.c_input " );   
}   
```  
  
  **`文字行。` `文字行。`對唯讀的模組集**  
**存取被拒絕。**  
**讀取\/寫入的模組集**   
## .NET Framework 對等用法  
  
-   [System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)  
  
-   [System::Security::Permissions::FileIOPermission](https://msdn.microsoft.com/en-us/library/system.security.permissions.fileiopermission.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_access、\_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_stat、\_wstat 函式](../../c-runtime-library/reference/stat-functions.md)