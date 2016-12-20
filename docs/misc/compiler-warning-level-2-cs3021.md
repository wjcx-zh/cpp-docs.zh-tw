---
title: "編譯器警告 (層級 2) CS3021 | Microsoft Docs"
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
  - "CS3021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3021"
ms.assetid: 89f09e4d-65b0-4422-86ea-85c7e05ac29b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS3021
'type' 不需要 CLSCompliant 屬性，因為組件沒有 CLSCompliant 屬性  
  
 如果 `[CLSCompliant(false)]`  出現在組件層級 CLSCompliant 屬性未設為 true 之組件中的類別 \(亦即，行 `[assembly: CLSCompliant(true)]`\)，則會發生這個警告。 因為組件未將它自己宣告為符合 CLS 標準，所以組件內的任何項目都不需要將它自己宣告為不符合標準，因為它是假設為不符合標準。 如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)。  
  
 若要移除這個警告，請移除屬性或加入組件層級屬性。  
  
## 範例  
 下列範例會產生 CS3021：  
  
```  
// CS3021.cs using System; // Uncomment the following line to declare the assembly CLS Compliant, // and avoid the warning without removing the attribute on the class. //[assembly: CLSCompliant(true)] // Remove the next line to avoid the warning. [CLSCompliant(false)]               // CS3021 public class C { public static void Main() { } }  
```  
  
## 請參閱  
 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)