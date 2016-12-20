---
title: "編譯器錯誤 CS1638 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1638"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1638"
ms.assetid: 5279c060-5be3-4c29-80cc-21326d4cffdb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1638
'identifier' 是保留的識別項，並在使用 ISO 語言版本模式時無法使用  
  
 **\/langversion** 編譯器參數指定 ISO 語言相容性選項時，在識別項中任何位置具有雙底線的任何識別項都會產生此錯誤。 若要避免這個錯誤，請排除具有雙底線的任何識別項，或不要使用 ISO\-1 語言版本選項。  
  
## 範例  
 下列範例會產生 CS1638：  
  
```  
// CS1638.cs // compile with: /langversion:ISO-1 class bad__identifer // CS1638 (double underscores are not ISO compliant) { } // Try this instead: //class GoodIdentifier //{ //} class CMain { public static void Main() { } }  
```  
  
## 請參閱  
 [\/langversion \(Conformant Syntax\)](../Topic/-langversion%20\(C%23%20Compiler%20Options\).md)