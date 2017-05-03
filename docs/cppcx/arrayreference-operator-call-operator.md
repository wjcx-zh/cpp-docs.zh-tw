---
title: "ArrayReference::operator() 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::ArrayReference::operatorArray^"
dev_langs: 
  - "C++"
ms.assetid: 48726344-82bb-4c1d-b246-ed74b895f99b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# ArrayReference::operator() 運算子
將目前的 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 物件轉換回 [Platform::Array](../cppcx/platform-array-class.md) 類別。  
  
## 語法  
  
```cpp  
  
Array<__TArg>^ operator ();  
  
```  
  
## 傳回值  
 `Array<__TArg>^` 類型之物件的控制代碼  
  
## 備註  
 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 和 [Platform::Array](../cppcx/platform-array-class.md) 是標準 C\+\+ 類別樣板，而不是 ref 類別。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::ArrayReference 類別](../cppcx/platform-arrayreference-class.md)