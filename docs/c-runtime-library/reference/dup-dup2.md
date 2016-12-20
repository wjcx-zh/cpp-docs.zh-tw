---
title: "_dup、_dup2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_dup"
  - "_dup2"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_dup2"
  - "_dup"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_dup 函式"
  - "_dup2 函式"
  - "dup 函式"
  - "dup2 函式"
  - "檔案控制代碼 [C++], 複製"
  - "檔案控制代碼 [C++], 重新指派"
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _dup、_dup2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立開啟檔案 \(`_dup`\) 的第二個檔案描述項，或重新指派檔案描述項 \(`_dup2`\)。  
  
## 語法  
  
```  
int _dup(   
   int fd   
);  
int _dup2(   
   int fd1,  
   int fd2   
);  
```  
  
#### 參數  
 `fd`, `fd1`  
 參考開啟檔案的檔案描述項。  
  
 `fd2`  
 任何檔案描述項。  
  
## 傳回值  
 `_dup` 會傳回新的檔案描述項。  `_dup2` 會傳回 0 以表示成功。  如果發生錯誤，每一個函式皆傳回 – 1 並在檔案描述無效時，將 `errno` 設為 `EBADF` ；如果沒有其他可用的檔案描述項，則設為 `EMFILE`。  在無效檔案描述項的情況下，函式也會叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 、和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `_dup` 和 `_dup2` 函式將第二個檔案描述項與目前開啟的檔案作關聯。  這些函式可用於關聯預先定義的檔案描述項，例如 `stdout`，或者與不同檔案作關聯。  使用任一檔案描述項，檔案中的作業可以在其上執行。  檔案中允許的存取類型不會受到新建立描述項的影響。  `_dup` 為指定之檔案傳回下一個可用的檔案描述項。  `_dup2` 強制 `fd2` 參考檔案與 `fd1`相同。  如果 `fd2` 在呼叫時與開啟檔案作關聯，則會關閉該檔案。  
  
 `_dup` 和 `_dup2` 接受檔案描述做為參數。  若要將資料流 `(FILE *)` 傳至任一中的函式，請使用 [\_fileno](../../c-runtime-library/reference/fileno.md)。  `fileno` 常式會傳回目前與指定資料流關聯的檔案描述項。  下列範例顯示如何將 `stderr` \(定義在 Stdio.h 中的 `FILE` `*` \) 與檔案描述項關聯：  
  
```  
int cstderr = _dup( _fileno( stderr ));  
```  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_dup`|\<io.h\>|  
|`_dup2`|\<io.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_dup.c  
// This program uses the variable old to save  
// the original stdout. It then opens a new file named  
// DataFile and forces stdout to refer to it. Finally, it  
// restores stdout to its original state.  
//  
  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int old;  
   FILE *DataFile;  
  
   old = _dup( 1 );   // "old" now refers to "stdout"   
                      // Note:  file descriptor 1 == "stdout"   
   if( old == -1 )  
   {  
      perror( "_dup( 1 ) failure" );  
      exit( 1 );  
   }  
   _write( old, "This goes to stdout first\n", 26 );  
   if( fopen_s( &DataFile, "data", "w" ) != 0 )  
   {  
      puts( "Can't open file 'data'\n" );  
      exit( 1 );  
   }  
  
   // stdout now refers to file "data"   
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )  
   {  
      perror( "Can't _dup2 stdout" );  
      exit( 1 );  
   }  
   puts( "This goes to file 'data'\n" );  
  
   // Flush stdout stream buffer so it goes to correct file   
   fflush( stdout );  
   fclose( DataFile );  
  
   // Restore original stdout   
   _dup2( old, 1 );  
   puts( "This goes to stdout\n" );  
   puts( "The file 'data' contains:" );  
   _flushall();  
   system( "type data" );  
}  
```  
  
  **結果會先顯示在stdout**  
**這些結果會再顯於stdout**  
**'data'這檔案中會包含:**  
**這些會在'data'這檔案中**   
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)