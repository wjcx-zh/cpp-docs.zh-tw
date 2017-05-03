---
title: "String::IsEmpty 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::IsEmpty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::IsEmpty"
ms.assetid: 4b651706-eace-4055-a694-d9e26a03ce05
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::IsEmpty 方法
指出目前 String 物件是否為空。  
  
## 語法  
  
```cpp  
  
bool IsEmpty()  
```  
  
## 傳回值  
 如果目前 String 物件為 `true` 或空字串 \(L""\) 則為 `null`，否則為 `false`。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**vccorlib.h  
  
## 請參閱  
 [Platform::String 類別](../cppcx/platform-string-class.md)