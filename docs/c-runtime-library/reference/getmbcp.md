---
title: "_getmbcp | Microsoft Docs"
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
  - "_getmbcp"
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
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_getmbcp"
  - "getmbcp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getmbcp 函式"
  - "字碼頁, 判斷目前的"
  - "getmbcp 函式"
ms.assetid: 2db202d4-5c3d-4871-a0b8-ceb0b79ee7bb
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getmbcp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取目前的字碼頁。  
  
## 語法  
  
```  
int _getmbcp( void );  
```  
  
## 傳回值  
 傳回目前多位元組字碼頁。  傳回值 0 表示單一位元組字碼頁正在使用中。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getmbcp`|\<mbctype.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)