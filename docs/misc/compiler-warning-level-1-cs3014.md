---
title: "編譯器警告 (層級 1) CS3014 | Microsoft Docs"
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
  - "CS3014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3014"
ms.assetid: 6825b42f-1820-4265-b8d8-9b3387d7c130
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3014
'member' 不需要 CLSCompliant 屬性，因為組件沒有 CLSCompliant 屬性  
  
 原始程式碼檔中未指定符合 Common Language Specification \(CLS\) 標準，但檔案中的建構卻標示為符合 CLS 標準。 這是不允許的。 若要解決這個警告，將符合 CLS 標準的組件層級屬性加入檔案中 \(在下列範例中，取消註解包含組件層級屬性的那一行\)。 如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 範例  
 下列範例會產生 CS3014：  
  
```  
// CS3014.cs using System; // [assembly:CLSCompliant(true)] public class I { [CLSCompliant(true)]   // CS3014 public void M() { } public static void Main() { } }  
```