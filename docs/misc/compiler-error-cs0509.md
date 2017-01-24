---
title: "編譯器錯誤 CS0509 | Microsoft Docs"
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
  - "CS0509"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0509"
ms.assetid: dc113e03-7a01-489b-b886-51ee056fc96a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0509
'class1': 無法衍生自密封類型 'class2'  
  
 [密封](../Topic/sealed%20\(C%23%20Reference\).md)類別不能當成[基底](../Topic/base%20\(C%23%20Reference\).md)類別使用。 預設會密封結構。  
  
 下列範例會產生 CS0509：  
  
```  
// CS0509.cs // compile with: /target:library sealed public class clx {} public class cly : clx {}   // CS0509  
```