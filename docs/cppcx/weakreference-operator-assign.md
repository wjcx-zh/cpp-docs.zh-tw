---
title: "WeakReference::operator= | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/WeakReference::operator="
ms.assetid: 20b034d1-8f4f-46ae-81f0-73b76599f86b
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WeakReference::operator=
指派值給 WeakReference。  
  
## 語法  
  
```cpp  
WeakReference& operator=(decltype(__nullptr));  
  
WeakReference& operator=(const WeakReference& __otherArg);  
  
WeakReference& operator=(WeakReference&& __otherArg);  
  
WeakReference& operator=(const volatile ::Platform::Object^ const __otherArg);  
  
```  
  
## 備註  
 上述清單中的最後一個多載可讓您指派 ref 類別給 WeakReference 變數。 在這種情況下，ref 類別會向下轉型為 [Platform::Object](../cppcx/platform-object-class.md)^。 您可以在稍後於 [WeakReference::Resolve\<T\>](../cppcx/weakreference-resolve-method-platform-namespace.md) 成員函式中，指定它做為類型參數的引數以還原原始類型。  
  
## 需求  
 Windows 8.0 \(含\) 以後版本  
  
## 請參閱  
 [Platform::WeakReference 類別](../cppcx/platform-weakreference-class.md)