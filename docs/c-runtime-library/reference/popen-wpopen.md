---
title: "_popen、_wpopen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_popen"
  - "_wpopen"
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
  - "tpopen"
  - "popen"
  - "wpopen"
  - "_popen"
  - "_wpopen"
  - "_tpopen"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_popen 函式"
  - "_tpopen 函式"
  - "_wpopen 函式"
  - "管道, 建立"
  - "popen 函式"
  - "tpopen 函式"
  - "wpopen 函式"
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _popen、_wpopen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立管道並執行命令。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
  
      FILE *_popen(  
const char *command,  
const char *mode   
);  
FILE *_wpopen(  
const wchar_t *command,  
const wchar_t *mode   
);  
```  
  
#### 參數  
 *Command \- 命令*  
 要執行的命令。  
  
 *mode*  
 傳回資料流的模式。  
  
## 傳回值  
 傳回與建立的管道的一端相連的資料流。  管道另一端與產生的命令的標準輸入或標準輸出相連。  函式在錯誤時傳回 **NULL** 。  如果錯誤是不正確的參數，例如，如果 *命令* 或 *模式* 為 null 指標，或 *模式* 不是有效的方式， `errno` 設定為 `EINVAL`。  如需有效模式，請參閱 \< 備註 \> 一節。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_popen` 函式會建立管道且以指定的 *命令*字串非同步執行命令處理器的產生的複本。  字串 *模式* 指定要求的存取形式，如下所示。  
  
 **"r"**  
 使用傳回的資料流，呼叫程序可以讀取命令的標準輸出。  
  
 **"w"**  
 使用傳回的資料流，呼叫程序可以寫入的命令產生的標準輸入。  
  
 **"b"**  
 開啟二進位模式。  
  
 **"t"**  
 以文字模式開啟。  
  
> [!NOTE]
>  如果使用在 Windows 程式， `_popen` 函式會傳回造成程式停止無限期回覆的無效檔案指標。  `_popen` 在主控台應用程式正確運作。  若要建立重新輸入和輸出導向的 Windows 應用程式，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)]的 [建立重新導向的輸入和輸出的子處理序](http://msdn.microsoft.com/library/windows/desktop/ms682499) 。  
  
 `_wpopen` 是 `_popen` 的寬字元版本。 `_wpopen` 的 *path* 引數是寬字元字串。  `_wpopen` 和 `_popen` 其餘行為相同。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tpopen`|`_popen`|`_popen`|`_wpopen`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_popen`|\<stdio.h\>|  
|`_wpopen`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_popen.c  
/* This program uses _popen and _pclose to receive a   
 * stream of text from a system process.  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
  
   char   psBuffer[128];  
   FILE   *pPipe;  
  
        /* Run DIR so that it writes its output to a pipe. Open this  
         * pipe with read text attribute so that we can read it   
         * like a text file.   
         */  
  
   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )  
      exit( 1 );  
  
   /* Read pipe until end of file, or an error occurs. */  
  
   while(fgets(psBuffer, 128, pPipe))  
   {  
      printf(psBuffer);  
   }  
  
   /* Close pipe and print return value of pPipe. */  
   if (feof( pPipe))  
   {  
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );  
   }  
   else  
   {  
     printf( "Error: Failed to read the pipe to the end.\n");  
   }  
}  
```  
  
## 範例輸出  
 這個輸出假設在目前目錄中只有一個的檔案的副檔名為 .c。  
  
```  
 Volume in drive C is CDRIVE  
 Volume Serial Number is 0E17-1702  
  
 Directory of D:\proj\console\test1  
  
07/17/98  07:26p                   780 popen.c  
               1 File(s)            780 bytes  
                             86,597,632 bytes free  
  
Process returned 0  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_pclose](../../c-runtime-library/reference/pclose.md)   
 [\_pipe](../../c-runtime-library/reference/pipe.md)