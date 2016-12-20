---
title: "編譯器警告 (層級 1) CS3027 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3027"
ms.assetid: c515e623-3f5a-49fa-a878-f1d8e90fdc24
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3027
'type\_1' 不符合 CLS 標準，因為基底介面 'type\_2' 不符合 CLS 標準  
  
 不符合 CLS 標準的類型不能是符合 CLS 標準之類型的基底類型。  
  
## 範例  
 下列範例包含具有方法的介面，而方法在其簽章中使用不符合 CLS 標準的類型，讓類型不符合 CLS 標準。  
  
```  
// CS3027.cs // compile with: /target:library public interface IBase { void IMethod(uint i); }  
```  
  
## 範例  
 下列範例會產生 CS3027。  
  
```  
// CS3027_b.cs // compile with: /reference:CS3027.dll /target:library /W:1 [assembly:System.CLSCompliant(true)] public interface IDerived : IBase {}  
```