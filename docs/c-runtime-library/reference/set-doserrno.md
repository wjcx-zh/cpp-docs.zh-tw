---
title: "_set_doserrno | Microsoft Docs"
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
  - "_set_doserrno"
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
  - "_set_doserrno"
  - "set_doserrno"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_doserrno 全域變數"
  - "_set_doserrno 函式"
  - "doserrno 全域變數"
  - "set_doserrno 函式"
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_doserrno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定 [\_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 全域變數的值。  
  
## 語法  
  
```  
errno_t _set_doserrno(   
   int value   
);  
```  
  
#### 參數  
 \[in\] `value`  
 `_doserrno` 的新值。  
  
## 傳回值  
 如果成功，則傳回 0。  
  
## 備註  
 可能的值會在Errno.h中定義。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_set_doserrno`|\<stdlib.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 請參閱  
 [\_get\_doserrno](../../c-runtime-library/reference/get-doserrno.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)