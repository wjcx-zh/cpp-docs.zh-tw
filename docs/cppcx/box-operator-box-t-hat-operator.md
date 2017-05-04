---
title: "Box::operator Box&lt;T&gt;^ 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::operator Box<T>^"
dev_langs: 
  - "C++"
ms.assetid: c2c89385-c334-4b09-8f87-d46ea4809232
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Box::operator Box&lt;T&gt;^ 運算子
可以透過 Boxing 處理，從 `T` 實值類別轉換為 `Box<T>`。  
  
## 語法  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
#### 參數  
 `T`  
 任何列舉類型、實值類別或實值結構。[default 命名空間](../cppcx/default-namespace.md)中包含內建類型。  
  
## 傳回值  
 `Platform::Box<T>` `^` 執行個體，這個執行個體表示在 ref 類別中經過 Boxed 處理的原始值。  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform::Box 類別](../cppcx/platform-box-class.md)   
 [Platform::IBox 介面](../cppcx/platform-ibox-interface.md)   
 [Boxing](../cppcx/boxing-c-cx.md)