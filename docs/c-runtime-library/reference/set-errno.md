---
title: "_set_errno | Microsoft Docs"
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
  - "_set_errno"
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
  - "set_errno"
  - "_set_errno"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_errno 函式"
  - "errno 全域變數"
  - "set_errno 函式"
ms.assetid: d338914a-1894-4cf3-ae45-f2c4eb26590b
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_errno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定 `errno` 全域變數的值。  
  
## 語法  
  
```  
errno_t _set_errno(   
   int value   
);  
```  
  
#### 參數  
 \[in\] `value`  
 `errno` 的新值。  
  
## 傳回值  
 如果成功，則傳回 0。  
  
## 備註  
 可能的值會在Errno.h中定義。  請參閱[errno 常數](../../c-runtime-library/errno-constants.md)。  
  
## 範例  
  
```  
// crt_set_errno.c  
#include <stdio.h>  
#include <errno.h>  
  
int main()  
{  
   _set_errno( EILSEQ );  
   perror( "Oops" );  
}  
```  
  
  **Oops:不合法的位元組序列。**   
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_set_errno`|\<stdlib.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 請參閱  
 [\_get\_errno](../../c-runtime-library/reference/get-errno.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)