---
title: "編譯器錯誤 CS1665 | Microsoft Docs"
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
  - "CS1665"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1665"
ms.assetid: 93d4a4af-23c3-4730-a778-77852e41db4d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1665
固定大小緩衝區的長度必須大於零  
  
 如果以零或負值的大小宣告固定大小緩衝區，就會發生這個錯誤。 固定大小緩衝區的長度必須是正整數。  
  
## 範例  
 下列範例會產生 CS1665。  
  
```  
// CS1665.cs // compile with: /unsafe /target:library struct S { public unsafe fixed int A[0];   // CS1665 }  
```