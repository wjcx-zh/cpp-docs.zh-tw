---
title: "編譯器錯誤 CS0012 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0012"
ms.assetid: 5523e349-22f4-4b0b-b4b0-c4bf26c461f4
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0012
類型 'type' 定義在未被參考的組件中。 您必須加入對組件 'assembly' 的參考。  
  
 找不到參考類型的定義。 如果必要的 DLL 檔案未包含在編譯中，就會發生此狀況。 如需詳細資訊，請參閱[Add Reference Dialog Box](http://msdn.microsoft.com/zh-tw/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)與[\/reference \(Import Metadata\)](../Topic/-reference%20\(C%23%20Compiler%20Options\).md)。  
  
 下列編譯序列將會導致 CS0012：  
  
```  
// cs0012a.cs // compile with: /target:library public class A {}  
```  
  
 然後：  
  
```  
// cs0012b.cs // compile with: /target:library /reference:cs0012a.dll public class B { public static A f() { return new A(); } }  
```  
  
 然後：  
  
```  
// cs0012c.cs // compile with: /reference:cs0012b.dll class C { public static void Main() { object o = B.f();   // CS0012 } }  
```  
  
 您可以使用 `/reference:cs0012b.dll;cs0012a.dll` 編譯來解決這個 CS0012，或在 Visual Studio 中使用 [Add Reference Dialog Box](http://msdn.microsoft.com/zh-tw/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) 來加入 cs0012b.dll 和 cs0012a.dll 的參考。