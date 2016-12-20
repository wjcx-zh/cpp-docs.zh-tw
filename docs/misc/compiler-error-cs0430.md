---
title: "編譯器錯誤 CS0430 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0430"
ms.assetid: b63c4f9a-b1cd-41d2-a02e-2ed0f177450f
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0430
\/reference 選項中沒有指定外部別名 'alias'  
  
 當遇到外部別名但未將別名指定為命令列上的參考時，就會發生這個錯誤。 若要解決 CS0430，請使用 **\/reference** 進行編譯。  
  
## 範例  
  
```  
// CS0430_a.cs // compile with: /target:library public class MyClass {}  
```  
  
## 範例  
 使用 **\/reference:MyType\=cs0430\_a.dll** 進行編譯，以參考先前範例中所建立的 DLL 即可解決這個錯誤。 下列範例會產生 CS0430。  
  
```  
// CS0430_b.cs extern alias MyType;   // CS0430 public class Test { public static void Main() {} }  
  
```