---
title: "寫入 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_write"
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
apitype: "DLLExport"
f1_keywords: 
  - "write"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "write 函式"
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# _write
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將資料寫入檔案。  
  
## 語法  
  
```  
int _write(    int fd,    const void *buffer,    unsigned int count  );  
```  
  
#### 參數  
 `fd`  
 資料要寫入至其中之檔案的檔案描述項。  
  
 `buffer`  
 要寫入的資料。  
  
 `count`  
 位元組數。  
  
## 傳回值  
 若成功，`_write` 會傳回實際寫入的位元組數。  若磁碟上剩餘的實際空間小於函式嘗試寫入至磁碟的緩衝區大小，則 `_write` 會失敗，且不會清除任何緩衝區的內容到磁碟中。  –1 的傳回值表示錯誤。  若傳遞了無效的參數，此函式會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  若允許繼續執行，函式會傳回 \-1，且 `errno` 會設為以下三個值之一：`EBADF`，表示檔案描述項無效，或者不是供寫入而開啟檔案；`ENOSPC`，表示裝置上沒有足夠的剩餘空間可供作業使用；`EINVAL`，表示 `buffer` 為 Null 指標，或是在 Unicode 模式中傳遞了要寫入檔案的 `count` 個奇數位元組。  
  
 如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 若在文字模式中開啟檔案，則會在輸出中將每個換行字元取代為歸位字元 \(換行字元組\)。  這種取代不會影響傳回值。  
  
 若在 Unicode 轉譯模式中開啟檔案，例如，使用 `_open` 或 `_sopen` 以及一個包含 `_O_WTEXT`、`_O_U16TEXT` 或 `_O_U8TEXT` 的模式參數開啟 `fd`；或是使用 `fopen` 以及一個包含 `ccs=UNICODE`、`ccs=UTF-16LE` 或 `ccs=UTF-8` 的模式參數開啟 fd；或者此模式已透過使用 `_setmode` 變更為 Unicode 轉譯模式：則 `buffer` 會解譯為包含 **UTF\-16** 資料之 `wchar_t` 陣列的指標。  嘗試以此模式寫入奇數位元組會導致參數驗證錯誤。  
  
## 備註  
 `_write` 函式會將 `count` 個位元組從 `buffer` 寫入至與 `fd` 相關的檔案。  寫入作業會從與指定檔案相關之檔案指標 \(若有的話\) 的目前位置開始。  若檔案是開啟為以供附加，則作業會在檔案的目前結尾開始。  經過寫入作業之後，檔案指標會隨著實際寫入的位元組數而增加。  
  
 寫入以文字模式開啟的檔案時，`_write` 會將 CTRL\+Z 字元視為邏輯檔案結尾。  寫入至裝置中時，`_write` 會將緩衝區中的 CTRL\+Z 字元視為輸出結束字元。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_write`|\<io.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt__write.c  
//   
// This program opens a file for output and uses _write to write  
// some bytes to the file.  
  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <errno.h>  
#include <share.h>  
  
char buffer[] = "This is a test of '_write' function";  
  
int main( void )  
{  
   int         fileHandle = 0;  
   unsigned    bytesWritten = 0;  
  
   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,  
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )  
      return -1;  
  
   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )  
   {  
      switch(errno)  
      {  
         case EBADF:  
            perror("Bad file descriptor!");  
            break;  
         case ENOSPC:  
            perror("No space left on device!");  
            break;  
         case EINVAL:  
            perror("Invalid parameter: buffer was NULL!");  
            break;  
         default:  
            // An unrelated error occured   
            perror("Unexpected error!");  
      }  
   }  
   else  
   {  
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );  
   }  
   _close( fileHandle );  
}  
```  
  
  **將 36 個位元組寫入檔案。**   
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_read](../../c-runtime-library/reference/read.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)