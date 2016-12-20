---
title: "rename、_wrename | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "rename"
  - "_wrename"
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
  - "_wrename"
  - "_trename"
  - "Rename"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_trename 函式"
  - "_wrename 函式"
  - "目錄 [C++], 重新命名"
  - "檔案 [C++], 重新命名"
  - "名稱 [C++], 變更目錄"
  - "名稱 [C++], 變更檔案"
  - "rename 函式"
  - "重新命名目錄"
  - "重新命名檔案"
  - "trename 函式"
  - "wrename 函式"
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rename、_wrename
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重新命名目錄或目錄  
  
## 語法  
  
```  
  
      int rename(  
   const char *oldname,  
   const char *newname   
);  
int _wrename(  
   const wchar_t *oldname,  
   const wchar_t *newname   
);  
```  
  
#### 參數  
 *oldname*  
 指到舊名稱的指標。  
  
 *NewName*  
 對新名稱的指標。  
  
## 傳回值  
 如果成功，這些函式都會傳回 0。  在錯誤，函式會傳回非零的值並將 `errno` 設定為下列其中一個值:  
  
 `EACCES`  
 *newname* 或目錄中指定的檔案已經存在或是無法建立 \(無效路徑\);或者 *oldname* 是目錄，而 *newname* 指定不同的路徑。  
  
 `ENOENT`  
 *oldname* 找不到或路徑指定的檔案。  
  
 `EINVAL`  
 名稱包含無效字元。  
  
 如需其他可能的傳回值，請參閱 [\_doserrno、\_errno、syserrlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 **rename** 函式給 *oldname* 或目錄重新命名指定的檔案至 *newname*指定名稱。  舊名稱必須是現有檔案或目錄的路徑。  新名稱不可以是現有的檔案或目錄的名稱。  您可以使用 **rename** 從目錄移動檔案或裝置到另一個傳遞給 *newname* 引數不同的路徑。  不過，您無法使用 **rename**來移動目錄。  目錄可以重新命名，但是並沒有移動。  
  
 `_wrename` 是  `的寬字元版本，_wrename` 引數是寬字元字串。  否則 `_wrename` 和 **\_rename** 的行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE &\_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|---------------------------|----------------|-------------------|  
|`_trename`|**重新命名**|**重新命名**|`_wrename`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|**重新命名**|\<io.h\> 或 \<stdio.h\>|  
|`_wrename`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_renamer.c  
/* This program attempts to rename a file named  
 * CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation  
 * to succeed, a file named CRT_RENAMER.OBJ must exist and  
 * a file named CRT_RENAMER.JBO must not exist.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   int  result;  
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";  
  
   /* Attempt to rename file: */  
   result = rename( old, new );  
   if( result != 0 )  
      printf( "Could not rename '%s'\n", old );  
   else  
      printf( "File '%s' renamed to '%s'\n", old, new );  
}  
```  
  
## Output  
  
```  
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'  
```  
  
## .NET Framework 對等用法  
 [System::IO::File::Move](https://msdn.microsoft.com/en-us/library/system.io.file.move.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)