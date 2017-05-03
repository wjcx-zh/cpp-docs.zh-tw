---
title: "Object::ToString 方法 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::ToString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform, Object::ToString"
ms.assetid: 229dbf1c-cb43-4ed2-a1c5-a1f36b22a7ea
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::ToString 方法 (C++/CX)
傳回代表目前物件的字串。  
  
## 語法  
  
```cpp  
public:  
virtual String^ ToString()  
```  
  
## 傳回值  
 表示目前物件的字串。 您可以在 ref 類別或結構中覆寫這個方法，提供自訂字串訊息：  
  
```cpp  
public ref class Tree sealed { public: Tree(){} virtual Platform::String^ ToString()override { return "I’m a Tree"; }; };  
```  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::Object 類別](../cppcx/platform-object-class.md)