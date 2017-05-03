---
title: "StringReference::operator() 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::StringReference::operator()"
dev_langs: 
  - "C++"
ms.assetid: d5c65e82-300c-44aa-b826-0afe1e3645b1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# StringReference::operator() 運算子
將 `StringReference` 物件轉換成 `Platform::String^` 物件。  
  
## 語法  
  
```cpp  
  
__declspec(no_release_return) __declspec(no_refcount)  
         operator ::Platform::String^() const  
  
```  
  
## 傳回值  
 `Platform::String` 類型之物件的控制代碼。  
  
## 備註  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::StringReference 類別](../cppcx/platform-stringreference-class.md)