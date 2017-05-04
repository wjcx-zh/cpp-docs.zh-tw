---
title: "Object::Equals 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::Equals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform, Object::Equals"
ms.assetid: 263ccd41-2a29-4716-a47e-4bf2883f3403
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::Equals 方法
判斷指定的物件是否等於目前的物件。  
  
## 語法  
  
```cpp  
  
bool Equals(  
    Object^ obj  
)  
```  
  
## 參數  
 obj  
 要比較的物件。  
  
## 傳回值  
 如果物件相等則為 `true`，否則為 `false`。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::Object 類別](../cppcx/platform-object-class.md)