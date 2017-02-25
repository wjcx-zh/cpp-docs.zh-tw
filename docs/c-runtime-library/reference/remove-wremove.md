---
title: "remove、_wremove | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wremove"
  - "remove"
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
  - "remove"
  - "_wremove"
  - "_tremove"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tremove 函式"
  - "_wremove 函式"
  - "檔案 [C++], 刪除"
  - "檔案 [C++], 移除"
  - "remove 函式"
  - "tremove 函式"
  - "wremove 函式"
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# remove、_wremove
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刪除檔案  
  
## 語法  
  
```  
  
      int remove(  
   const char *path   
);  
int _wremove(  
   const wchar_t *path   
);  
```  
  
#### 參數  
 *path*  
 待移除檔案的路徑。  
  
## 傳回值  
 如果檔案已成功刪除，這些函式都會傳回 0。  否則，會傳回 \-1 並設定 `errno` 的任一對 `EACCES` 表示路徑指定唯讀檔案已開啟，則為表示的 **ENOENT** 檔案名稱或路徑找不到或路徑指定目錄。  
  
 如需有關這些回傳碼和其他回傳碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 **remove** 函式刪除指定路徑的檔案 *。* `_wremove` 是 **\_remove**寬字元版本;對 `_wremove` 的 *路徑* 引數是寬字元字串。  否則 `_wremove` 和 **\_remove** 的行為相同。  對檔案的所有控制代碼，刪除之前必須先關閉。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tremove`|**remove**|**remove**|`_wremove`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|**remove**|\<stdio.h\> 或 \<io.h\>|  
|`_wremove`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_remove.c  
/* This program uses remove to delete crt_remove.txt */  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( remove( "crt_remove.txt" ) == -1 )  
      perror( "Could not delete 'CRT_REMOVE.TXT'" );  
   else  
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );  
}  
```  
  
## 輸入:crt\_remove.txt  
  
```  
This file will be deleted.  
```  
  
## 範例輸出  
  
```  
Deleted 'CRT_REMOVE.TXT'  
```  
  
## .NET Framework 對等用法  
 [System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_unlink、\_wunlink](../../c-runtime-library/reference/unlink-wunlink.md)