---
title: "編譯器錯誤 CS0713 | Microsoft Docs"
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
  - "CS0713"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0713"
ms.assetid: 27a46765-d982-43ba-909f-9278e26b80d2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0713
靜態類別 'static type' 不可衍生自類型 'type'。 靜態類別必須衍生自物件。  
  
 如果允許這麼做，靜態類別會從基底類別中繼承方法和非靜態成員，因此不是靜態的。 因此，不允許這麼做。  
  
 下列範例會產生 CS0713：  
  
```  
// CS0713.cs public class Base { } public static class Derived : Base  // CS0713 { } public class CMain { public static void Main() { } }  
```