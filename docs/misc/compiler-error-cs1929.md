---
title: "編譯器錯誤 CS1929 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1929"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1929"
ms.assetid: effdd5d4-e156-418b-9d45-4ca194ab4319
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1929
執行個體引數：無法從 'typeA' 轉換為 'typeB'。  
  
 當您嘗試從不會擴充的類別叫用擴充方法時，就會產生這個錯誤。 在此處所顯示的範例中，擴充方法是針對衍生類別 `A` 而定義，但不是針對基底類別 `B`。  
  
### 更正這個錯誤  
  
1.  請在您必須叫用之處為類型建立新的擴充方法，或是將呼叫移到現有方法會擴充之類型的物件。  
  
## 範例  
 下列程式碼會產生 CS1928 和 CS1929：  
  
```  
// cs1929.cs using System.Linq; using System.Collections; static class Ext { public static void ExtMethod(this A a) { } } class A : B { } class B { static void Main() { B b = new B(); b.ExtMethod(); // CS1929 } }  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)