---
title: "編譯器錯誤 CS0424 | Microsoft Docs"
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
  - "CS0424"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0424"
ms.assetid: 09ae482c-255a-4f99-8dc8-ba31c3ea8c71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0424
'class': 具有 ComImport 屬性的類別不能指定基底類別  
  
 指定 <xref:System.Runtime.InteropServices.ComImportAttribute> 屬性表示是要從 COM 模組匯入類別的實作。 不允許將繼承自基底類別的其他方法或欄位加入 COM 模組中所定義的實作。  
  
 下列範例會產生 CS0424：  
  
```  
// CS0424.cs // compile with: /target:library using System.Runtime.InteropServices; public class A {} [ ComImport, Guid("7ab770c7-0e23-4d7a-8aa2-19bfad479829") ] class B : A {}   // CS0424 error  
```