---
title: "編譯器警告 (層級 1) CS0809 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0809"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0809"
ms.assetid: 2c2f0248-ab3a-4cdc-a1b0-2f0e05eac4c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS0809
過時的成員 'memberA' 會覆寫非過時的成員 'memberB'。  
  
 一般而言，標記為過時的成員不應該覆寫未標記為過時的成員。[!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] 中會產生這個警告，但 [!INCLUDE[vsprvslong](../error-messages/compiler-errors-1/includes/vsprvslong_md.md)] 中則不會。  
  
### 更正這個錯誤  
  
1.  從覆寫成員移除 `Obsolete` 屬性，或將其加入基底類別成員中。  
  
## 範例  
  
```  
// CS0809.cs public class Base { public virtual void Test1() { } } public class C : Base { [System.Obsolete()] public override void Test1() // CS0809 { } }  
```