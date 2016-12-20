---
title: "編譯器警告 (層級 1) CS3001 | Microsoft Docs"
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
  - "CS3001"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3001"
ms.assetid: c4f3e247-5e47-4182-b415-c573fb1a152f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3001
引數類型 'type' 不符合 CLS 標準  
  
 [public](../Topic/public%20\(C%23%20Reference\).md)、[protected](../Topic/protected%20\(C%23%20Reference\).md) 或 `protected` `internal` 方法必須接受其類型符合 Common Language Specification \(CLS\) 標準的參數。 如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 範例  
 下列範例會產生 CS3001：  
  
```  
// CS3001.cs [assembly:System.CLSCompliant(true)] public class a { public void bad(ushort i)   // CS3001 { } private void OK(ushort i)   // OK, private method { } public static void Main() { } }  
```