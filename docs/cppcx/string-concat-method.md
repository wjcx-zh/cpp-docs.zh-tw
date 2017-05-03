---
title: "String::Concat 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Concat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Concat"
ms.assetid: 68052d22-3df0-4777-828d-fc3a8e8a3ab7
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Concat 方法
串連兩個 String 物件的值。  
  
## 語法  
  
```cpp  
  
String^ Concat( String ^ str1,   
String ^ str2  
)  
  
```  
  
#### 參數  
 `str1`  
 第一個 String 物件，或 `null`。  
  
 `str2`  
 第二個 String 物件，或 `null`。  
  
## 傳回值  
 由 `str1` 與 `str2` 兩者的值串連後得出其值的新 String^ 物件。  
  
 如果 `str1` 為 `null` 而 `str2` 不是，則會傳回`str1` 。 如果 `str2` 為 `null` 而 `str1` 不是，則會傳回 `str2`。 如果 `str1` 與 `str2` 都是 `null`，則會傳回空字串 \(L""\)。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)