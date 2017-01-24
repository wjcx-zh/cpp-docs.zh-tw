---
title: "編譯器錯誤 CS0249 | Microsoft Docs"
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
  - "CS0249"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0249"
ms.assetid: 8bc3572f-d949-4867-b119-6527fb924a4a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0249
請勿覆寫 object.Finalize， 請改為提供解構函式。  
  
 請使用解構函式語法，來指定要在物件終結時執行的指示。  
  
 如需詳細資訊，請參閱 [C\# 及 C\+\+ 中的解構函式語法](http://msdn.microsoft.com/zh-tw/d7901491-7e89-4b6f-8270-0635aa6581b5)。  
  
 下列範例會產生 CS0249：  
  
```  
// CS0249.cs class MyClass { protected override void Finalize()   // CS0249 // try the following line instead // ~MyClass() { } public static void Main() { } }  
```