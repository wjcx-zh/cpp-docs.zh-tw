---
title: "編譯器錯誤 CS0699 | Microsoft Docs"
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
  - "CS0699"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0699"
ms.assetid: 1dff310b-6b8d-46b4-a649-bbf23282ff1f
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0699
'generic' 未定義類型參數 'identifier'  
  
 在泛型宣告中使用了在該泛型之類型參數宣告清單中找不到的類型參數。 如果類型參數所使用的名稱不一致，就可能會發生這種情況。  
  
 下列範例會產生 CS0699：  
  
```  
// CS0699.cs class C<T> where U : I   // CS0699 – U is not a valid type parameter { }  
```