---
title: "Object::ReferenceEquals 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::ReferenceEquals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform, Object::ReferenceEquals"
ms.assetid: a179e74a-46c7-4bfd-b848-b89ef3ff7197
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::ReferenceEquals 方法
判斷指定的物件執行個體是否為相同的執行個體。  
  
## 語法  
  
```cpp  
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2)  
```  
  
## 參數  
 obj1  
 要比較的第一個物件。  
  
 obj2  
 要比較的第二個物件。  
  
## 傳回值  
 如果這兩個物件相同則為 `true`，否則為 `false`。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::Object 類別](../cppcx/platform-object-class.md)