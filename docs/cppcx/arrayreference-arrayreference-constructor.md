---
title: "ArrayReference::ArrayReference 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::ArrayReference::ArrayReference"
dev_langs: 
  - "C++"
ms.assetid: 9fc7dfcf-47af-40ba-a697-da476fb90efc
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# ArrayReference::ArrayReference 建構函式
初始化 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 類別的新執行個體。  
  
## 語法  
  
```cpp  
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);  
ArrayReference(ArrayReference&& otherArg)  
  
```  
  
#### 參數  
 `dataArg`  
 陣列資料的指標。  
  
 `sizeArg`  
 來源陣列中的元素數目。  
  
 `otherArg`  
 將會移動其資料來初始化新執行個體的 `ArrayReference` 物件。  
  
## 備註  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::ArrayReference 類別](../cppcx/platform-arrayreference-class.md)   
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)