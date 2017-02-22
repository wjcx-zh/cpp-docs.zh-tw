---
title: "__max | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__max"
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
apitype: "DLLExport"
f1_keywords: 
  - "max"
  - "__max"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__max 巨集"
  - "max 巨集"
  - "maximum 巨集"
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __max
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

回傳兩個值中的較大者。  
  
## 語法  
  
```  
type __max(  
   type a,  
   type b   
);  
```  
  
#### 參數  
 `type`  
 任何數字資料型別。  
  
 `a, b`  
 欲比較的兩個數值型別資料。  
  
## 傳回值  
 `__max` 回傳它的兩個參數中的較大者。  
  
## 備註  
 `__max` 巨集比較兩個數值並回傳較大者的數值。  參數可以是任何數值型別資料，有號或無號。  兩個引數和回傳值都必須是相同的資料型別。  
  
## 需求  
  
|程序|必要的標頭檔|  
|--------|------------|  
|`__max`|\<stdlib.h\>|  
  
## 範例  
 如需詳細資訊，請參閱 [\_\_min](../../c-runtime-library/reference/min.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::Math::Max](https://msdn.microsoft.com/en-us/library/system.math.max.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_\_min](../../c-runtime-library/reference/min.md)