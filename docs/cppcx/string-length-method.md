---
title: "String::Length 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Length"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Length"
ms.assetid: 92376897-1bf2-4b7a-9298-d2d3f05d8d6b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Length 方法
擷取目前 String 物件中的字元數。  
  
## 語法  
  
```cpp  
  
unsigned int Length()  
```  
  
## 傳回值  
 目前 String 物件中的字元數。  
  
## 備註  
 String 的長度，其中沒有字元為零。 以下字串的長度為 5：  
  
```  
  
String^ str = "Hello";  
int len = str->Length(); //len = 5  
```  
  
 [String::Data 方法](../cppcx/string-data-method.md) 傳回的字元陣列有一個額外字元，它是結尾 NULL 或 ‘\\0’。 這個字元的長度也是兩個位元組。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)