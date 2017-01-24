---
title: "編譯器錯誤 CS1725 | Microsoft Docs"
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
  - "cs1725"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1725"
ms.assetid: baef9ae3-b036-41d6-972c-9f3cdae1e8bd
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1725
Friend 組件參考 'reference' 無效。 InternalsVisibleTo 宣告不能指定版本、文化特性、公開金鑰語彙基元或處理器架構。  
  
 您無法在 Friend 組件參考中加入版本文化特性。 部分類別對 Friend 組件而言應該是可見的。  
  
## 範例  
 下列範例會產生 CS1725。  
  
```  
// CS1725.cs // compile with: /target:library using System.Runtime.CompilerServices; [assembly:InternalsVisibleTo("partial01,version=1.1.0.0")]   // CS1725 // try the following line instead // [assembly:InternalsVisibleTo("partial01")] partial class TestClass { public static string strBar = "my string"; }  
```  
  
## 請參閱  
 [如何：建立簽署的 Friend 組件](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)