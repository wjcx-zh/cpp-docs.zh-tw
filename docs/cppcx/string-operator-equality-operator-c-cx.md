---
title: "String::operator== 運算子 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::operator=="
ms.assetid: c804b269-64f9-4bc0-929b-2dfa87bf46ac
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::operator== 運算子 (C++/CX)
指出兩個指定的 String 物件是否具有相同的文字值。  
  
## 語法  
  
```cpp  
  
bool String::operator==( String^ str1,  
                         String^ str2)  
  
```  
  
#### 參數  
 `str1`  
 要比較的第一個 String 物件。  
  
 `str2`  
 要比較的第二個 String 物件。  
  
## 傳回值  
 如果 `true` 和 `str1` 的內容相等，則為 `str2`，否則為 `false`。  
  
## 備註  
 這個運算子與 [String::CompareOrdinal 方法](../cppcx/string-compareordinal-method.md)相同。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)