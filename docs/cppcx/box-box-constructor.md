---
title: "Box::Box 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::Box"
dev_langs: 
  - "C++"
ms.assetid: 3c4777f0-801c-4b24-9426-6d658dfaecf8
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Box::Box 建構函式
建立可封裝指定類型之值的 `Box`。  
  
## 語法  
  
```cpp  
Box(T valueArg);  
```  
  
#### 參數  
 `valueArg`  
 要處理為 boxed 之值的類型，例如 `int`、`bool`、`float64`、`DateTime`。  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform::Box 類別](../cppcx/platform-box-class.md)   
 [Boxing](../cppcx/boxing-c-cx.md)