---
title: "這個 &#39;Sub New&#39; 的第一個陳述式必須呼叫 &#39;MyBase.New&#39; 或 &#39;MyClass.New&#39; (多個不含參數的可存取建構函式) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32038"
  - "bc32038"
helpviewer_keywords: 
  - "BC32038"
ms.assetid: 52e4e9df-a85b-46ae-a0cc-7d8fa377fe95
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 這個 &#39;Sub New&#39; 的第一個陳述式必須呼叫 &#39;MyBase.New&#39; 或 &#39;MyClass.New&#39; (多個不含參數的可存取建構函式)
此 'Sub New' 的第一個陳述式，必須呼叫 'MyBase.New' 或 'MyClass.New'，因為 '\<衍生\>' 的基底類別 '\<基底\>' 有一個以上不使用引數即可呼叫的可存取 'Sub New'。  
  
 類別建構函式不會提供對基底類別建構函式的呼叫，且 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 無法提供隱含的呼叫，因為它無法判斷要呼叫哪個基底類別建構函式。  
  
 **錯誤 ID︰**BC32038  
  
### 更正這個錯誤  
  
-   請使用 `MyClass.New()` 或 `Me.New()`，加入對基底類別建構函式 `MyBase.New()` 的呼叫，或對此類別之另一個建構函式的呼叫，作為這個建構函式的第一行。  
  
## 請參閱  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [MyBase \- delete](http://msdn.microsoft.com/zh-tw/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)