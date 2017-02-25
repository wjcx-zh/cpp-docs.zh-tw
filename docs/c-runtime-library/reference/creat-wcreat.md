---
title: "_creat、_wcreat | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_creat"
  - "_wcreat"
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
  - "wcreat"
  - "_wcreat"
  - "_creat"
  - "tcreat"
  - "_tcreat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wcreat 函式"
  - "_wcreat 函式"
  - "檔案 [C#], 建立"
  - "_creat 函式"
  - "tcreat 函式"
  - "creat 函式"
  - "_tcreat 函式"
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _creat、_wcreat
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立新檔案。  `_creat` 和 `_wcreat` 已被取代；使用 [\_sopen\_s、\_wsopen\_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md) 。  
  
## 語法  
  
```  
int _creat(   
   const char *filename,  
   int pmode   
);  
int _wcreat(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### 參數  
 `filename`  
 新檔案的名稱。  
  
 `pmode`  
 使用權限設定。  
  
## 傳回值  
 這些函式，如果成功則傳回建立檔案的檔案描述項。  否則，如下表所示，函式會傳回 – 1 和 `errno` 集合。  
  
|`errno` 設定|說明|  
|----------------|--------|  
|`EACCES`|`filename` 指定一個現有唯讀檔或指定目錄而非檔案。|  
|`EMFILE`|沒有可用的檔案描述。|  
|`ENOENT`|找不到指定的檔案。|  
  
 如果 `filename` 為 NULL，則會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 \-1。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 、和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `_creat` 函式會建立新的檔案或開啟並縮短現有項目。  `_wcreat` 是 `_creat` 的寬字元版本。 `_wcreat` 的 `filename` 引數是寬字元字串。  `_wcreat` 和 `_creat` 其餘行為相同。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tcreat`|`_creat`|`_creat`|`_wcreat`|  
  
 如果 `filename` 指定的檔案不存在，則建立新檔案。與特定使用權限集合和撰寫開啟。  如果檔案已經存在，而且它的使用權限設定為允許寫入， `_creat` 截斷檔案對長度為 0，終結目前的內容，並開啟它來寫入。  使用權限設定，`pmode`，只適用於新建立的檔案。  在第一次關閉後，新的檔案接收指定的使用權限設定。  整數運算式 `pmode` 包含定義於 SYS\\Stat.h 裏的表示常值 `_S_IWRITE` 和 `_S_IREAD` 其一或兩者兼有的整數表達式。  當給定兩個常值時，它們以位元連接藉由 `OR` 運算子\(  **&#124;**\).  `pmode` 參數會設為下列其中一個值。  
  
|值|定義|  
|-------|--------|  
|`_S_IWRITE`|允許的寫入。|  
|`_S_IREAD`|允許的讀取。|  
|`_S_IREAD &#124; _S_IWRITE`|允許讀取和寫入。|  
  
 如果沒有寫入權限，則檔案是唯讀的。  所有檔案都是可讀取的；唯寫權限是不可能的。  模式 `_S_IWRITE` 和 `_S_IREAD``| _S_IWRITE` 模式等價。  使用 `_creat` 開啟的檔案在相容性模式永遠開啟 \(請參閱 [\_sopen](../../c-runtime-library/reference/sopen-wsopen.md)\) 的 `_SH_DENYNO`。  
  
 `_creat` 在設定存取權限之前提供 `pmode` 目前的檔案存取權限遮罩 \(請參閱 [\_umask](../../c-runtime-library/reference/umask.md)\) 。  `_creat` 是主要為了前一個程式庫的相容性所提供。  `_open` 和 `_O_CREAT` 和 `_O_TRUNC` 的呼叫中以 `oflag` 參數等於 `_creat` 且指定新程式碼為較好的。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_creat`|\<io.h\>|\<sys\/types.h\>, \<sys\/stat.h\>, \<errno.h\>|  
|`_wcreat`|\<io.h\> or \<wchar.h\>|\<sys\/types.h\>, \<sys\/stat.h\>, \<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_creat.c  
// compile with: /W3  
// This program uses _creat to create  
// the file (or truncate the existing file)  
// named data and open it for writing.  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int fh;  
  
   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996  
   // Note: _creat is deprecated; use _sopen_s instead  
   if( fh == -1 )  
      perror( "Couldn't create data file" );  
   else  
   {  
      printf( "Created data file.\n" );  
      _close( fh );  
   }  
}  
```  
  
  **建立的資料檔案。**   
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_dup、\_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_sopen、\_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [\_umask](../../c-runtime-library/reference/umask.md)