---
title: "編譯器警告 (層級 1) CS3005 | Microsoft Docs"
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
  - "CS3005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3005"
ms.assetid: 64b687e3-2dbd-45dd-b6da-81f77eb7d6bd
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3005
只有大小寫不同的識別項 'identifier' 不符合 CLS 標準  
  
 [public](../Topic/public%20\(C%23%20Reference\).md)、[protected](../Topic/protected%20\(C%23%20Reference\).md) 或 `protected` `internal` 識別項與 `public`、`protected` 或 `protected` `internal` 識別項僅有一或多個字母的大小寫不同，不符合 Common Language Specification \(CLS\)。   如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 範例  
 下列範例會產生 CS3003：  
  
```  
// CS3005.cs using System; [assembly:CLSCompliant(true)] public class a { public static int a1 = 0; public static int A1 = 1;   // CS3005 public static void Main() { Console.WriteLine(a1); Console.WriteLine(A1); } }  
```