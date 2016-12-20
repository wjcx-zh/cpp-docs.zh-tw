---
title: "編譯器警告 (層級 1) CS3017 | Microsoft Docs"
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
  - "CS3017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3017"
ms.assetid: 8e56b2f0-9caf-4c9a-98c2-d3ad0b70e767
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3017
在模組上指定的 CLSCompliant 屬性不能與組件上的 CLSCompliant 屬性不同  
  
 如果您所擁有之組件的 CLSCompliant 屬性與模組的 CLSCompliant 屬性衝突，就會發生這個警告。 符合 CLS 標準的組件不能包含不符合 CLS 標準的模組。 若要解決這個警告，請確定組件和模組的 CLSCompliant 屬性同時為 true 或 false，或是移除其中一個屬性。 如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 範例  
 下列範例會產生 CS3017：  
  
```  
// CS3017.cs // compile with: /target:module using System; [module: CLSCompliant(true)] [assembly: CLSCompliant(false)]  // CS3017 // Try this line instead: // [assembly: CLSCompliant(true)] class C { static void Main() {} }  
```