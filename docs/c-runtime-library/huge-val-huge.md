---
title: "HUGE_VAL、_HUGE | Microsoft Docs"
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
  - "_HUGE"
apilocation: 
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_HUGE"
  - "HUGE_VAL"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_HUGE 常數"
  - "HUGE_VAL 常數"
  - "雙精度浮點數值"
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# HUGE_VAL、_HUGE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <math.h>  
  
```  
  
## 備註  
 `HUGE_VAL` 是最大能顯示的雙精度浮點數值。  在發生錯誤時，這個值是由許多執行階段數學函式傳回。  有些函式則會傳回`HUGE_VAL` 。  `HUGE_VAL` 會定義為 `_HUGE`，但執行階段數學函式會傳回 `HUGE_VAL`。  為了一致性，您也應該在您的程式碼中使用 `HUGE_VAL` 。  
  
## 請參閱  
 [全域常數](../c-runtime-library/global-constants.md)