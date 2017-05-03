---
title: "StringReference::operator= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::StringReference::operator="
dev_langs: 
  - "C++"
ms.assetid: 03a33467-d65f-4508-bcb4-17d7cc99398f
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# StringReference::operator= 運算子
將指定的物件指定給目前的 `StringReference` 物件。  
  
## 語法  
  
```cpp  
  
   StringReference& operator=(const StringReference& __fstrArg);  
  
StringReference& operator=(const ::default::char16* __strArg);  
  
```  
  
#### 參數  
 `__fstrArg`  
 用來初始化目前 `StringReference` 物件之 `StringReference` 物件的位址。  
  
 `__strArg`  
 用來初始化目前 `StringReference` 物件之 char16 值陣列的指標。  
  
## 傳回值  
 類型為 `StringReference` 之物件的參考。  
  
## 備註  
 因為 `StringReference` 是標準 C\+\+ 類別而不是 ref 類別，所以它不會出現在 \[**物件瀏覽器**\] 中。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::StringReference 類別](../cppcx/platform-stringreference-class.md)