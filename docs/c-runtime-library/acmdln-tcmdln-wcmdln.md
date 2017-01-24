---
title: "_acmdln、_tcmdln、_wcmdln | Microsoft Docs"
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
  - "_wcmdln"
  - "_acmdln"
apilocation: 
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_acmdln"
  - "acmdln"
  - "_wcmdln"
  - "wcmdln"
  - "_tcmdln"
  - "tcmdln"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_acmdln 全域變數"
  - "_tcmdln 全域變數"
  - "_wcmdln 全域變數"
  - "acmdln 全域變數"
  - "tcmdln 全域變數"
  - "wcmdln 全域變數"
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _acmdln、_tcmdln、_wcmdln
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內部 CRT 全域變數。  命令列。  
  
## 語法  
  
```  
char * _acmdln; wchar_t * _wcmdln;  #ifdef WPRFLAG    #define _tcmdln _wcmdln #else    #define _tcmdln _acmdln  
```  
  
## 備註  
 這些 CRT 內部變數會儲存完整的命令列。  這些變數會在 CRT 的已匯出符號中公開，而不是供您用於程式碼中。  `_acmdln` 將資料儲存為字元字串。  `_wcmdln` 將資料儲存為寬字元字串。  `_tcmdln` 可定義為 `_acmdln` 或  `_wcmdln`，這要取決於哪個較合適。  
  
## 請參閱  
 [全域變數](../c-runtime-library/global-variables.md)