---
title: "編譯器警告 (層級 1) CS3018 | Microsoft Docs"
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
  - "CS3018"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3018"
ms.assetid: 35d2f4bd-10c3-4e9f-8e02-389ab84db2cd
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3018
因為 'type' 是不符合 CLS 標準之類型 'type' 的成員，所以不可標記為符合 CLS 標準  
  
 如果 CLSCompliant 屬性設定為 `true` 的巢狀類別宣告為 CLSCompliant 屬性設定為 `false` 之類別的成員，則會發生這個警告。 這是不允許的作業，因為巢狀類別不能符合 CLS 標準 \(如果巢狀類別是不符合 CLS 標準之外部類別的成員\)。 若要解決這個警告，請從巢狀類別中移除 CLSCompliant 屬性，或將它從 `true` 變更為 `false`。 如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 範例  
 下列範例會產生 CS3018。  
  
```  
// CS3018.cs // compile with: /target:library using System; [assembly: CLSCompliant(true)] [CLSCompliant(false)] public class Outer { [CLSCompliant(true)]   // CS3018 public class Nested {} // OK public class Nested2 {} [CLSCompliant(false)] public class Nested3 {} }  
```