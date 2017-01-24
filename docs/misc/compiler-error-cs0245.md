---
title: "編譯器錯誤 CS0245 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0245"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0245"
ms.assetid: 3f2beb2f-a510-4568-9d11-bb1f65066acd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0245
不能直接呼叫解構函式和 object.Finalize。 請考慮呼叫 IDisposable.Dispose \(如果有\)。  
  
 如需詳細資訊，請參閱[進行記憶體回收的程式設計基本項目](../Topic/Garbage%20Collection.md)和[解構函式](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0245：  
  
```  
// CS0245.cs using System; using System.Collections; class MyClass // : IDisposable { /* public void Dispose() { // cleanup code goes here } */ void m() { this.Finalize();   // CS0245 // this.Dispose(); } public static void Main() { } }  
```