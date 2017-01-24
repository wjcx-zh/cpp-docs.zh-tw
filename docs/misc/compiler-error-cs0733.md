---
title: "編譯器錯誤 CS0733 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0733"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0733"
ms.assetid: 1b0150e0-48d3-4b9c-85cc-27346e4f5f84
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0733
無法轉送泛型類型 'GenericType\<\>'  
  
## 範例  
 下列範例會產生 CS0733。 請將第一個檔案編譯為程式庫，然後在編譯第二個檔案時參考這個檔案。  
  
```  
// CS0733a.cs // compile with: /target:library public class GenericType<T> { }  
```  
  
```  
// CS0733.cs // compile with: /target:library /r:CS0733a.dll [assembly: System.Runtime.CompilerServices.TypeForwardedTo(typeof(GenericType<int>))]   // CS0733  
```