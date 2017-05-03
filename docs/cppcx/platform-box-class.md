---
title: "Platform::Box 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box"
dev_langs: 
  - "C++"
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Box 類別
允許將實值類型 \(例如 `Windows::Foundation::DateTime`\) 或純量類型 \(例如 `int`\) 儲存在 `Platform::Object` 類型中。 通常不需要明確使用 `Box`，因為當您將實值類型轉換成 `Object^` 時，將會隱含地進行 Boxing 作業。  
  
## 語法  
  
```cpp  
ref class Box abstract;  
```  
  
## 備註  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)   
 [Boxing](../cppcx/boxing-c-cx.md)