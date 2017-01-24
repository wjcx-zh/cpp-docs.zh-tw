---
title: "編譯器警告 (層級 1) CS3015 | Microsoft Docs"
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
  - "CS3015"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3015"
ms.assetid: 58182215-0c2f-4497-8baf-ffb29f18d6c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3015
'method signature' 沒有僅使用符合 CLS 標準之類型的可存取建構函式  
  
 若要符合 Common Language Specification \(CLS\) 規範，屬性類別的引數清單就不能包含陣列。 如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 範例  
 下列範例會產生 C3015。  
  
```  
// CS3015.cs // compile with: /target:library using System; [assembly:CLSCompliant(true)] public class MyAttribute : Attribute { public MyAttribute(int[] ai) {}   // CS3015 // try the following line instead // public MyAttribute(int ai) {} }  
```