---
title: "編譯器警告 (層級 1) CS1720 | Microsoft Docs"
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
  - "CS1720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1720"
ms.assetid: 97adc294-3a4c-4418-a4ed-ccff43125b62
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1720
運算式一律會造成 System.NullReferenceException，因為 'generic type' 的預設值是 null  
  
 如果您撰寫的運算式涉及的泛型類型變數預設值為參考類型 \(例如類別\)，則會發生此錯誤。 以下列運算式為例：  
  
```  
default(T).ToString()  
```  
  
 由於 `T` 是參考類型，其預設值為 null，因此嘗試對其套用 <xref:System.Object.ToString%2A> 方法時會擲回 <xref:System.NullReferenceException>。  
  
## 範例  
 針對類型 `T` 的類別參考條件約束可確保 `T` 是參考類型。  
  
 下列範例會產生 CS1720：  
  
```  
// CS1720.cs using System; public class Tester { public static void GenericClass<T>(T t1) where T : class { Console.WriteLine(default(T).ToString());  // CS1720 } public static void Main() {} }  
```