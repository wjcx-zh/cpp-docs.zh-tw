---
title: "_umask_s | Microsoft Docs"
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
  - "_umask_s"
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
  - "unmask_s"
  - "_umask_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_umask_s 函式"
  - "檔案使用權限 [C++]"
  - "檔案 [C++], 的使用權限設定"
  - "遮罩"
  - "遮罩, 檔案使用權限設定"
  - "umask_s 函式"
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _umask_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定預設檔案使用權限遮。  這些是 [\_umask](../../c-runtime-library/reference/umask.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t _umask_s(  
   int mode,  
   int * pOldMode  
);  
```  
  
#### 參數  
 \[in\] `mode`  
 預設使用權限集合。  
  
 \[out\] `oldMode`  
 使用權限設定先前的值。  
  
## 傳回值  
 傳回錯誤碼，如果 `Mode` 沒有指定有效的方式或 `pOldMode` 指標是 `NULL`。  
  
### 錯誤狀況  
  
|`mode`|`pOldMode`|**傳回值**|`oldMode` **的內容**|  
|------------|----------------|-------------|-----------------------|  
|any|`NULL`|`EINVAL`|未修改|  
|無效的模式|any|`EINVAL`|未修改|  
  
 如果以上任何一個錯誤情況發生，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行， `_umask_s` 會傳回 `EINVAL` 並設定 `errno` 為 `EINVAL`。  
  
## 備註  
 目前處理序檔案使用權限遮罩套用至這個模式的由 `mode`指定的 `_umask_s` 函式集*。*檔案使用權限遮罩修改 `_creat`、 `_open`或 `_sopen`建立的新檔案使用權限設定。  如果遮罩中的位元為 1，對應的位元檔案的要求的使用權限值設為 0 \(禁止\)。  如果遮罩中的位元為 0，對應的位元會保持不變。  新檔案的使用權限設定未設定，直到檔案第一次關閉。  
  
 整數運算式 `pmode` 包含定義於 SYS\\STAT.H 裏的下列資訊清單常值其一或兩者兼有的整數表達式。  
  
 `_S_IWRITE`  
 允許的寫入。  
  
 `_S_IREAD`  
 允許的讀取。  
  
 `_S_IREAD | _S_IWRITE`  
 允許讀取和寫入。  
  
 當給定兩個常值時，它們是以位元 OR 運算連接而已。         `|`  \).  如果 `mode` 引數為 `_S_IREAD`，將不允許 \(檔案唯寫\)。  如果 `mode` 引數為 `_S_IWRITE`，將不允許寫入 \(檔案唯讀\)。  例如，在中，如果寫入位元遮罩中設定，所有新的檔案是唯讀的。  請注意與 MS\-DOS 和 Windows 作業系統中，所有檔案是可讀取的;寫入唯寫權限是不可能的。  因此，設定會有 `_umask_s` 讀取的位元對檔案的方式產生任何影響。  
  
 如果 `pmode` 不是其中一個組件資訊清單常數也不會合併替代組常數，函式將會忽略參數。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_umask_s`|\<io.h 和\> sys \<\/stat.h 和 sys\> \/types.h \<\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_umask_s.c  
/* This program uses _umask_s to set  
 * the file-permission mask so that all future  
 * files will be created as read-only files.  
 * It also displays the old mask.  
 */  
  
#include <sys/stat.h>  
#include <sys/types.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int oldmask, err;  
  
   /* Create read-only files: */  
   err = _umask_s( _S_IWRITE, &oldmask );  
   if (err)  
   {  
      printf("Error setting the umask.\n");  
      exit(1);  
   }  
   printf( "Oldmask = 0x%.4x\n", oldmask );  
}  
```  
  
  **Oldmask \= 0x0000**   
## .NET Framework 對等用法  
 [System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_umask](../../c-runtime-library/reference/umask.md)