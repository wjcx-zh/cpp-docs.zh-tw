---
title: "_get_errno | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_errno"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_get_errno"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_errno 函式"
  - "errno 全域變數"
  - "get_errno 函式"
ms.assetid: b3fd5ebc-f41b-4314-a2f4-2f2d79d6e740
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_errno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得 errno 全域變數的目前值。  
  
## 語法  
  
```  
errno_t _get_errno(   
   int * pValue   
);  
```  
  
#### 參數  
 \[out\] `pValue`  
 out 要填入的整數的指標 `errno` 變數的目前值。  
  
## 傳回值  
 如果成功則回傳零，如果失敗則為錯誤碼。  如果 `pValue` 為 `NULL`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `EINVAL` 。  
  
## 備註  
 `errno`的可能值會定義在Errno.h中。  請參閱[errno 常數](../../c-runtime-library/errno-constants.md)。  
  
## 範例  
  
```  
// crt_get_errno.c  
#include <stdio.h>  
#include <fcntl.h>  
#include <sys/stat.h>  
#include <share.h>  
#include <errno.h>  
  
int main()  
{  
   errno_t err;  
   int pfh;  
   _sopen_s( &pfh, "nonexistent.file", _O_WRONLY, _SH_DENYNO, _S_IWRITE );  
   _get_errno( &err );  
   printf( "errno = %d\n", err );  
   printf( "fyi, ENOENT = %d\n", ENOENT );  
}  
```  
  
  **errno \= 2**  
**fyi， ENOENT \= 2**   
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_get_errno`|\<stdlib.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## NET Framework 對等  
 不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_set\_errno](../../c-runtime-library/reference/set-errno.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)