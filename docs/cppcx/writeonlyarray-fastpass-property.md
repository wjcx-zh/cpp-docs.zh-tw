---
title: "WriteOnlyArray::FastPass 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::FastPass"
dev_langs: 
  - "C++"
ms.assetid: f7a54ae0-afa0-4728-8736-c63933f789aa
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::FastPass 屬性
表示是否可以執行內部 FastPass 最佳化。 不適合由使用者程式碼所使用。  
  
## 語法  
  
```cpp  
property bool FastPass{  
   bool get() const;  
}  
```  
  
## 傳回值  
 表示陣列是否為 FastPass 的布林值。  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform::WriteOnlyArray 類別](../cppcx/platform-writeonlyarray-class.md)