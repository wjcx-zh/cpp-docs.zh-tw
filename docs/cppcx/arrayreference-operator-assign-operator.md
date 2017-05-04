---
title: "ArrayReference::operator= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::ArrayReference::operator="
dev_langs: 
  - "C++"
ms.assetid: 131a4612-d66b-48e4-90af-c665ccc0cce4
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# ArrayReference::operator= 運算子
使用移動語意，將指定的物件指定給目前的 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 物件。  
  
## 語法  
  
```cpp  
  
ArrayReference& operator=(ArrayReference&& __otherArg);  
  
```  
  
#### 參數  
 `__ otherArg`  
 移至目前 `ArrayReference` 物件的物件。  
  
## 傳回值  
 類型為 `ArrayReference` 之物件的參考。  
  
## 備註  
 `Platform::ArrayReference` 是標準 C\+\+ 類別樣板，而不是 ref 類別。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::ArrayReference 類別](../cppcx/platform-arrayreference-class.md)