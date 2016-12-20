---
title: "編譯器錯誤 CS0739 | Microsoft Docs"
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
  - "CS0739"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0739"
ms.assetid: c2a83015-401c-4d85-bb19-ed29800904c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0739
'type name' 與 TypeForwardedToAttribute 重複。  
  
 組件的外部類型不能有多個 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>。  
  
### 更正這個錯誤  
  
1.  請找到並移除重複的 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>。  
  
## 範例  
 下列程式碼會產生 CS0739：  
  
```  
// CS0739.cs // CS0739 // Assume that a class Test is declared in a separate dll // with a namespace that is named cs739dll. [assembly: System.Runtime.CompilerServices.TypeForwardedTo(typeof(cs739dll.Test))] [assembly: System.Runtime.CompilerServices.TypeForwardedTo(typeof(cs739dll.Test))] namespace cs0739 { class Program { static void Main(string[] args) { } } }  
```  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>