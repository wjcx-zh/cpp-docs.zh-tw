---
title: "_set_fmode | Microsoft Docs"
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
  - "_set_fmode"
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
  - "_set_fmode"
  - "set_fmode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_fmode 函式"
  - "檔案轉譯 [C++], 預設模式"
  - "檔案轉譯 [C++], 設定模式"
  - "set_fmode 函式"
ms.assetid: f80eb9c7-733b-4652-a9bc-6b3790a35f12
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_fmode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定檔案 I\/O 作業的預設檔案傳輸模式。  
  
## 語法  
  
```  
errno_t _set_fmode(   
   int mode   
);  
```  
  
#### 參數  
 \[in\] `mode`  
 所需的檔案版本模式: `_O_TEXT` 或 `_O_BINARY`。  
  
## 傳回值  
 如果成功則回傳零，如果失敗則為錯誤碼。  如果 `mode` 不為 `_O_TEXT` 或 `_O_BINARY` 或 `_O_WTEXT`，則會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `EINVAL` 。  
  
## 備註  
 函式會設定 [\_fmode](../../c-runtime-library/fmode.md) 全域變數。  這個變數指定檔案 I\/O 作業 `_open` 和 `_pipe` 預設的傳輸模式。  
  
 `_O_TEXT` 和 `_O_BINARY` 是在 Fcntl.h 中定義的。  `EINVAL` 在 Errno.h 定義。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_set_fmode`|\<stdlib.h\>|\<fcntl.h\>, \<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_set_fmode.c  
#include <stdlib.h>  
#include <stdio.h>  
#include <fcntl.h>     /* for _O_TEXT and _O_BINARY */  
#include <errno.h>     /* for EINVAL */  
#include <sys\stat.h>  /* for _S_IWRITE */  
#include <share.h>     /* for _SH_DENYNO */  
  
int main()  
{  
   int mode, fd, ret;  
   errno_t err;  
   int buf[12] = { 65, 66, 67, 68, 69, 70, 71, 72, 73, 74,  
                   75, 76 };  
   char * filename = "fmode.out";  
  
   err = _get_fmode(&mode);  
   if (err == EINVAL)  
   {  
      printf( "Invalid parameter: mode\n");  
      return 1;  
   }  
   else  
      printf( "Default Mode is %s\n", mode == _O_TEXT ? "text" :  
              "binary");  
  
   err = _set_fmode(_O_BINARY);  
   if (err == EINVAL)  
   {  
      printf( "Invalid mode.\n");  
      return 1;  
   }  
  
   if ( _sopen_s(&fd, filename, _O_RDWR | _O_CREAT, _SH_DENYNO, _S_IWRITE | _S_IREAD) != 0 )  
   {  
      printf( "Error opening the file %s\n", filename);  
      return 1;  
   }  
  
   if (ret = _write(fd, buf, 12*sizeof(int)) < 12*sizeof(int))  
   {  
      printf( "Problem writing to the file %s.\n", filename);  
      printf( "Number of bytes written: %d\n", ret);  
   }  
  
   if (_close(fd) != 0)  
   {  
      printf("Error closing the file %s. Error code %d.\n",  
             filename, errno);  
   }  
  
   system("type fmode.out");  
}  
```  
  
  **Default Mode is binary**  
**A   B   C   D   E   F   G   H   I   J   K   L**   
## 請參閱  
 [\_fmode](../../c-runtime-library/fmode.md)   
 [\_get\_fmode](../../c-runtime-library/reference/get-fmode.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [文字和二進位模式檔案 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)