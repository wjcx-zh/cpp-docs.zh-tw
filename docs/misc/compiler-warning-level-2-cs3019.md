---
title: "編譯器警告 (層級 2) CS3019 | Microsoft Docs"
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
  - "CS3019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3019"
ms.assetid: b41117cf-8956-4989-93fd-9903812e2d2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS3019
將不會在 'type' 上執行 CLS 相容性檢查，因為從此組件之外無法看到它。  
  
 當其他組件無法看到具有 <xref:System.CLSCompliantAttribute> 屬性的類型或成員時，就會出現這個警告。 若要解決這個錯誤，請從其他組件無法看到的任何類別或成員中移除此屬性，或將類型或成員設為可見。 如需 CLS 符合性的詳細資訊，請參閱 [\<PAVE OVER\> 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)。  
  
## 範例  
 下列範例會產生 CS3019：  
  
```  
// CS3019.cs // compile with: /W:2 using System; [assembly: CLSCompliant(true)] // To fix the error, remove the next line [CLSCompliant(true)]  // CS3019 class C { [CLSCompliant(false)]  // CS3019 void Foo() { } static void Main() { } }  
```  
  
## 請參閱  
 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)