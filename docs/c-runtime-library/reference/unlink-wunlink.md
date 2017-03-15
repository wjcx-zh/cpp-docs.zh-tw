---
title: "_unlink、_wunlink | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_unlink"
  - "_wunlink"
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
  - "_tunlink"
  - "_unlink"
  - "wunlink"
  - "_wunlink"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tunlink 函式"
  - "_unlink 函式"
  - "_wunlink 函式"
  - "檔案 [C++], 刪除"
  - "檔案 [C++], 移除"
  - "tunlink 函式"
  - "unlink 函式"
  - "wunlink 函式"
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _unlink、_wunlink
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刪除檔案  
  
## 語法  
  
```  
int _unlink(  
   const char *filename   
);  
int _wunlink(  
   const wchar_t *filename   
);  
```  
  
#### 參數  
 `filename`  
 要移除的檔案名稱。  
  
## 傳回值  
 如果成功，這些函式都會傳回 0。  否則，函式會傳回– 1 並將 `errno` 設定為 `EACCES`，表示路徑指定唯讀檔案，則為 `ENOENT`，表示檔案或路徑找不到或路徑指定了目錄。  
  
 如需有關這些回傳碼和其他回傳碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_unlink` 函式刪除`filename`指定的檔案。  `_wunlink` 是 `_unlink` 的寬字元版本。 `_wunlink` 的 `filename` 引數是寬字元字串。  這三個函式其餘部分的運作相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tunlink`|`_unlink`|`_unlink`|`_wunlink`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_unlink`|\<io.h 和\> stdio.h \<\>|  
|`_wunlink`|\<io.h\> or \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式碼範例  
 這個程式會使用 \_unlink 刪除 CRT\_UNLINK.TXT。  
  
```  
// crt_unlink.c  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( _unlink( "crt_unlink.txt" ) == -1 )  
      perror( "Could not delete 'CRT_UNLINK.TXT'" );  
   else  
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );  
}  
```  
  
### 輸入:crt\_unlink.txt  
  
```  
This file will be deleted.  
```  
  
### 範例輸出  
  
```  
Deleted 'CRT_UNLINK.TXT'  
```  
  
## .NET Framework 對等用法  
 [System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [remove、\_wremove](../../c-runtime-library/reference/remove-wremove.md)