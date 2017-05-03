---
title: "String::operator&gt;= 運算子 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::operator>="
ms.assetid: 58cc458f-e82c-4024-b0c5-7f66941bc8aa
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::operator&gt;= 運算子 (C++/CX)
指出其中一個 String 物件的值是否大於或等於另一個 String 物件的值。  
  
## 語法  
  
```cpp  
  
bool String::operator>=( String^ str1,  
                         String^ str2)  
  
```  
  
#### 參數  
 `str1`  
 第一個 String 物件。  
  
 `str2`  
 第二個 String 物件。  
  
## 傳回值  
 如果 `str1` 的值大於或等於 `str2` 的值，則為 `true`，否則為 `false`。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)