---
title: "編譯器錯誤 CS0734 | Microsoft Docs"
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
  - "CS0734"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0734"
ms.assetid: 9e1b0e49-bfc3-400c-9fd1-37e3c827e656
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0734
只有在建置 'module' 的目標類型時，才可指定 \/moduleassemblyname 選項。  
  
 只有在建置 .netmodule 時，才應該使用編譯器選項 **\/moduleassemblyname**。 如需詳細資訊，請參閱 [\/moduleassemblyname \(Specify Friend Assembly for Module\)](../Topic/-moduleassemblyname%20\(C%23%20Compiler%20Option\).md)。  
  
 如需建置 .netmodule 的詳細資訊，請參閱[\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)。  
  
## 範例  
 下列範例會產生 CS0734。 若要解決，請在編譯中加入 **\/target:module**。  
  
```  
// CS0734.cs // compile with: /moduleassemblyname:A // CS0734 expected public class Test {}  
```