---
title: "String::Equals 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Equals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Equals"
ms.assetid: b0c78419-242d-4d38-93e3-ff2818412624
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Equals 方法
指出指定的字串是否擁有與目前物件相同的值。  
  
## 語法  
  
```cpp  
  
bool String::Equals(Object^ str);  
  
bool String::Equals(String^ str);  
  
```  
  
#### 參數  
 `str`  
 要比較的物件。  
  
## 傳回值  
 如果 `true` 等於目前物件則為 `str`，否則為 `false`。  
  
## 備註  
 這個方法與 [String::CompareOrdinal 方法](../cppcx/string-compareordinal-method.md)相同。 在第一個多載中，`str` 參數應該可以轉換成 String^ 物件。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)