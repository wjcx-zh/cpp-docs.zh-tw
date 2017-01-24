---
title: "編譯器錯誤 CS0709 | Microsoft Docs"
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
  - "CS0709"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0709"
ms.assetid: 91040f55-a060-4cc3-b830-f6b771af28d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0709
'derived class': 不能衍生自靜態類別 '基底類別'  
  
 靜態類別無法具現化或從中衍生。 換句話說，靜態類別不能是任何其他類別的基底類別。  
  
## 範例  
 下列範例會產生 CS0709。  
  
```  
// CS0709.cs // compile with: /target:library public static class Base {} public class Derived : Base {}   // CS0709  
```