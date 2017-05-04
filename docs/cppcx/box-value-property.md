---
title: "Box::Value 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::Value"
dev_langs: 
  - "C++"
ms.assetid: f456b105-6c14-4737-8c27-ad47d1eabd32
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Box::Value 屬性
傳回 `Box` 物件中封裝的值。  
  
## 語法  
  
```cpp  
virtual property T Value{  
   T get();  
}  
```  
  
## 傳回值  
 傳回 Boxed 值，與該值進行 Boxed 處理之前的原始類型相同。  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform::Box 類別](../cppcx/platform-box-class.md)   
 [Boxing](../cppcx/boxing-c-cx.md)