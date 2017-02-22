---
title: "__RTDynamicCast | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__RTDynamicCast"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__RTDynamicCast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__RTDynamicCast"
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# __RTDynamicCast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[dynamic\_cast](../cpp/dynamic-cast-operator.md) 運算子的執行階段實作。  
  
## 語法  
  
```cpp  
PVOID __RTDynamicCast (  
   PVOID inptr,   
   LONG VfDelta,  
   PVOID SrcType,  
   PVOID TargetType,   
   BOOL isReference  
   ) throw(...)  
```  
  
#### 參數  
 `inptr`  
 多型物件的指標。  
  
 `VfDelta`  
 物件中虛擬函式指標的位移。  
  
 `SrcType`  
 `inptr` 參數指向的對靜態物件。  
  
 `TargetType`  
 轉型的預期的結果。  
  
 `isReference`  
 如果輸入是參考，則是`true`；如果輸入是指標，則是`false` 。  
  
## 傳回值  
 如果成功，則為對適當的子物件的指標；否則，則為NULL。  
  
## 例外狀況  
 如果輸入至`dynamic_cast<>`的是指標而且轉換失敗，則為`bad_cast()`。  
  
## 備註  
 將 `inptr` 型別轉換為 `TargetType` 型別的的物件 。  如果 `TargetType` 是指標，`inptr` 的型別必須為指標，或是如果 `TargetType` 為參考，它就是 l\-value。  `TargetType` 必須是指向先前定義的類別或是 「空指標」的指標或參考。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_\_RTDynamicCast|rtti.h|